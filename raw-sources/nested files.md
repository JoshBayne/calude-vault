How can I move all files from layers of subdirectories to a single directory. The files in reference are hundreds of images and video files spread across their own subdirectory several layers deep

Here are the most reliable ways to do this:

### Using `find` + `mv` (Linux/macOS)

**Basic approach — move everything to one flat directory:**

bash

```bash
find /source/path -type f \( -iname "*.jpg" -o -iname "*.png" -o -iname "*.mp4" -o -iname "*.mov" \) \
  -exec mv {} /destination/path/ \;
```

**Safer approach — handles duplicate filenames by prepending the parent folder name:**

bash

```bash
find /source/path -type f \( -iname "*.jpg" -o -iname "*.png" -o -iname "*.mp4" -o -iname "*.mov" \) | \
  while read file; do
    dir=$(basename "$(dirname "$file")")
    filename=$(basename "$file")
    mv "$file" "/destination/path/${dir}_${filename}"
  done
```

### Using `rsync` (flattens and copies, not moves)

bash

```bash
find /source/path -type f \( -iname "*.jpg" -o -iname "*.png" \) -exec rsync -av {} /destination/path/ \;
```

### On Windows (PowerShell)

powershell

```powershell
Get-ChildItem -Path "C:\source" -Recurse -Include *.jpg,*.png,*.mp4,*.mov |
  Move-Item -Destination "C:\destination\"
```

---

### Key things to watch out for

**Duplicate filenames** — If two files in different subdirs share a name, one will silently overwrite the other. Use the “safer approach” above to prefix with the parent folder name, or use this to detect conflicts first:

bash

```bash
find /source/path -type f | xargs -I{} basename {} | sort | uniq -d
```

**Dry run first** — Replace `mv` with `echo` to preview what would happen:

bash

```bash
find /source/path -type f -iname "*.jpg" -exec echo mv {} /destination/path/ \;
```

**Common image/video extensions to include:**

- Images: `*.jpg`, `*.jpeg`, `*.png`, `*.gif`, `*.heic`, `*.raw`, `*.cr2`, `*.dng`
- Video: `*.mp4`, `*.mov`, `*.avi`, `*.mkv`, `*.m4v`

The `find` command approach is the most flexible and battle-tested for this kind of task. Would you like help tailoring it to your specific directory structure or OS?

on windows, adjust the powershell script to include appending a digit to avoid duplicate names

Here’s the updated PowerShell script that handles duplicate filenames by appending an incrementing number:

powershell

```powershell
$source = "C:\source"
$destination = "C:\destination"

# Create destination if it doesn't exist
New-Item -ItemType Directory -Force -Path $destination | Out-Null

Get-ChildItem -Path $source -Recurse -Include *.jpg,*.jpeg,*.png,*.gif,*.heic,*.raw,*.cr2,*.dng,*.mp4,*.mov,*.avi,*.mkv,*.m4v |
  ForEach-Object {
      $destFile = Join-Path $destination $_.Name

      if (Test-Path $destFile) {
          $baseName = [System.IO.Path]::GetFileNameWithoutExtension($_.Name)
          $ext      = [System.IO.Path]::GetExtension($_.Name)
          $counter  = 1

          do {
              $destFile = Join-Path $destination "${baseName}_${counter}${ext}"
              $counter++
          } while (Test-Path $destFile)
      }

      Move-Item -Path $_.FullName -Destination $destFile
  }
```

**What it does:**

- Tries to move the file as-is first
- If a file with that name already exists, it increments a counter until it finds a free name — e.g. `photo.jpg` → `photo_1.jpg` → `photo_2.jpg`
- Creates the destination folder automatically if it doesn’t exist

**To do a dry run first** (replace `Move-Item` with `Write-Host` to preview):

powershell

```powershell
Write-Host "Would move: $($_.FullName) → $destFile"
```

Just swap `$source` and `$destination` for your actual paths and you’re good to go.