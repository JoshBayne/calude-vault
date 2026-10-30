Our company uses the Microsoft business premium subscription to office 365. How can I automate the import of personal calendars of specific users into a group calendar so that all members of that team can see conflicts of time. Assume all users except myself are tech illiterate and I have the highest admin access to the entire suite.

Business Premium gives you everything you need, and you don’t need to touch anyone’s computer. The setup has two parts: let one account read the personal calendars, then have an automated job copy them into a shared team calendar.

### First, check whether you need copying at all

Everyone in your tenant can already see each other’s free/busy by default. When anyone creates a meeting in Outlook or Teams, the **Scheduling Assistant** shows conflicts across all invitees. If the goal is “avoid booking people at the same time,” you may already have it. The steps below are for when the team wants **one visible calendar showing everyone’s blocks at a glance**.

### Step 1: Create the team calendar

Use a **Microsoft 365 Group** (or the one behind a Teams team). Its calendar appears automatically in every member’s Outlook and Teams, so the non-technical users have nothing to set up.

One caveat to test early: Power Automate’s calendar picker doesn’t always list group calendars. If yours doesn’t appear, use a **shared mailbox** calendar instead and give the team Reviewer access.

### Step 2: Give a service account read access to each personal calendar

Use a dedicated licensed account (e.g. `calendar-sync@yourco.com`) rather than your own, so the automation doesn’t break when your password changes. In Exchange Online PowerShell:

powershell

```powershell
Connect-ExchangeOnline
$users = "alice@yourco.com","bob@yourco.com","carol@yourco.com"
foreach ($u in $users) {
  Add-MailboxFolderPermission -Identity "${u}:\Calendar" -User calendar-sync@yourco.com -AccessRights Reviewer
}
```

If it errors, your calendar folder may have a localized name. Run `Get-MailboxFolderStatistics $u -FolderScope Calendar` to find it.

### Step 3: Build one Power Automate flow per person

Power Automate with the Office 365 Outlook connector is included in Business Premium. Sign in as the service account at make.powerautomate.com.

1. Trigger: **Recurrence** (every 15 to 30 minutes).
2. Action: **Get calendar view of events (V3)**, with the person’s calendar selected (it appears once Step 2 is done) and a window of today to +60 days.
3. Action: **Apply to each** event, then **Create event (V4)** on the team calendar:
    - Subject: `Alice – Busy` (or include the title if the team agrees to that)
    - Same start and end times
    - Skip events where Show As is Free
4. Before the loop, delete the previously copied events in that window, so edits and cancellations propagate and you don’t get duplicates. Tag copies with a category like `Synced-Alice` so you only delete your own.

Once one flow works, use **Save As** to clone it for each person and change the source calendar and name.

### Things to decide

- **Privacy:** Copy only “Busy” plus the person’s name unless people agree to share titles. Tell staff the team calendar exists. Flows read private events too, so don’t copy their details.
- **Flicker:** Delete-and-recreate is simple but can briefly show gaps. A more polished alternative is a small Microsoft Graph script using delta queries, run from Azure Automation. It updates in place and uses app-only permissions, so there’s no service-account mailbox dependency. It needs a small Azure subscription.
- **Ownership:** Document the flows, because they’re tied to the service account. Make sure that account is exempt from MFA/password-expiry policies that would break the connection.
- **Scale:** For more than about 10 to 15 people, the Graph approach is more maintainable than a flow per person.

I’d say try the Power Automate route for one user first and see how the team reacts. I can write the Graph/PowerShell script for the more robust version, or lay out the exact flow actions step by step, if you’d like.