using sharepoint, how can I view the statistics on who last looked at a file?

SharePoint doesn’t have a direct “who viewed this file” feature for individual users, but here are the ways you can access usage statistics:

**For Site Owners / Admins:**

1. **Page/File Analytics** – Navigate to the file or page in SharePoint, then click the **Analytics** icon (bar chart icon) in the top-right toolbar. This shows views over time, but typically shows **aggregate view counts**, not individual viewer names.
2. **SharePoint Admin Center** – Go to the Microsoft 365 Admin Center → SharePoint Admin → **Reports** to see site-level usage data.
3. **Microsoft 365 Usage Reports** – In the **Microsoft 365 Admin Center**, under **Reports → Usage**, you can see activity reports including SharePoint file activity, which can show who accessed files.
4. **Audit Logs (Most Detailed)** – This is the best option for seeing _who_ accessed a file:
    - Go to **Microsoft Purview compliance portal** (compliance.microsoft.com)
    - Navigate to **Audit → Audit Search**
    - Filter by activity type: _“Accessed file”_ or _“Viewed file”_
    - Filter by the specific file or site URL
    - This shows individual user access with timestamps

**Limitations to be aware of:**

- Audit log access requires admin permissions (Global Admin, Compliance Admin, etc.)
- Audit logs may need to be enabled first if they haven’t been turned on
- Microsoft 365 may anonymize individual user data in some reports depending on your organization’s privacy settings
- Retention of audit logs depends on your license (90 days for E3, up to 1 year+ for E5)

The **Audit Log** route via Microsoft Purview is your most reliable path if you need to see specific users and timestamps. Would you like more detail on any of these methods?

How can I make a segregated investor portal in the most current version of Sharepoint that allows invited only users to view sensitive financial information?

Here’s a comprehensive guide to building a secure, segregated investor portal in SharePoint:

---

### 1. Site Architecture

**Create a dedicated Communication Site or Hub Site**

- Go to SharePoint Admin Center → Sites → Create Site
- Choose **Communication Site** (cleaner for external-facing portals)
- Keep it completely separate from your internal intranet

**Use a flat, permission-based folder structure:**

```
Investor Portal (Top-level site)
├── General Documents (all investors)
├── Fund A Investors (only Fund A)
├── Fund B Investors (only Fund B)
└── Individual Investor Folders (1:1 access)
```

---

### 2. Access Control — The Core of Segregation

**Break Permission Inheritance** on each library/folder:

- Go to the folder → **Manage Access** → **Advanced Settings** → **Stop Inheriting Permissions**
- This lets each folder have entirely independent permissions

**Create SharePoint Groups per investor class:**

- `Investor-FundA-ReadOnly`
- `Investor-FundB-ReadOnly`
- `LP-Tier1-Access`
- Never give investors anything higher than **Read** permission level

**Use Microsoft Entra ID (formerly Azure AD) groups** for scalability — manage membership in Entra and sync to SharePoint automatically.

---

### 3. External / Invited-Only Access

**Enable external sharing selectively:**

- SharePoint Admin Center → Policies → Sharing
- Set the site to **“Specific people”** (most restrictive external sharing option)
- Disable sharing at the tenant level, then enable only for this specific site

**Invite investors via:**

- SharePoint’s **“Share”** with specific email addresses
- Or use **Microsoft Entra B2B** (recommended for larger portals) — investors get a guest account tied to their email, with MFA enforced

**Require Authentication:**

- Never use “Anyone with the link” — always require sign-in
- In site sharing settings, uncheck _“Allow sharing with anyone”_

---

### 4. Security Hardening

**Enforce Multi-Factor Authentication (MFA):**

- Via Microsoft Entra Conditional Access policies
- Require MFA for all guest/external accounts accessing the site

**Set Conditional Access Policies:**

- Block access from non-compliant devices
- Restrict access by geography/IP if needed
- Require terms of use acknowledgment on first login

**Disable Download / Printing (Optional but recommended):**

- Go to the document library → **Library Settings** → **Information Rights Management (IRM)**
- Enable IRM to prevent download, print, and copy
- Or use **Microsoft Purview sensitivity labels** to enforce encryption on the documents themselves — protection travels with the file

**Set link expiration:**

- Any shared links should have expiration dates set
- SharePoint Admin → Sharing → Set default link expiration (e.g., 30 days)

---

### 5. Sensitivity Labels & Compliance

**Apply Microsoft Purview Sensitivity Labels:**

- Label documents as _Confidential – Investor Only_
- Labels enforce encryption, watermarking, and access restrictions even if a file is downloaded
- Requires Microsoft 365 E3 or E5 licensing

**Enable Audit Logging:**

- Microsoft Purview → Audit → ensure logging is on
- You’ll get a full trail of who viewed, downloaded, or shared any document

---

### 6. Investor Experience

**Customize the portal:**

- Use SharePoint’s **web parts** to build a clean landing page
- Add a **Hero web part** for announcements
- Use **Quick Links** for easy document navigation
- Add a **People web part** for investor relations contacts

**Custom Domain (optional):**

- Map a custom URL like `investors.yourfirm.com` via SharePoint’s custom domain feature in the Admin Center

---

### 7. Ongoing Management Checklist

|Task|Frequency|
|---|---|
|Review guest user access|Quarterly|
|Run Access Reviews in Entra ID|Quarterly|
|Check audit logs for anomalies|Monthly|
|Rotate/expire sharing links|Per document lifecycle|
|Offboard departed investors|Immediately upon exit|

---

### Licensing Requirements

|Feature|Minimum License|
|---|---|
|External B2B access|Microsoft 365 Business Basic+|
|Conditional Access / MFA|Entra ID P1 (included in M365 E3)|
|Sensitivity Labels + IRM|Microsoft 365 E3|
|Advanced audit + compliance|Microsoft 365 E5|

---

The combination of **broken permission inheritance + Entra B2B guest accounts + Conditional Access MFA + Purview sensitivity labels** gives you a genuinely enterprise-grade segregated investor portal. Would you like a deeper dive into any specific layer — such as setting up Entra B2B, configuring IRM, or structuring permissions for multiple fund classes?

Generate an example HTML file that I can use as a template to make the landing page for the Investor portal. Keep in mind that I am using web parts from Sharepoint. Include a CTA button for scheduling a demo of the product.

Read a file, created a file, shared files

Here’s your investor portal landing page template. Here’s what’s included and how to adapt it for SharePoint:

**Sections & Web Part Zones**  
Every content section is marked with a dashed `sp-webpart-zone` border and a label (e.g., _“Quick Links Web Part”_, _“Document Library Web Part”_) so you know exactly which native SharePoint web part to drop in when building the page in the SPO editor. You can delete those placeholder cards and wire in the real web parts.

**What to customize before publishing:**

- Replace `[Firm Name]` throughout with your actual firm name
- Swap the placeholder stats (AUM, IRR, etc.) in the hero panel with real figures
- Update all `[yourfirm].com` email addresses
- Replace contact names/roles with your actual IR team
- Point the **Schedule a Demo** button at your booking link — Microsoft Bookings integrates natively with M365 and is the simplest option

**The Demo CTA** is the gold “Schedule a Demo” button in the bottom banner, currently pointing to Microsoft Bookings. You can swap that `href` for a Calendly link or any other scheduler.

**Design notes:** The template uses a navy/gold palette suited to financial services, Cormorant Garamond for headings (refined, institutional feel), and is fully responsive down to mobile.

'''html
<!DOCTYPE html>`
<html lang="en">

`<head>`

`<meta charset="UTF-8" />`

`<meta name="viewport" content="width=device-width, initial-scale=1.0"/>`

`<title>Investor Portal — [Firm Name]</title>`

`<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>`

`<style>`

`/* ─── CSS Variables ─────────────────────────────────────── */`

`:root {`

`--navy: #0b1829;`

`--navy-mid: #132338;`

`--gold: #c9a84c;`

`--gold-light: #e8c97a;`

`--cream: #f5f0e8;`

`--cream-mid: #ede7da;`

`--white: #ffffff;`

`--text-dim: #8a9ab5;`

`--border: rgba(201,168,76,0.18);`

`--font-serif: 'Cormorant Garamond', Georgia, serif;`

`--font-sans: 'DM Sans', sans-serif;`

`}`

`/* ─── Reset & Base ──────────────────────────────────────── */`

`*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }`

`html { scroll-behavior: smooth; }`

`body {`

`background: var(--navy);`

`color: var(--cream);`

`font-family: var(--font-sans);`

`font-weight: 300;`

`line-height: 1.7;`

`overflow-x: hidden;`

`}`

`/* ─── Noise texture overlay ─────────────────────────────── */`

`body::before {`

`content: '';`

`position: fixed;`

`inset: 0;`

`background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");`

`pointer-events: none;`

`z-index: 0;`

`opacity: 0.4;`

`}`

`/* ─── Gold line accent ──────────────────────────────────── */`

`.gold-line {`

`display: block;`

`width: 48px;`

`height: 1px;`

`background: var(--gold);`

`margin-bottom: 1.4rem;`

`}`

`/* ─── Navigation ────────────────────────────────────────── */`

`nav {`

`position: fixed;`

`top: 0; left: 0; right: 0;`

`z-index: 100;`

`display: flex;`

`align-items: center;`

`justify-content: space-between;`

`padding: 1.4rem 3rem;`

`background: rgba(11,24,41,0.88);`

`backdrop-filter: blur(14px);`

`border-bottom: 1px solid var(--border);`

`animation: fadeDown 0.8s ease both;`

`}`

`@keyframes fadeDown {`

`from { opacity: 0; transform: translateY(-16px); }`

`to { opacity: 1; transform: translateY(0); }`

`}`

`.nav-logo {`

`font-family: var(--font-serif);`

`font-size: 1.35rem;`

`font-weight: 300;`

`letter-spacing: 0.08em;`

`color: var(--cream);`

`}`

`.nav-logo span { color: var(--gold); }`

`.nav-links {`

`display: flex;`

`gap: 2.4rem;`

`list-style: none;`

`}`

`.nav-links a {`

`font-size: 0.78rem;`

`letter-spacing: 0.12em;`

`text-transform: uppercase;`

`color: var(--text-dim);`

`text-decoration: none;`

`transition: color 0.2s;`

`}`

`.nav-links a:hover { color: var(--gold); }`

`.nav-cta {`

`font-size: 0.78rem;`

`letter-spacing: 0.1em;`

`text-transform: uppercase;`

`color: var(--navy);`

`background: var(--gold);`

`border: none;`

`padding: 0.6rem 1.4rem;`

`cursor: pointer;`

`font-family: var(--font-sans);`

`font-weight: 500;`

`transition: background 0.2s, transform 0.15s;`

`}`

`.nav-cta:hover { background: var(--gold-light); transform: translateY(-1px); }`

`/* ─── Hero ──────────────────────────────────────────────── */`

`.hero {`

`position: relative;`

`min-height: 100vh;`

`display: grid;`

`grid-template-columns: 1fr 1fr;`

`align-items: center;`

`padding: 8rem 3rem 5rem;`

`gap: 4rem;`

`z-index: 1;`

`}`

`/* Diagonal geometric background */`

`.hero::after {`

`content: '';`

`position: absolute;`

`top: 0; right: 0;`

`width: 52%;`

`height: 100%;`

`background: var(--navy-mid);`

`clip-path: polygon(8% 0, 100% 0, 100% 100%, 0% 100%);`

`z-index: -1;`

`}`

`.hero-text { animation: fadeUp 1s 0.2s ease both; }`

`@keyframes fadeUp {`

`from { opacity: 0; transform: translateY(28px); }`

`to { opacity: 1; transform: translateY(0); }`

`}`

`.hero-eyebrow {`

`font-size: 0.72rem;`

`letter-spacing: 0.2em;`

`text-transform: uppercase;`

`color: var(--gold);`

`margin-bottom: 1.2rem;`

`}`

`.hero-title {`

`font-family: var(--font-serif);`

`font-size: clamp(2.8rem, 5vw, 4.4rem);`

`font-weight: 300;`

`line-height: 1.12;`

`letter-spacing: -0.01em;`

`color: var(--cream);`

`margin-bottom: 1.6rem;`

`}`

`.hero-title em {`

`font-style: italic;`

`color: var(--gold);`

`}`

`.hero-subtitle {`

`font-size: 0.95rem;`

`color: var(--text-dim);`

`max-width: 420px;`

`margin-bottom: 2.8rem;`

`line-height: 1.8;`

`}`

`.hero-actions { display: flex; gap: 1rem; align-items: center; flex-wrap: wrap; }`

`.btn-primary {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.5rem;`

`background: var(--gold);`

`color: var(--navy);`

`font-family: var(--font-sans);`

`font-size: 0.8rem;`

`font-weight: 500;`

`letter-spacing: 0.1em;`

`text-transform: uppercase;`

`padding: 0.9rem 2rem;`

`border: none;`

`cursor: pointer;`

`text-decoration: none;`

`transition: background 0.2s, transform 0.15s, box-shadow 0.2s;`

`box-shadow: 0 4px 24px rgba(201,168,76,0.25);`

`}`

`.btn-primary:hover {`

`background: var(--gold-light);`

`transform: translateY(-2px);`

`box-shadow: 0 8px 32px rgba(201,168,76,0.35);`

`}`

`.btn-primary svg { transition: transform 0.2s; }`

`.btn-primary:hover svg { transform: translateX(3px); }`

`.btn-ghost {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.5rem;`

`background: transparent;`

`color: var(--cream-mid);`

`font-family: var(--font-sans);`

`font-size: 0.8rem;`

`letter-spacing: 0.1em;`

`text-transform: uppercase;`

`padding: 0.9rem 1.6rem;`

`border: 1px solid var(--border);`

`cursor: pointer;`

`text-decoration: none;`

`transition: border-color 0.2s, color 0.2s;`

`}`

`.btn-ghost:hover { border-color: var(--gold); color: var(--gold); }`

`/* Hero right — stats panel */`

`.hero-panel {`

`background: rgba(255,255,255,0.03);`

`border: 1px solid var(--border);`

`padding: 2.8rem;`

`animation: fadeUp 1s 0.45s ease both;`

`}`

`.hero-panel-label {`

`font-size: 0.7rem;`

`letter-spacing: 0.18em;`

`text-transform: uppercase;`

`color: var(--gold);`

`margin-bottom: 2rem;`

`}`

`.stat-grid {`

`display: grid;`

`grid-template-columns: 1fr 1fr;`

`gap: 2rem 2.4rem;`

`}`

`.stat-item {}`

`.stat-value {`

`font-family: var(--font-serif);`

`font-size: 2.2rem;`

`font-weight: 300;`

`color: var(--cream);`

`line-height: 1;`

`margin-bottom: 0.3rem;`

`}`

`.stat-label {`

`font-size: 0.72rem;`

`letter-spacing: 0.1em;`

`text-transform: uppercase;`

`color: var(--text-dim);`

`}`

`.stat-divider {`

`grid-column: 1 / -1;`

`height: 1px;`

`background: var(--border);`

`}`

`.access-notice {`

`margin-top: 2rem;`

`display: flex;`

`align-items: center;`

`gap: 0.7rem;`

`font-size: 0.75rem;`

`color: var(--text-dim);`

`}`

`.lock-icon {`

`width: 28px; height: 28px;`

`background: rgba(201,168,76,0.1);`

`border: 1px solid var(--border);`

`display: flex; align-items: center; justify-content: center;`

`flex-shrink: 0;`

`}`

`/* ─── SharePoint Web Part Zone ──────────────────────────── */`

`/*`

`SHAREPOINT NOTE:`

`Replace the placeholder sections below with actual`

`SharePoint web parts when building in SPO page editor.`

`Each .sp-webpart-zone is a drop zone for web parts.`

`*/`

`section { position: relative; z-index: 1; }`

`/* ─── Quick Access (Hero web part area) ─────────────────── */`

`.quick-access {`

`background: var(--navy-mid);`

`border-top: 1px solid var(--border);`

`border-bottom: 1px solid var(--border);`

`padding: 3.5rem 3rem;`

`}`

`.section-label {`

`font-size: 0.7rem;`

`letter-spacing: 0.2em;`

`text-transform: uppercase;`

`color: var(--gold);`

`margin-bottom: 2.2rem;`

`}`

`/* ── SP Web Part Placeholder style ── */`

`.sp-webpart-zone {`

`border: 1px dashed rgba(201,168,76,0.3);`

`background: rgba(201,168,76,0.03);`

`padding: 1.4rem 1.8rem;`

`border-radius: 2px;`

`position: relative;`

`}`

`.sp-webpart-zone::before {`

`content: attr(data-webpart);`

`position: absolute;`

`top: -0.6rem;`

`left: 1rem;`

`background: var(--navy-mid);`

`padding: 0 0.5rem;`

`font-size: 0.62rem;`

`letter-spacing: 0.14em;`

`text-transform: uppercase;`

`color: var(--gold);`

`font-family: var(--font-sans);`

`}`

`/* Quick links grid */`

`.quick-links {`

`display: grid;`

`grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));`

`gap: 1rem;`

`}`

`.quick-link-card {`

`background: rgba(255,255,255,0.03);`

`border: 1px solid var(--border);`

`padding: 1.6rem;`

`cursor: pointer;`

`text-decoration: none;`

`color: var(--cream);`

`transition: background 0.2s, border-color 0.2s, transform 0.15s;`

`display: flex;`

`flex-direction: column;`

`gap: 0.8rem;`

`}`

`.quick-link-card:hover {`

`background: rgba(201,168,76,0.06);`

`border-color: var(--gold);`

`transform: translateY(-2px);`

`}`

`.quick-link-icon {`

`width: 36px; height: 36px;`

`border: 1px solid var(--border);`

`display: flex; align-items: center; justify-content: center;`

`color: var(--gold);`

`}`

`.quick-link-title {`

`font-size: 0.85rem;`

`font-weight: 500;`

`letter-spacing: 0.02em;`

`}`

`.quick-link-desc {`

`font-size: 0.72rem;`

`color: var(--text-dim);`

`line-height: 1.5;`

`}`

`/* ─── Documents & Announcements ─────────────────────────── */`

`.content-grid {`

`display: grid;`

`grid-template-columns: 1.6fr 1fr;`

`gap: 0;`

`min-height: 520px;`

`}`

`.documents-panel {`

`padding: 4rem 3rem;`

`border-right: 1px solid var(--border);`

`}`

`.section-title {`

`font-family: var(--font-serif);`

`font-size: 1.7rem;`

`font-weight: 300;`

`color: var(--cream);`

`margin-bottom: 2rem;`

`}`

`/* Document list placeholder */`

`.doc-list { display: flex; flex-direction: column; gap: 0; }`

`.doc-item {`

`display: flex;`

`align-items: center;`

`gap: 1.2rem;`

`padding: 1.1rem 0;`

`border-bottom: 1px solid rgba(201,168,76,0.1);`

`text-decoration: none;`

`color: var(--cream);`

`transition: padding-left 0.2s;`

`}`

`.doc-item:hover { padding-left: 0.5rem; }`

`.doc-item:hover .doc-name { color: var(--gold); }`

`.doc-icon {`

`width: 32px; height: 32px;`

`background: rgba(201,168,76,0.08);`

`border: 1px solid var(--border);`

`display: flex; align-items: center; justify-content: center;`

`flex-shrink: 0;`

`color: var(--gold);`

`font-size: 0.7rem;`

`}`

`.doc-info { flex: 1; min-width: 0; }`

`.doc-name { font-size: 0.85rem; font-weight: 400; white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }`

`.doc-meta { font-size: 0.68rem; color: var(--text-dim); margin-top: 0.15rem; letter-spacing: 0.05em; }`

`.doc-badge {`

`font-size: 0.6rem;`

`letter-spacing: 0.1em;`

`text-transform: uppercase;`

`color: var(--gold);`

`border: 1px solid rgba(201,168,76,0.3);`

`padding: 0.15rem 0.45rem;`

`flex-shrink: 0;`

`}`

`/* Announcements panel */`

`.announcements-panel {`

`background: var(--navy-mid);`

`padding: 4rem 2.6rem;`

`}`

`.announcement-card {`

`border-left: 2px solid var(--gold);`

`padding: 1rem 1.2rem;`

`margin-bottom: 1.4rem;`

`background: rgba(201,168,76,0.04);`

`}`

`.announcement-date {`

`font-size: 0.65rem;`

`letter-spacing: 0.14em;`

`text-transform: uppercase;`

`color: var(--gold);`

`margin-bottom: 0.4rem;`

`}`

`.announcement-title {`

`font-family: var(--font-serif);`

`font-size: 1rem;`

`font-weight: 400;`

`color: var(--cream);`

`margin-bottom: 0.4rem;`

`line-height: 1.3;`

`}`

`.announcement-text {`

`font-size: 0.78rem;`

`color: var(--text-dim);`

`line-height: 1.6;`

`}`

`/* ─── People / Contacts web part area ───────────────────── */`

`.contacts-section {`

`padding: 4rem 3rem;`

`border-top: 1px solid var(--border);`

`}`

`.contacts-grid {`

`display: grid;`

`grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));`

`gap: 1.2rem;`

`margin-top: 2rem;`

`}`

`.contact-card {`

`border: 1px solid var(--border);`

`padding: 1.6rem;`

`background: rgba(255,255,255,0.02);`

`transition: border-color 0.2s;`

`}`

`.contact-card:hover { border-color: var(--gold); }`

`.contact-avatar {`

`width: 48px; height: 48px;`

`background: rgba(201,168,76,0.12);`

`border: 1px solid var(--border);`

`display: flex; align-items: center; justify-content: center;`

`font-family: var(--font-serif);`

`font-size: 1.1rem;`

`color: var(--gold);`

`margin-bottom: 1rem;`

`}`

`.contact-name { font-size: 0.88rem; font-weight: 500; margin-bottom: 0.2rem; }`

`.contact-role { font-size: 0.7rem; color: var(--text-dim); letter-spacing: 0.06em; margin-bottom: 0.8rem; }`

`.contact-email { font-size: 0.72rem; color: var(--gold); text-decoration: none; }`

`.contact-email:hover { text-decoration: underline; }`

`/* ─── Demo CTA Banner ───────────────────────────────────── */`

`.demo-cta {`

`position: relative;`

`padding: 5rem 3rem;`

`background: var(--navy-mid);`

`border-top: 1px solid var(--border);`

`overflow: hidden;`

`text-align: center;`

`}`

`/* Geometric corner accents */`

`.demo-cta::before, .demo-cta::after {`

`content: '';`

`position: absolute;`

`width: 160px; height: 160px;`

`border: 1px solid var(--border);`

`}`

`.demo-cta::before { top: -40px; left: -40px; }`

`.demo-cta::after { bottom: -40px; right: -40px; }`

`.demo-cta-inner { position: relative; z-index: 1; max-width: 560px; margin: 0 auto; }`

`.demo-eyebrow {`

`font-size: 0.7rem;`

`letter-spacing: 0.22em;`

`text-transform: uppercase;`

`color: var(--gold);`

`margin-bottom: 1rem;`

`}`

`.demo-title {`

`font-family: var(--font-serif);`

`font-size: clamp(1.8rem, 3.5vw, 2.6rem);`

`font-weight: 300;`

`color: var(--cream);`

`line-height: 1.2;`

`margin-bottom: 1.2rem;`

`}`

`.demo-title em { font-style: italic; color: var(--gold); }`

`.demo-subtitle {`

`font-size: 0.9rem;`

`color: var(--text-dim);`

`margin-bottom: 2.4rem;`

`line-height: 1.7;`

`}`

`.demo-btn {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.6rem;`

`background: var(--gold);`

`color: var(--navy);`

`font-family: var(--font-sans);`

`font-size: 0.82rem;`

`font-weight: 500;`

`letter-spacing: 0.12em;`

`text-transform: uppercase;`

`padding: 1rem 2.4rem;`

`border: none;`

`cursor: pointer;`

`text-decoration: none;`

`box-shadow: 0 6px 32px rgba(201,168,76,0.3);`

`transition: background 0.2s, transform 0.15s, box-shadow 0.2s;`

`}`

`.demo-btn:hover {`

`background: var(--gold-light);`

`transform: translateY(-2px);`

`box-shadow: 0 10px 40px rgba(201,168,76,0.4);`

`}`

`/* ─── Footer ────────────────────────────────────────────── */`

`footer {`

`background: #080f1a;`

`border-top: 1px solid var(--border);`

`padding: 2.4rem 3rem;`

`display: flex;`

`align-items: center;`

`justify-content: space-between;`

`gap: 1rem;`

`flex-wrap: wrap;`

`}`

`.footer-logo {`

`font-family: var(--font-serif);`

`font-size: 1rem;`

`letter-spacing: 0.08em;`

`color: var(--cream);`

`}`

`.footer-logo span { color: var(--gold); }`

`.footer-text {`

`font-size: 0.7rem;`

`color: var(--text-dim);`

`letter-spacing: 0.06em;`

`}`

`.footer-links {`

`display: flex;`

`gap: 1.6rem;`

`list-style: none;`

`}`

`.footer-links a {`

`font-size: 0.7rem;`

`letter-spacing: 0.1em;`

`text-transform: uppercase;`

`color: var(--text-dim);`

`text-decoration: none;`

`transition: color 0.2s;`

`}`

`.footer-links a:hover { color: var(--gold); }`

`/* ─── Responsive ────────────────────────────────────────── */`

`@media (max-width: 900px) {`

`nav { padding: 1.2rem 1.5rem; }`

`.nav-links { display: none; }`

`.hero {`

`grid-template-columns: 1fr;`

`padding: 7rem 1.5rem 3rem;`

`gap: 3rem;`

`}`

`.hero::after { display: none; }`

`.content-grid { grid-template-columns: 1fr; }`

`.documents-panel { border-right: none; border-bottom: 1px solid var(--border); padding: 3rem 1.5rem; }`

`.announcements-panel { padding: 3rem 1.5rem; }`

`.quick-access, .contacts-section, .demo-cta { padding: 3rem 1.5rem; }`

`footer { flex-direction: column; align-items: flex-start; gap: 1.2rem; padding: 2rem 1.5rem; }`

`}`

`</style>`

`</head>`

`<body>`

`<!-- ═══════════════════════════════════════`

`NAVIGATION`

`Replace logo/links with SharePoint`

`global navigation or mega menu web part`

`════════════════════════════════════════ -->`

`<nav>`

`<div class="nav-logo">[Firm<span>Name</span>]</div>`

`<ul class="nav-links">`

`<li><a href="#documents">Documents</a></li>`

`<li><a href="#announcements">Updates</a></li>`

`<li><a href="#contacts">Contacts</a></li>`

`<li><a href="#demo">Request Demo</a></li>`

`</ul>`

`<!-- Replace with SharePoint "Sign In" button or profile web part -->`

`<button class="nav-cta" onclick="alert('Replace with SharePoint login / My Profile link')">Sign In</button>`

`</nav>`

`<!-- ═══════════════════════════════════════`

`HERO SECTION`

`Customize headline + stats with your`

`firm's real data before publishing`

`════════════════════════════════════════ -->`

`<header class="hero">`

`<div class="hero-text">`

`<p class="hero-eyebrow">Secure Investor Portal</p>`

`<h1 class="hero-title">Your capital,<br><em>clearly</em> managed.</h1>`

`<p class="hero-subtitle">`

`Access fund performance reports, capital account statements, K-1s,`

`and investor communications — all in one secure, invite-only environment.`

`</p>`

`<div class="hero-actions">`

`<!-- Primary CTA — links to your document library -->`

`<a href="#documents" class="btn-primary">`

`View Documents`

`<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>`

`</a>`

`<!-- Secondary — request portal access -->`

`<a href="mailto:ir@[yourfirm].com?subject=Portal Access Request" class="btn-ghost">`

`Request Access`

`</a>`

`</div>`

`</div>`

`<!-- Firm stats panel — replace with real figures -->`

`<div class="hero-panel">`

`<p class="hero-panel-label">Portfolio at a Glance</p>`

`<div class="stat-grid">`

`<div class="stat-item">`

`<div class="stat-value">$2.4B</div>`

`<div class="stat-label">AUM</div>`

`</div>`

`<div class="stat-item">`

`<div class="stat-value">18.2%</div>`

`<div class="stat-label">Net IRR</div>`

`</div>`

`<div class="stat-divider"></div>`

`<div class="stat-item">`

`<div class="stat-value">6</div>`

`<div class="stat-label">Active Funds</div>`

`</div>`

`<div class="stat-item">`

`<div class="stat-value">Q4 '24</div>`

`<div class="stat-label">Last Reported</div>`

`</div>`

`</div>`

`<div class="access-notice">`

`<div class="lock-icon">`

`<svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/></svg>`

`</div>`

`<span>Access is restricted to verified investors only. All activity is logged and audited.</span>`

`</div>`

`</div>`

`</header>`

`<!-- ═══════════════════════════════════════`

`QUICK ACCESS`

`SHAREPOINT: Replace the cards below`

`with a "Quick Links" web part`

`════════════════════════════════════════ -->`

`<section class="quick-access" id="quick-access">`

`<p class="section-label">Quick Access</p>`

`<!-- ┌─ SHAREPOINT WEB PART DROP ZONE ──────────────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="Quick Links Web Part">`

`<div class="quick-links">`

`<a href="#" class="quick-link-card">`

`<div class="quick-link-icon">`

`<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/></svg>`

`</div>`

`<div class="quick-link-title">Capital Statements</div>`

`<div class="quick-link-desc">Q4 2024 capital account statements and allocations</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="quick-link-icon">`

`<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`

`</div>`

`<div class="quick-link-title">Performance Reports</div>`

`<div class="quick-link-desc">Fund-level performance, IRR, and benchmark comparisons</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="quick-link-icon">`

`<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>`

`</div>`

`<div class="quick-link-title">K-1 Tax Documents</div>`

`<div class="quick-link-desc">Annual K-1 schedules for tax filing</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="quick-link-icon">`

`<svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>`

`</div>`

`<div class="quick-link-title">LP Meetings</div>`

`<div class="quick-link-desc">Recordings, decks, and minutes from LP meetings</div>`

`</a>`

`</div>`

`</div>`

`<!-- └──────────────────────────────────────────────────────┘ -->`

`</section>`

`<!-- ═══════════════════════════════════════`

`DOCUMENTS + ANNOUNCEMENTS`

`════════════════════════════════════════ -->`

`<section class="content-grid">`

`<!-- Documents — replace with Document Library web part -->`

`<div class="documents-panel" id="documents">`

`<span class="gold-line"></span>`

`<p class="section-label">Recent Documents</p>`

`<h2 class="section-title">Fund Materials</h2>`

`<!-- ┌─ SHAREPOINT WEB PART DROP ZONE ────────────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="Document Library Web Part">`

`<div class="doc-list">`

`<a href="#" class="doc-item">`

`<div class="doc-icon">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">Q4 2024 Quarterly Report — Fund III</div>`

`<div class="doc-meta">Updated Mar 12, 2025 · 3.2 MB</div>`

`</div>`

`<span class="doc-badge">New</span>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-icon">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">2024 Annual Investor Letter</div>`

`<div class="doc-meta">Updated Feb 28, 2025 · 1.8 MB</div>`

`</div>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-icon">XLS</div>`

`<div class="doc-info">`

`<div class="doc-name">Capital Account Statement — Q4 2024</div>`

`<div class="doc-meta">Updated Mar 1, 2025 · 540 KB</div>`

`</div>`

`<span class="doc-badge">New</span>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-icon">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">LP Meeting Deck — February 2025</div>`

`<div class="doc-meta">Updated Feb 18, 2025 · 7.1 MB</div>`

`</div>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-icon">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">Schedule K-1 — Tax Year 2024</div>`

`<div class="doc-meta">Updated Mar 3, 2025 · 420 KB</div>`

`</div>`

`</a>`

`</div>`

`</div>`

`<!-- └────────────────────────────────────────────────────┘ -->`

`</div>`

`<!-- Announcements — replace with Announcements web part -->`

`<div class="announcements-panel" id="announcements">`

`<span class="gold-line"></span>`

`<p class="section-label">Updates</p>`

`<h2 class="section-title">Announcements</h2>`

`<!-- ┌─ SHAREPOINT WEB PART DROP ZONE ────────────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="News / Announcements Web Part">`

`<div class="announcement-card">`

`<div class="announcement-date">March 15, 2025</div>`

`<div class="announcement-title">Q4 2024 Reports Now Available</div>`

`<div class="announcement-text">Quarterly performance reports and capital statements for Q4 2024 have been uploaded to the document library.</div>`

`</div>`

`<div class="announcement-card">`

`<div class="announcement-date">February 20, 2025</div>`

`<div class="announcement-title">Annual LP Meeting — Recording Posted</div>`

`<div class="announcement-text">The recording and presentation deck from our February LP meeting are now available in the LP Meetings folder.</div>`

`</div>`

`<div class="announcement-card">`

`<div class="announcement-date">January 8, 2025</div>`

`<div class="announcement-title">K-1 Documents Available March 1</div>`

`<div class="announcement-text">Schedule K-1 tax documents for the 2024 fiscal year will be available in the portal by March 1, 2025.</div>`

`</div>`

`</div>`

`<!-- └────────────────────────────────────────────────────┘ -->`

`</div>`

`</section>`

`<!-- ═══════════════════════════════════════`

`CONTACTS / PEOPLE WEB PART`

`════════════════════════════════════════ -->`

`<section class="contacts-section" id="contacts">`

`<span class="gold-line"></span>`

`<p class="section-label">Your Team</p>`

`<h2 class="section-title">Investor Relations Contacts</h2>`

`<!-- ┌─ SHAREPOINT WEB PART DROP ZONE ──────────────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="People Web Part">`

`<div class="contacts-grid">`

`<div class="contact-card">`

`<div class="contact-avatar">JA</div>`

`<div class="contact-name">Jane Ashford</div>`

`<div class="contact-role">Managing Partner, IR</div>`

`<a href="mailto:j.ashford@[yourfirm].com" class="contact-email">j.ashford@[yourfirm].com</a>`

`</div>`

`<div class="contact-card">`

`<div class="contact-avatar">MR</div>`

`<div class="contact-name">Marcus Reid</div>`

`<div class="contact-role">Director, Investor Relations</div>`

`<a href="mailto:m.reid@[yourfirm].com" class="contact-email">m.reid@[yourfirm].com</a>`

`</div>`

`<div class="contact-card">`

`<div class="contact-avatar">SK</div>`

`<div class="contact-name">Sasha Kim</div>`

`<div class="contact-role">Fund Accounting & Reporting</div>`

`<a href="mailto:s.kim@[yourfirm].com" class="contact-email">s.kim@[yourfirm].com</a>`

`</div>`

`<div class="contact-card">`

`<div class="contact-avatar">TC</div>`

`<div class="contact-name">Thomas Chen</div>`

`<div class="contact-role">Legal & Compliance</div>`

`<a href="mailto:t.chen@[yourfirm].com" class="contact-email">t.chen@[yourfirm].com</a>`

`</div>`

`</div>`

`</div>`

`<!-- └──────────────────────────────────────────────────────┘ -->`

`</section>`

`<!-- ═══════════════════════════════════════`

`DEMO CTA BANNER`

`Primary call-to-action for scheduling`

`a demo of the portal / product`

`════════════════════════════════════════ -->`

`<section class="demo-cta" id="demo">`

`<div class="demo-cta-inner">`

`<p class="demo-eyebrow">See It In Action</p>`

`<h2 class="demo-title">Experience the portal<br><em>firsthand</em>.</h2>`

`<p class="demo-subtitle">`

`Schedule a guided walkthrough with our Investor Relations team.`

`We'll show you how to access your documents, read your statements,`

`and get the most from your secure portal.`

`</p>`

`<!--`

`Replace href with your scheduling link (Calendly, Microsoft Bookings, etc.)`

`Microsoft Bookings integrates natively with Microsoft 365.`

`-->`

`<a href="https://outlook.office.com/bookings/" target="_blank" class="demo-btn">`

`<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`

`Schedule a Demo`

`</a>`

`</div>`

`</section>`

`<!-- ═══════════════════════════════════════`

`FOOTER`

`════════════════════════════════════════ -->`

`<footer>`

`<div class="footer-logo">[Firm<span>Name</span>]</div>`

`<p class="footer-text">© 2025 [Firm Name]. All rights reserved. Access to this portal is restricted and monitored.</p>`

`<ul class="footer-links">`

`<li><a href="#">Privacy Policy</a></li>`

`<li><a href="#">Terms of Use</a></li>`

`<li><a href="mailto:ir@[yourfirm].com">Contact IR</a></li>`

`</ul>`

`</footer>`

`</body>`

`</html>`
'''

Instead of an investment firm, this portal is for investors into a private Tech comapny.

Created a file, shared files

Here’s the redesigned template, rebuilt from the ground up for a private tech company context. Key differences from the finance version:

**What changed:**

- **Aesthetic** — Dark navy/electric blue with a grid background texture and glow effects, fitting for a tech company rather than the gold/cream financial palette
- **Hero metrics** — Now shows ARR growth, active users, total raised, and runway instead of AUM and IRR
- **Documents** — Tailored to tech investor materials: board decks, KPI dashboards, cap tables, financial models, and audited statements
- **Company Updates** — Replaced fund announcements with product launches, ARR milestones, key hires, and partnership news
- **Milestones / Roadmap** — A new timeline section showing funding rounds, growth milestones, and upcoming targets (not present in the finance version)
- **Demo CTA** — Positioned as a product + portal walkthrough, with a note clarifying it’s _“NDA-protected”_ which is appropriate for a private company

**To customize before publishing**, replace all `[Company Name]`, `[company].com`, `[$X]M`, and bracketed placeholders with your real data, then swap each `sp-webpart-zone` block for the corresponding native SharePoint web part.

'''
`!DOCTYPE html>`

`<html lang="en">`

`<head>`

`<meta charset="UTF-8" />`

`<meta name="viewport" content="width=device-width, initial-scale=1.0"/>`

`<title>Investor Portal — [Company Name]</title>`

`<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700&family=Inter:wght@300;400;500&display=swap" rel="stylesheet"/>`

`<style>`

`/* ─── CSS Variables ─────────────────────────────────────── */`

`:root {`

`--bg: #080c14;`

`--bg-2: #0d1220;`

`--bg-3: #111827;`

`--accent: #4f8eff;`

`--accent-2: #7eb3ff;`

`--accent-glow:rgba(79,142,255,0.18);`

`--green: #22d3a0;`

`--white: #f0f4ff;`

`--mid: #8898b8;`

`--dim: #3d4f6e;`

`--border: rgba(79,142,255,0.14);`

`--border-mid: rgba(255,255,255,0.07);`

`--font-head: 'Syne', sans-serif;`

`--font-body: 'Inter', sans-serif;`

`}`

`*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }`

`html { scroll-behavior: smooth; }`

`body {`

`background: var(--bg);`

`color: var(--white);`

`font-family: var(--font-body);`

`font-weight: 300;`

`line-height: 1.7;`

`overflow-x: hidden;`

`}`

`/* ─── Grid background texture ───────────────────────────── */`

`body::before {`

`content: '';`

`position: fixed;`

`inset: 0;`

`background-image:`

`linear-gradient(rgba(79,142,255,0.03) 1px, transparent 1px),`

`linear-gradient(90deg, rgba(79,142,255,0.03) 1px, transparent 1px);`

`background-size: 48px 48px;`

`pointer-events: none;`

`z-index: 0;`

`}`

`/* Radial glow behind hero */`

`body::after {`

`content: '';`

`position: fixed;`

`top: -20%;`

`left: 50%;`

`transform: translateX(-50%);`

`width: 900px;`

`height: 600px;`

`background: radial-gradient(ellipse at center, rgba(79,142,255,0.1) 0%, transparent 70%);`

`pointer-events: none;`

`z-index: 0;`

`}`

`/* ─── Utility ───────────────────────────────────────────── */`

`.accent-bar {`

`display: block;`

`width: 32px; height: 2px;`

`background: var(--accent);`

`margin-bottom: 1.2rem;`

`border-radius: 2px;`

`}`

`.tag {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.4rem;`

`font-size: 0.65rem;`

`letter-spacing: 0.16em;`

`text-transform: uppercase;`

`color: var(--accent);`

`border: 1px solid var(--border);`

`background: var(--accent-glow);`

`padding: 0.3rem 0.75rem;`

`border-radius: 100px;`

`font-family: var(--font-head);`

`font-weight: 500;`

`}`

`.tag-dot {`

`width: 5px; height: 5px;`

`border-radius: 50%;`

`background: var(--green);`

`animation: pulse 2s ease-in-out infinite;`

`}`

`@keyframes pulse {`

`0%, 100% { opacity: 1; transform: scale(1); }`

`50% { opacity: 0.5; transform: scale(0.8); }`

`}`

`/* ─── Navigation ────────────────────────────────────────── */`

`nav {`

`position: fixed;`

`top: 0; left: 0; right: 0;`

`z-index: 100;`

`display: flex;`

`align-items: center;`

`justify-content: space-between;`

`padding: 1.2rem 3rem;`

`background: rgba(8,12,20,0.82);`

`backdrop-filter: blur(20px);`

`border-bottom: 1px solid var(--border-mid);`

`animation: fadeDown 0.7s ease both;`

`}`

`@keyframes fadeDown {`

`from { opacity: 0; transform: translateY(-12px); }`

`to { opacity: 1; transform: translateY(0); }`

`}`

`.nav-logo {`

`display: flex;`

`align-items: center;`

`gap: 0.7rem;`

`font-family: var(--font-head);`

`font-size: 1.1rem;`

`font-weight: 700;`

`letter-spacing: -0.02em;`

`color: var(--white);`

`text-decoration: none;`

`}`

`.logo-mark {`

`width: 28px; height: 28px;`

`background: var(--accent);`

`border-radius: 6px;`

`display: flex; align-items: center; justify-content: center;`

`}`

`.logo-mark svg { color: #fff; }`

`.nav-links {`

`display: flex;`

`gap: 2.2rem;`

`list-style: none;`

`}`

`.nav-links a {`

`font-size: 0.8rem;`

`font-weight: 400;`

`color: var(--mid);`

`text-decoration: none;`

`transition: color 0.2s;`

`letter-spacing: 0.01em;`

`}`

`.nav-links a:hover { color: var(--white); }`

`.nav-right { display: flex; gap: 0.8rem; align-items: center; }`

`.btn-sm-ghost {`

`font-size: 0.75rem;`

`font-family: var(--font-body);`

`color: var(--mid);`

`background: transparent;`

`border: 1px solid var(--border-mid);`

`padding: 0.5rem 1.1rem;`

`cursor: pointer;`

`border-radius: 6px;`

`transition: border-color 0.2s, color 0.2s;`

`}`

`.btn-sm-ghost:hover { border-color: var(--accent); color: var(--white); }`

`.btn-sm-primary {`

`font-size: 0.75rem;`

`font-family: var(--font-body);`

`font-weight: 500;`

`color: #fff;`

`background: var(--accent);`

`border: none;`

`padding: 0.5rem 1.2rem;`

`cursor: pointer;`

`border-radius: 6px;`

`transition: background 0.2s, box-shadow 0.2s;`

`box-shadow: 0 0 16px rgba(79,142,255,0.3);`

`}`

`.btn-sm-primary:hover { background: var(--accent-2); box-shadow: 0 0 24px rgba(79,142,255,0.45); }`

`/* ─── Hero ──────────────────────────────────────────────── */`

`.hero {`

`position: relative;`

`z-index: 1;`

`min-height: 100vh;`

`display: flex;`

`flex-direction: column;`

`align-items: center;`

`justify-content: center;`

`text-align: center;`

`padding: 10rem 2rem 6rem;`

`gap: 0;`

`}`

`.hero-tag { margin-bottom: 1.8rem; animation: fadeUp 0.7s 0.1s ease both; }`

`@keyframes fadeUp {`

`from { opacity: 0; transform: translateY(20px); }`

`to { opacity: 1; transform: translateY(0); }`

`}`

`.hero-title {`

`font-family: var(--font-head);`

`font-size: clamp(2.6rem, 6vw, 5rem);`

`font-weight: 700;`

`letter-spacing: -0.03em;`

`line-height: 1.05;`

`color: var(--white);`

`max-width: 780px;`

`margin-bottom: 1.4rem;`

`animation: fadeUp 0.7s 0.2s ease both;`

`}`

`.hero-title .highlight {`

`background: linear-gradient(135deg, var(--accent), var(--green));`

`-webkit-background-clip: text;`

`-webkit-text-fill-color: transparent;`

`background-clip: text;`

`}`

`.hero-sub {`

`font-size: 1rem;`

`color: var(--mid);`

`max-width: 520px;`

`margin-bottom: 2.8rem;`

`line-height: 1.8;`

`animation: fadeUp 0.7s 0.3s ease both;`

`}`

`.hero-actions {`

`display: flex;`

`gap: 1rem;`

`justify-content: center;`

`flex-wrap: wrap;`

`animation: fadeUp 0.7s 0.4s ease both;`

`margin-bottom: 5rem;`

`}`

`.btn-primary {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.5rem;`

`background: var(--accent);`

`color: #fff;`

`font-family: var(--font-body);`

`font-size: 0.85rem;`

`font-weight: 500;`

`padding: 0.85rem 1.8rem;`

`border: none;`

`border-radius: 8px;`

`cursor: pointer;`

`text-decoration: none;`

`box-shadow: 0 0 24px rgba(79,142,255,0.35);`

`transition: background 0.2s, transform 0.15s, box-shadow 0.2s;`

`}`

`.btn-primary:hover {`

`background: var(--accent-2);`

`transform: translateY(-2px);`

`box-shadow: 0 4px 32px rgba(79,142,255,0.5);`

`}`

`.btn-primary svg { transition: transform 0.2s; }`

`.btn-primary:hover svg { transform: translateX(3px); }`

`.btn-ghost {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.5rem;`

`background: transparent;`

`color: var(--mid);`

`font-family: var(--font-body);`

`font-size: 0.85rem;`

`padding: 0.85rem 1.6rem;`

`border: 1px solid var(--border-mid);`

`border-radius: 8px;`

`cursor: pointer;`

`text-decoration: none;`

`transition: border-color 0.2s, color 0.2s;`

`}`

`.btn-ghost:hover { border-color: var(--accent); color: var(--white); }`

`/* Hero metrics strip */`

`.hero-metrics {`

`display: flex;`

`gap: 0;`

`border: 1px solid var(--border-mid);`

`border-radius: 12px;`

`background: rgba(255,255,255,0.03);`

`backdrop-filter: blur(10px);`

`overflow: hidden;`

`animation: fadeUp 0.7s 0.5s ease both;`

`width: 100%;`

`max-width: 720px;`

`}`

`.metric {`

`flex: 1;`

`padding: 1.4rem 1.8rem;`

`border-right: 1px solid var(--border-mid);`

`text-align: left;`

`}`

`.metric:last-child { border-right: none; }`

`.metric-value {`

`font-family: var(--font-head);`

`font-size: 1.7rem;`

`font-weight: 700;`

`color: var(--white);`

`letter-spacing: -0.03em;`

`line-height: 1;`

`margin-bottom: 0.3rem;`

`}`

`.metric-value .unit { font-size: 1rem; color: var(--accent); }`

`.metric-label {`

`font-size: 0.7rem;`

`color: var(--mid);`

`letter-spacing: 0.04em;`

`}`

`.metric-change {`

`font-size: 0.68rem;`

`color: var(--green);`

`margin-top: 0.2rem;`

`}`

`/* ─── Section shared ────────────────────────────────────── */`

`section { position: relative; z-index: 1; }`

`.section-head {`

`margin-bottom: 2.4rem;`

`}`

`.section-eyebrow {`

`font-size: 0.68rem;`

`letter-spacing: 0.18em;`

`text-transform: uppercase;`

`color: var(--accent);`

`font-family: var(--font-head);`

`font-weight: 600;`

`margin-bottom: 0.6rem;`

`}`

`.section-title {`

`font-family: var(--font-head);`

`font-size: 1.65rem;`

`font-weight: 700;`

`letter-spacing: -0.02em;`

`color: var(--white);`

`}`

`/* ─── SharePoint web part zone ──────────────────────────── */`

`.sp-webpart-zone {`

`border: 1px dashed rgba(79,142,255,0.25);`

`background: rgba(79,142,255,0.03);`

`border-radius: 10px;`

`padding: 1.4rem 1.8rem;`

`position: relative;`

`}`

`.sp-webpart-zone::before {`

`content: attr(data-webpart);`

`position: absolute;`

`top: -0.6rem;`

`left: 1rem;`

`background: var(--bg-2);`

`padding: 0 0.5rem;`

`font-size: 0.6rem;`

`letter-spacing: 0.14em;`

`text-transform: uppercase;`

`color: var(--accent);`

`font-family: var(--font-head);`

`font-weight: 600;`

`}`

`/* ─── Quick Access ──────────────────────────────────────── */`

`.quick-access {`

`padding: 4rem 3rem;`

`border-top: 1px solid var(--border-mid);`

`background: var(--bg-2);`

`}`

`.quick-links {`

`display: grid;`

`grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));`

`gap: 1rem;`

`}`

`.quick-link-card {`

`background: var(--bg-3);`

`border: 1px solid var(--border-mid);`

`border-radius: 10px;`

`padding: 1.6rem;`

`text-decoration: none;`

`color: var(--white);`

`display: flex;`

`flex-direction: column;`

`gap: 0.9rem;`

`transition: border-color 0.2s, transform 0.15s, box-shadow 0.2s;`

`}`

`.quick-link-card:hover {`

`border-color: var(--accent);`

`transform: translateY(-3px);`

`box-shadow: 0 8px 32px rgba(79,142,255,0.12);`

`}`

`.ql-icon {`

`width: 38px; height: 38px;`

`background: var(--accent-glow);`

`border: 1px solid var(--border);`

`border-radius: 8px;`

`display: flex; align-items: center; justify-content: center;`

`color: var(--accent);`

`}`

`.ql-title { font-family: var(--font-head); font-size: 0.88rem; font-weight: 600; }`

`.ql-desc { font-size: 0.72rem; color: var(--mid); line-height: 1.5; }`

`/* ─── Content grid ──────────────────────────────────────── */`

`.content-grid {`

`display: grid;`

`grid-template-columns: 1.5fr 1fr;`

`border-top: 1px solid var(--border-mid);`

`}`

`/* Documents */`

`.documents-panel {`

`padding: 4rem 3rem;`

`border-right: 1px solid var(--border-mid);`

`}`

`.doc-list { display: flex; flex-direction: column; gap: 0; }`

`.doc-item {`

`display: flex;`

`align-items: center;`

`gap: 1rem;`

`padding: 1rem 0.8rem;`

`border-bottom: 1px solid var(--border-mid);`

`text-decoration: none;`

`color: var(--white);`

`border-radius: 6px;`

`transition: background 0.15s, padding-left 0.15s;`

`}`

`.doc-item:hover { background: rgba(79,142,255,0.05); padding-left: 1.2rem; }`

`.doc-item:hover .doc-name { color: var(--accent-2); }`

`.doc-type-badge {`

`font-size: 0.58rem;`

`font-family: var(--font-head);`

`font-weight: 700;`

`letter-spacing: 0.08em;`

`padding: 0.25rem 0.5rem;`

`border-radius: 4px;`

`background: var(--accent-glow);`

`border: 1px solid var(--border);`

`color: var(--accent);`

`flex-shrink: 0;`

`min-width: 36px;`

`text-align: center;`

`}`

`.doc-type-badge.green { background: rgba(34,211,160,0.1); border-color: rgba(34,211,160,0.2); color: var(--green); }`

`.doc-info { flex: 1; min-width: 0; }`

`.doc-name {`

`font-size: 0.83rem;`

`font-weight: 400;`

`white-space: nowrap;`

`overflow: hidden;`

`text-overflow: ellipsis;`

`transition: color 0.15s;`

`}`

`.doc-meta { font-size: 0.67rem; color: var(--mid); margin-top: 0.1rem; }`

`.doc-new {`

`font-size: 0.58rem;`

`font-family: var(--font-head);`

`font-weight: 600;`

`letter-spacing: 0.1em;`

`color: var(--green);`

`border: 1px solid rgba(34,211,160,0.25);`

`border-radius: 100px;`

`padding: 0.15rem 0.5rem;`

`flex-shrink: 0;`

`}`

`/* Updates / Announcements */`

`.updates-panel {`

`background: var(--bg-2);`

`padding: 4rem 2.4rem;`

`}`

`.update-item {`

`padding: 1.2rem 0;`

`border-bottom: 1px solid var(--border-mid);`

`}`

`.update-item:last-child { border-bottom: none; }`

`.update-header {`

`display: flex;`

`align-items: center;`

`justify-content: space-between;`

`margin-bottom: 0.5rem;`

`}`

`.update-category {`

`font-size: 0.62rem;`

`font-family: var(--font-head);`

`font-weight: 600;`

`letter-spacing: 0.12em;`

`text-transform: uppercase;`

`color: var(--accent);`

`}`

`.update-date {`

`font-size: 0.65rem;`

`color: var(--mid);`

`}`

`.update-title {`

`font-family: var(--font-head);`

`font-size: 0.9rem;`

`font-weight: 600;`

`color: var(--white);`

`margin-bottom: 0.35rem;`

`line-height: 1.3;`

`}`

`.update-text {`

`font-size: 0.75rem;`

`color: var(--mid);`

`line-height: 1.6;`

`}`

`/* ─── Milestones / Timeline ─────────────────────────────── */`

`.milestones-section {`

`padding: 4.5rem 3rem;`

`border-top: 1px solid var(--border-mid);`

`background: var(--bg);`

`}`

`.timeline {`

`display: flex;`

`flex-direction: column;`

`gap: 0;`

`margin-top: 2.4rem;`

`position: relative;`

`padding-left: 2rem;`

`}`

`.timeline::before {`

`content: '';`

`position: absolute;`

`left: 0;`

`top: 8px;`

`bottom: 8px;`

`width: 1px;`

`background: var(--border-mid);`

`}`

`.timeline-item {`

`position: relative;`

`padding: 0 0 2rem 2rem;`

`}`

`.timeline-item:last-child { padding-bottom: 0; }`

`.timeline-dot {`

`position: absolute;`

`left: -6px;`

`top: 6px;`

`width: 13px; height: 13px;`

`border-radius: 50%;`

`background: var(--bg-2);`

`border: 2px solid var(--dim);`

`}`

`.timeline-dot.active {`

`background: var(--accent);`

`border-color: var(--accent);`

`box-shadow: 0 0 12px rgba(79,142,255,0.5);`

`}`

`.timeline-dot.done {`

`background: var(--green);`

`border-color: var(--green);`

`}`

`.timeline-date {`

`font-size: 0.65rem;`

`color: var(--mid);`

`letter-spacing: 0.08em;`

`margin-bottom: 0.3rem;`

`}`

`.timeline-title {`

`font-family: var(--font-head);`

`font-size: 0.92rem;`

`font-weight: 600;`

`color: var(--white);`

`margin-bottom: 0.2rem;`

`}`

`.timeline-desc {`

`font-size: 0.75rem;`

`color: var(--mid);`

`line-height: 1.6;`

`}`

`/* ─── People / Contacts ─────────────────────────────────── */`

`.contacts-section {`

`padding: 4.5rem 3rem;`

`border-top: 1px solid var(--border-mid);`

`background: var(--bg-2);`

`}`

`.contacts-grid {`

`display: grid;`

`grid-template-columns: repeat(auto-fit, minmax(210px, 1fr));`

`gap: 1rem;`

`margin-top: 2rem;`

`}`

`.contact-card {`

`background: var(--bg-3);`

`border: 1px solid var(--border-mid);`

`border-radius: 10px;`

`padding: 1.6rem;`

`transition: border-color 0.2s;`

`}`

`.contact-card:hover { border-color: var(--accent); }`

`.contact-avatar {`

`width: 44px; height: 44px;`

`border-radius: 10px;`

`background: var(--accent-glow);`

`border: 1px solid var(--border);`

`display: flex; align-items: center; justify-content: center;`

`font-family: var(--font-head);`

`font-size: 0.95rem;`

`font-weight: 700;`

`color: var(--accent);`

`margin-bottom: 1rem;`

`}`

`.contact-name { font-family: var(--font-head); font-size: 0.9rem; font-weight: 600; margin-bottom: 0.15rem; }`

`.contact-role { font-size: 0.7rem; color: var(--mid); margin-bottom: 0.8rem; }`

`.contact-email { font-size: 0.72rem; color: var(--accent); text-decoration: none; }`

`.contact-email:hover { text-decoration: underline; }`

`/* ─── Demo CTA ──────────────────────────────────────────── */`

`.demo-cta {`

`position: relative;`

`padding: 6rem 2rem;`

`background: var(--bg);`

`border-top: 1px solid var(--border-mid);`

`overflow: hidden;`

`text-align: center;`

`z-index: 1;`

`}`

`/* Glow blob */`

`.demo-cta::before {`

`content: '';`

`position: absolute;`

`top: 50%; left: 50%;`

`transform: translate(-50%, -50%);`

`width: 600px; height: 400px;`

`background: radial-gradient(ellipse, rgba(79,142,255,0.12) 0%, transparent 70%);`

`pointer-events: none;`

`}`

`/* Corner brackets */`

`.corner {`

`position: absolute;`

`width: 24px; height: 24px;`

`border-color: var(--dim);`

`border-style: solid;`

`border-width: 0;`

`}`

`.corner-tl { top: 2rem; left: 2rem; border-top-width: 1px; border-left-width: 1px; }`

`.corner-tr { top: 2rem; right: 2rem; border-top-width: 1px; border-right-width: 1px; }`

`.corner-bl { bottom: 2rem; left: 2rem; border-bottom-width: 1px; border-left-width: 1px; }`

`.corner-br { bottom: 2rem; right: 2rem; border-bottom-width: 1px; border-right-width: 1px; }`

`.demo-inner { position: relative; z-index: 1; max-width: 560px; margin: 0 auto; }`

`.demo-tag { margin-bottom: 1.6rem; }`

`.demo-title {`

`font-family: var(--font-head);`

`font-size: clamp(1.9rem, 4vw, 3rem);`

`font-weight: 700;`

`letter-spacing: -0.03em;`

`color: var(--white);`

`line-height: 1.1;`

`margin-bottom: 1rem;`

`}`

`.demo-title .highlight {`

`background: linear-gradient(135deg, var(--accent), var(--green));`

`-webkit-background-clip: text;`

`-webkit-text-fill-color: transparent;`

`background-clip: text;`

`}`

`.demo-sub {`

`font-size: 0.9rem;`

`color: var(--mid);`

`line-height: 1.75;`

`margin-bottom: 2.4rem;`

`}`

`.demo-btn {`

`display: inline-flex;`

`align-items: center;`

`gap: 0.6rem;`

`background: var(--accent);`

`color: #fff;`

`font-family: var(--font-body);`

`font-size: 0.88rem;`

`font-weight: 500;`

`padding: 1rem 2.2rem;`

`border: none;`

`border-radius: 8px;`

`cursor: pointer;`

`text-decoration: none;`

`box-shadow: 0 0 32px rgba(79,142,255,0.4);`

`transition: background 0.2s, transform 0.15s, box-shadow 0.2s;`

`margin-bottom: 1rem;`

`}`

`.demo-btn:hover {`

`background: var(--accent-2);`

`transform: translateY(-2px);`

`box-shadow: 0 4px 48px rgba(79,142,255,0.55);`

`}`

`.demo-disclaimer {`

`font-size: 0.68rem;`

`color: var(--dim);`

`letter-spacing: 0.04em;`

`}`

`/* ─── Footer ────────────────────────────────────────────── */`

`footer {`

`background: #050810;`

`border-top: 1px solid var(--border-mid);`

`padding: 2.4rem 3rem;`

`display: flex;`

`align-items: center;`

`justify-content: space-between;`

`flex-wrap: wrap;`

`gap: 1.2rem;`

`}`

`.footer-logo {`

`display: flex;`

`align-items: center;`

`gap: 0.6rem;`

`font-family: var(--font-head);`

`font-size: 0.95rem;`

`font-weight: 700;`

`color: var(--white);`

`text-decoration: none;`

`}`

`.footer-logo-mark {`

`width: 22px; height: 22px;`

`background: var(--accent);`

`border-radius: 5px;`

`}`

`.footer-copy { font-size: 0.68rem; color: var(--dim); }`

`.footer-links {`

`display: flex;`

`gap: 1.6rem;`

`list-style: none;`

`}`

`.footer-links a {`

`font-size: 0.7rem;`

`color: var(--mid);`

`text-decoration: none;`

`transition: color 0.2s;`

`}`

`.footer-links a:hover { color: var(--accent); }`

`/* ─── Responsive ────────────────────────────────────────── */`

`@media (max-width: 900px) {`

`nav { padding: 1rem 1.5rem; }`

`.nav-links { display: none; }`

`.hero { padding: 8rem 1.5rem 4rem; }`

`.hero-metrics { flex-direction: column; }`

`.metric { border-right: none; border-bottom: 1px solid var(--border-mid); }`

`.metric:last-child { border-bottom: none; }`

`.quick-access, .milestones-section, .contacts-section { padding: 3rem 1.5rem; }`

`.content-grid { grid-template-columns: 1fr; }`

`.documents-panel { border-right: none; border-bottom: 1px solid var(--border-mid); padding: 3rem 1.5rem; }`

`.updates-panel { padding: 3rem 1.5rem; }`

`footer { flex-direction: column; align-items: flex-start; padding: 2rem 1.5rem; }`

`}`

`</style>`

`</head>`

`<body>`

`<!-- ═══════════════════════════════════════`

`NAVIGATION`

`Replace with SharePoint global nav`

`or Mega Menu web part`

`════════════════════════════════════════ -->`

`<nav>`

`<a href="#" class="nav-logo">`

`<div class="logo-mark">`

`<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`

`</div>`

`[Company Name]`

`</a>`

`<ul class="nav-links">`

`<li><a href="#documents">Documents</a></li>`

`<li><a href="#milestones">Milestones</a></li>`

`<li><a href="#contacts">Team</a></li>`

`<li><a href="#demo">Schedule Demo</a></li>`

`</ul>`

`<div class="nav-right">`

`<button class="btn-sm-ghost" onclick="alert('Replace with SharePoint sign-in / My Profile')">Sign In</button>`

`<a href="#demo" class="btn-sm-primary">Schedule Demo</a>`

`</div>`

`</nav>`

`<!-- ═══════════════════════════════════════`

`HERO`

`Customize headline, metrics, and CTAs`

`with your company's real data`

`════════════════════════════════════════ -->`

`<header class="hero">`

`<div class="hero-tag">`

`<span class="tag">`

`<span class="tag-dot"></span>`

`Private Investor Portal — Invite Only`

`</span>`

`</div>`

`<h1 class="hero-title">`

`Your window into<br>`

`<span class="highlight">[Company Name]</span>`

`</h1>`

`<p class="hero-sub">`

`Access real-time performance data, financial reports, board updates,`

`and company milestones — all in one secure, permission-controlled portal.`

`</p>`

`<div class="hero-actions">`

`<a href="#documents" class="btn-primary">`

`View Reports`

`<svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><line x1="5" y1="12" x2="19" y2="12"/><polyline points="12 5 19 12 12 19"/></svg>`

`</a>`

`<a href="mailto:investors@[company].com?subject=Investor Portal Access Request" class="btn-ghost">`

`Request Access`

`</a>`

`</div>`

`<!-- Company metrics strip — replace with real figures -->`

`<div class="hero-metrics">`

`<div class="metric">`

`<div class="metric-value">$<span class="unit">—</span>M</div>`

`<div class="metric-label">Total Raised</div>`

`<div class="metric-change">Series [X] · [Month Year]</div>`

`</div>`

`<div class="metric">`

`<div class="metric-value">—<span class="unit">%</span></div>`

`<div class="metric-label">ARR Growth YoY</div>`

`<div class="metric-change">↑ vs prior period</div>`

`</div>`

`<div class="metric">`

`<div class="metric-value">—<span class="unit">K</span></div>`

`<div class="metric-label">Active Users</div>`

`<div class="metric-change">↑ MoM</div>`

`</div>`

`<div class="metric">`

`<div class="metric-value">—</div>`

`<div class="metric-label">Runway (Months)</div>`

`<div class="metric-change">as of [Quarter]</div>`

`</div>`

`</div>`

`</header>`

`<!-- ═══════════════════════════════════════`

`QUICK ACCESS`

`Replace cards with SharePoint`

`Quick Links web part`

`════════════════════════════════════════ -->`

`<section class="quick-access" id="quick-access">`

`<div class="section-head">`

`<div class="section-eyebrow">Jump To</div>`

`<div class="section-title">Quick Access</div>`

`</div>`

`<!-- ┌─ SHAREPOINT: Quick Links Web Part ───────────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="Quick Links Web Part">`

`<div class="quick-links">`

`<a href="#" class="quick-link-card">`

`<div class="ql-icon">`

`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/><polyline points="14 2 14 8 20 8"/><line x1="16" y1="13" x2="8" y2="13"/><line x1="16" y1="17" x2="8" y2="17"/></svg>`

`</div>`

`<div class="ql-title">Financial Reports</div>`

`<div class="ql-desc">P&L, balance sheet, cash flow statements</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="ql-icon">`

`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><polyline points="22 12 18 12 15 21 9 3 6 12 2 12"/></svg>`

`</div>`

`<div class="ql-title">KPI Dashboard</div>`

`<div class="ql-desc">ARR, churn, CAC, LTV, NRR metrics</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="ql-icon">`

`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="2" y="3" width="20" height="14" rx="2"/><line x1="8" y1="21" x2="16" y2="21"/><line x1="12" y1="17" x2="12" y2="21"/></svg>`

`</div>`

`<div class="ql-title">Board Decks</div>`

`<div class="ql-desc">Quarterly board meeting presentations</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="ql-icon">`

`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"/><circle cx="12" cy="10" r="3"/></svg>`

`</div>`

`<div class="ql-title">Cap Table</div>`

`<div class="ql-desc">Current ownership, option pool, dilution</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="ql-icon">`

`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/><path d="M23 21v-2a4 4 0 0 0-3-3.87"/><path d="M16 3.13a4 4 0 0 1 0 7.75"/></svg>`

`</div>`

`<div class="ql-title">Investor Updates</div>`

`<div class="ql-desc">Monthly and quarterly investor letters</div>`

`</a>`

`<a href="#" class="quick-link-card">`

`<div class="ql-icon">`

`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`

`</div>`

`<div class="ql-title">Schedule Demo</div>`

`<div class="ql-desc">Book a 1:1 walkthrough with our team</div>`

`</a>`

`</div>`

`</div>`

`<!-- └──────────────────────────────────────────────────────┘ -->`

`</section>`

`<!-- ═══════════════════════════════════════`

`DOCUMENTS + UPDATES`

`════════════════════════════════════════ -->`

`<section class="content-grid">`

`<!-- Document Library -->`

`<div class="documents-panel" id="documents">`

`<span class="accent-bar"></span>`

`<div class="section-head">`

`<div class="section-eyebrow">Secure Library</div>`

`<div class="section-title">Documents</div>`

`</div>`

`<!-- ┌─ SHAREPOINT: Document Library Web Part ────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="Document Library Web Part">`

`<div class="doc-list">`

`<a href="#" class="doc-item">`

`<div class="doc-type-badge">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">Q4 2024 Investor Update & Financial Summary</div>`

`<div class="doc-meta">Mar 10, 2025 · 2.4 MB</div>`

`</div>`

`<span class="doc-new">New</span>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-type-badge">PPTX</div>`

`<div class="doc-info">`

`<div class="doc-name">Board Meeting Deck — Q4 2024</div>`

`<div class="doc-meta">Feb 22, 2025 · 6.8 MB</div>`

`</div>`

`<span class="doc-new">New</span>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-type-badge green">XLS</div>`

`<div class="doc-info">`

`<div class="doc-name">KPI Dashboard — February 2025</div>`

`<div class="doc-meta">Mar 5, 2025 · 890 KB</div>`

`</div>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-type-badge">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">Cap Table — Post Series B (Feb 2025)</div>`

`<div class="doc-meta">Feb 15, 2025 · 310 KB</div>`

`</div>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-type-badge">PDF</div>`

`<div class="doc-info">`

`<div class="doc-name">Audited Financial Statements — FY 2023</div>`

`<div class="doc-meta">Apr 12, 2024 · 4.1 MB</div>`

`</div>`

`</a>`

`<a href="#" class="doc-item">`

`<div class="doc-type-badge green">XLS</div>`

`<div class="doc-info">`

`<div class="doc-name">3-Year Financial Model (Updated)</div>`

`<div class="doc-meta">Jan 30, 2025 · 1.2 MB</div>`

`</div>`

`</a>`

`</div>`

`</div>`

`<!-- └────────────────────────────────────────────────────┘ -->`

`</div>`

`<!-- Updates / Announcements -->`

`<div class="updates-panel" id="updates">`

`<span class="accent-bar"></span>`

`<div class="section-head">`

`<div class="section-eyebrow">Latest</div>`

`<div class="section-title">Company Updates</div>`

`</div>`

`<!-- ┌─ SHAREPOINT: News / Announcements Web Part ────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="News / Announcements Web Part">`

`<div class="update-item">`

`<div class="update-header">`

`<span class="update-category">Product</span>`

`<span class="update-date">Mar 14, 2025</span>`

`</div>`

`<div class="update-title">v3.0 Platform Launch — GA Released</div>`

`<div class="update-text">Our flagship platform hit general availability. 40+ enterprise customers migrated in week one with zero critical incidents.</div>`

`</div>`

`<div class="update-item">`

`<div class="update-header">`

`<span class="update-category">Growth</span>`

`<span class="update-date">Mar 1, 2025</span>`

`</div>`

`<div class="update-title">ARR Milestone: $[X]M Reached</div>`

`<div class="update-text">We crossed a significant ARR milestone ahead of plan. Full breakdown in the Q4 investor update now available in documents.</div>`

`</div>`

`<div class="update-item">`

`<div class="update-header">`

`<span class="update-category">Team</span>`

`<span class="update-date">Feb 18, 2025</span>`

`</div>`

`<div class="update-title">VP of Sales Hire — [Name] Joins</div>`

`<div class="update-text">We've brought on a seasoned VP of Sales from [Previous Company] to lead our enterprise go-to-market push in 2025.</div>`

`</div>`

`<div class="update-item">`

`<div class="update-header">`

`<span class="update-category">Partnership</span>`

`<span class="update-date">Jan 30, 2025</span>`

`</div>`

`<div class="update-title">Strategic Partnership Signed with [Partner]</div>`

`<div class="update-text">We've signed a distribution agreement that opens access to [Partner]'s 10,000+ customer base. Details in the board deck.</div>`

`</div>`

`</div>`

`<!-- └────────────────────────────────────────────────────┘ -->`

`</div>`

`</section>`

`<!-- ═══════════════════════════════════════`

`MILESTONES / PRODUCT ROADMAP`

`Replace with SharePoint News or a`

`custom list web part`

`════════════════════════════════════════ -->`

`<section class="milestones-section" id="milestones">`

`<span class="accent-bar"></span>`

`<div class="section-head">`

`<div class="section-eyebrow">Progress</div>`

`<div class="section-title">Company Milestones</div>`

`</div>`

`<!-- ┌─ SHAREPOINT: Custom List or News Web Part ───────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="Custom List / Timeline Web Part">`

`<div class="timeline">`

`<div class="timeline-item">`

`<div class="timeline-dot done"></div>`

`<div class="timeline-date">Q1 2024</div>`

`<div class="timeline-title">Series A Closed — $[X]M</div>`

`<div class="timeline-desc">Oversubscribed round led by [Lead Investor]. Proceeds deployed to engineering and GTM.</div>`

`</div>`

`<div class="timeline-item">`

`<div class="timeline-dot done"></div>`

`<div class="timeline-date">Q3 2024</div>`

`<div class="timeline-title">Reached $[X]M ARR</div>`

`<div class="timeline-desc">Crossed ARR milestone 2 quarters ahead of plan. NRR at 118%.</div>`

`</div>`

`<div class="timeline-item">`

`<div class="timeline-dot done"></div>`

`<div class="timeline-date">Q4 2024</div>`

`<div class="timeline-title">Series B Closed — $[X]M</div>`

`<div class="timeline-desc">Led by [Lead Investor] with participation from existing investors. 18-month runway.</div>`

`</div>`

`<div class="timeline-item">`

`<div class="timeline-dot active"></div>`

`<div class="timeline-date">Q1 2025 — Current</div>`

`<div class="timeline-title">v3.0 Platform GA + Enterprise Push</div>`

`<div class="timeline-desc">Platform launched. Enterprise sales motion underway with 6 active enterprise pilots.</div>`

`</div>`

`<div class="timeline-item">`

`<div class="timeline-dot"></div>`

`<div class="timeline-date">Q3 2025 — Target</div>`

`<div class="timeline-title">International Expansion — [Region]</div>`

`<div class="timeline-desc">Planned launch in [region] market with localized product and dedicated sales hire.</div>`

`</div>`

`<div class="timeline-item">`

`<div class="timeline-dot"></div>`

`<div class="timeline-date">Q4 2025 — Target</div>`

`<div class="timeline-title">Profitability / Series C Preparation</div>`

`<div class="timeline-desc">Path to operating profitability or Series C raise depending on growth trajectory.</div>`

`</div>`

`</div>`

`</div>`

`<!-- └──────────────────────────────────────────────────────┘ -->`

`</section>`

`<!-- ═══════════════════════════════════════`

`TEAM CONTACTS`

`Replace with SharePoint People web part`

`════════════════════════════════════════ -->`

`<section class="contacts-section" id="contacts">`

`<span class="accent-bar"></span>`

`<div class="section-head">`

`<div class="section-eyebrow">Leadership</div>`

`<div class="section-title">Your Points of Contact</div>`

`</div>`

`<!-- ┌─ SHAREPOINT: People Web Part ────────────────────────┐ -->`

`<div class="sp-webpart-zone" data-webpart="People Web Part">`

`<div class="contacts-grid">`

`<div class="contact-card">`

`<div class="contact-avatar">JD</div>`

`<div class="contact-name">Jane Doe</div>`

`<div class="contact-role">CEO & Co-Founder</div>`

`<a href="mailto:jane@[company].com" class="contact-email">jane@[company].com</a>`

`</div>`

`<div class="contact-card">`

`<div class="contact-avatar">MS</div>`

`<div class="contact-name">Mark Smith</div>`

`<div class="contact-role">CFO</div>`

`<a href="mailto:mark@[company].com" class="contact-email">mark@[company].com</a>`

`</div>`

`<div class="contact-card">`

`<div class="contact-avatar">AL</div>`

`<div class="contact-name">Amy Lee</div>`

`<div class="contact-role">Head of Investor Relations</div>`

`<a href="mailto:amy@[company].com" class="contact-email">amy@[company].com</a>`

`</div>`

`<div class="contact-card">`

`<div class="contact-avatar">RK</div>`

`<div class="contact-name">Raj Kumar</div>`

`<div class="contact-role">CTO & Co-Founder</div>`

`<a href="mailto:raj@[company].com" class="contact-email">raj@[company].com</a>`

`</div>`

`</div>`

`</div>`

`<!-- └──────────────────────────────────────────────────────┘ -->`

`</section>`

`<!-- ═══════════════════════════════════════`

`DEMO CTA`

`Primary call-to-action — scheduling`

`a portal / product walkthrough`

`════════════════════════════════════════ -->`

`<section class="demo-cta" id="demo">`

`<div class="corner corner-tl"></div>`

`<div class="corner corner-tr"></div>`

`<div class="corner corner-bl"></div>`

`<div class="corner corner-br"></div>`

`<div class="demo-inner">`

`<div class="demo-tag">`

`<span class="tag">`

`<svg width="10" height="10" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`

`Schedule a Session`

`</span>`

`</div>`

`<h2 class="demo-title">`

`See <span class="highlight">[Company Name]</span><br>in action.`

`</h2>`

`<p class="demo-sub">`

`Book a guided walkthrough of the product and the portal with our team.`

`We'll show you where we're headed, answer your questions, and walk through`

`the latest numbers directly.`

`</p>`

`<!--`

`Replace href with your booking link.`

`Microsoft Bookings integrates natively with M365:`

`https://outlook.office.com/bookings/`

`Or use Calendly, HubSpot Meetings, etc.`

`-->`

`<a href="https://outlook.office.com/bookings/" target="_blank" class="demo-btn">`

`<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="4" width="18" height="18" rx="2"/><line x1="16" y1="2" x2="16" y2="6"/><line x1="8" y1="2" x2="8" y2="6"/><line x1="3" y1="10" x2="21" y2="10"/></svg>`

`Schedule a Demo`

`</a>`

`<p class="demo-disclaimer">30-minute session · Video call · NDA-protected</p>`

`</div>`

`</section>`

`<!-- ═══════════════════════════════════════`

`FOOTER`

`════════════════════════════════════════ -->`

`<footer>`

`<a href="#" class="footer-logo">`

`<div class="footer-logo-mark"></div>`

`[Company Name]`

`</a>`

`<p class="footer-copy">© 2025 [Company Name], Inc. All rights reserved. Access is restricted to verified investors. All activity is logged.</p>`

`<ul class="footer-links">`

`<li><a href="#">Privacy Policy</a></li>`

`<li><a href="#">Terms of Use</a></li>`

`<li><a href="mailto:investors@[company].com">Contact IR</a></li>`

`</ul>`

`</footer>`

`</body>`

`</html>`
'''

