In sharepoint, is it better for there to be multiple libraries for different documents, or one library with multiple folders dividing the content a layer or two deep

This is a classic SharePoint architecture question, and the honest answer is: **it depends on your use case**, but there are clear principles that point you in the right direction.

### One Library with Folders

**Better when:**

- Content is closely related and users need to browse across it holistically
- You want a single set of permissions for everything (simpler to manage)
- You’re storing fewer than ~5,000 items total (SharePoint’s list view threshold)
- You want metadata and columns to apply uniformly across all documents
- Users frequently need to move files between “categories”

**Drawbacks:**

- Folders don’t scale well — deep nesting (3+ levels) becomes hard to navigate
- You can’t set different versioning, retention, or content type settings per folder
- Permissions inheritance gets messy if you need folder-level security

### Multiple Libraries

**Better when:**

- Different document types have genuinely different lifecycles (contracts vs. marketing assets vs. HR files)
- You need different settings per library — versioning, approval workflows, retention policies, content types
- Different teams need different permissions (a library-level permission boundary is much cleaner than folder-level)
- You’re likely to exceed 5,000 items in a single category
- You want distinct views, metadata columns, or templates per document type

**Drawbacks:**

- Navigation gets fragmented — users have to know which library to go to
- Search still works across libraries, but browsing is siloed
- More administrative overhead to maintain

### The General Rule of Thumb

**Use multiple libraries when the content is meaningfully different** — different permissions, different workflows, different metadata, or different audiences. Use folders within a library for simple organizational groupings of similar content.

A two-layer folder structure within a library is usually fine. Beyond that, you’re often better served by metadata/filtered views rather than deeper folders — SharePoint’s column filters and views can replace folder hierarchies entirely and are much more flexible.

The most common mistake is defaulting to deeply nested folders because it mirrors a file share. SharePoint is better treated as a database with views, not a filing cabinet.

sharepoint, embed an htm file into a news post using an iframe. The htm file is located in a seperate document library names "HTML Newsletters" while the newspost is held in the Site Pages library

Embedding an HTM file via iframe in SharePoint is a bit finicky because SharePoint blocks iframes by default and has some cross-origin quirks even within the same site. Here’s how to do it cleanly:

### Step 1: Get the Direct URL to the HTM File

In your **HTML Newsletters** library, find the file and copy its direct link. It will look something like:

```
https://yourtenant.sharepoint.com/sites/yoursite/HTML%20Newsletters/yournewsletter.htm
```

You want the raw file URL, not a sharing link. You can get this by clicking the three dots on the file → **Details** → copy the path at the bottom, or just navigate to the file and grab the URL from the browser.

### Step 2: Make Sure the File is Accessible

The HTM file needs to be accessible to anyone who will read the news post. If your library has restricted permissions, viewers of the news post won’t be able to load the iframe content. Make sure the library permissions align with your news post audience.

### Step 3: Add an Embed Web Part to the News Post

1. Open the news post in **edit mode**
2. Click the **+** to add a new web part where you want the newsletter to appear
3. Search for and add the **Embed** web part
4. In the embed field, paste an iframe tag like this:

html

```html
<iframe 
  src="https://yourtenant.sharepoint.com/sites/yoursite/HTML%20Newsletters/yournewsletter.htm"
  width="100%" 
  height="800px" 
  frameborder="0"
  scrolling="auto">
</iframe>
```

Adjust the `height` value to match your newsletter’s actual length.

### Step 4: Allow the URL (if it gets blocked)

SharePoint may reject the embed with a message like _“This content can’t be displayed in a frame.”_ If that happens, a SharePoint admin needs to whitelist the URL:

1. Go to **SharePoint Admin Center**
2. Navigate to **Settings** → **Pages** (or search for “HTML Field Security”)
3. Under **Allow or block embeds**, add your tenant URL or the specific library URL to the allowed list

Alternatively, via PowerShell:

powershell

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $false
# For iframe embedding specifically:
Set-SPOSite -Identity "https://yourtenant.sharepoint.com/sites/yoursite" -DenyAddAndCustomizePages 0
```

### Known Gotchas

- **Same-site iframes generally work**, but SharePoint can still block them depending on tenant security settings
- If the HTM file uses external fonts, images, or scripts, those may be blocked by the browser’s mixed-content rules
- The Embed web part has a character limit on the iframe code — if your src URL is very long, this can cause silent failures
- On **mobile**, iframes in SharePoint render poorly — consider adding a fallback link below the embed for mobile users

A link like _“View the newsletter directly”_ pointing to the HTM file is a good safety net regardless.