How to add user interactive graphs to a sharepoint site using an excel file

Here’s a breakdown of the best methods to add interactive graphs to a SharePoint site using an Excel file, from simplest to most powerful:

---

### Method 1: File & Media Web Part (Easiest)

This is the quickest way to embed an Excel chart directly.

1. **Upload your Excel file** to a SharePoint document library
2. Edit your SharePoint page and click the **“+” icon** to add a web part
3. Search for and add the **“File and Media”** (File Viewer) web part
4. Connect it to your Excel file in the document library
5. In the web part settings, you can choose to display: the full workbook, a specific chart, a table, or a named range

Within the settings you can also control whether to let people sort/filter/type into cells, and adjust the height/width of the display area. [SharePoint Stuff](https://sharepointstuff.com/2025/02/20/embed-an-excel-sheet-into-a-page-in-sharepoint/) This gives users basic interactivity like sorting and filtering.

**Best for:** Simple, quick embedding when your data doesn’t change often.

---

### Method 2: Embed Web Part with Excel Embed Code (More Control)

You can generate an embed code directly from Excel Online, choosing your interaction settings, then paste it into SharePoint’s **Embed web part** (under “Website address or embed code”). [SharePoint Stuff](https://sharepointstuff.com/2025/02/20/embed-an-excel-sheet-into-a-page-in-sharepoint/)

This lets you display specific sheets from the same Excel file on one page and control user interaction more precisely.

**Steps:**

1. Open your Excel file in **Excel Online** (via SharePoint or OneDrive)
2. Go to **File > Share > Embed**
3. Configure interaction options and copy the embed code
4. On your SharePoint page, add the **Embed** web part and paste the code

---

### Method 3: Import Excel to a SharePoint List + Quick Chart Web Part

This is the best option for **live, auto-updating charts**.

1. Import your Excel data into a **SharePoint List** (via the List app → Import from Excel)
2. Add the **Quick Chart** web part to your page
3. Set the data source to your SharePoint list

The Quick Chart web part updates itself automatically whenever the connected SharePoint list changes, keeping the chart current. [Virtosoftware](https://blog.virtosoftware.com/chart-in-sharepoint/) However, it only supports two chart types — column and pie — and is limited to 50 data points from a list. [Virtosoftware](https://blog.virtosoftware.com/chart-in-sharepoint/)

**Best for:** Keeping charts automatically synced with regularly updated data.

---

### Method 4: Power BI (Most Interactive & Powerful)

For advanced reports and analysis, Power BI is the way to go. Embedded reports are dynamic and interactive on a SharePoint page, just like in Power BI itself. [SharePoint Maven](https://sharepointmaven.com/4-ways-to-display-charts-in-sharepoint/)

**Steps:**

1. Connect Power BI to your Excel file as a data source
2. Build your report/dashboard in Power BI
3. In Power BI, go to **File > Embed in SharePoint Online** to get a URL
4. Add the **Power BI web part** to your SharePoint page and paste the URL

> ⚠️ Note: You need a Power BI Pro license to generate an embed link for SharePoint. [SharePoint Maven](https://sharepointmaven.com/4-ways-to-display-charts-in-sharepoint/)

**Best for:** Complex dashboards with drill-downs, filters, slicers, and multiple chart types.

---

### Quick Comparison

|Method|Interactivity|Auto-updates|Difficulty|Cost|
|---|---|---|---|---|
|File & Media Web Part|Basic (sort/filter)|Manual|⭐ Easy|Free|
|Embed Web Part|Moderate|Manual|⭐⭐|Free|
|Quick Chart + List|Limited chart types|✅ Auto|⭐⭐|Free|
|Power BI|Full drill-down/filter|✅ Auto|⭐⭐⭐|Pro license|

For most teams, **embedding via the File & Media web part** is the fastest start, and **Power BI** is the best long-term solution if you need real interactivity and live data.