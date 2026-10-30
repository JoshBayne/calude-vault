I would like to use Notifuse on a self hosted set up for email messaging my clients. Currently we use Square as a payment processor and reminder system for client events. I would like to connect my Square payment processor to Notifuse to handle reminders and confirmation emails. How can I have the two systems talk to each other to facilitate this?

Notifuse and Square don’t have a native plug-and-play connector — you’ll need a small middleware service that listens to Square’s webhooks and calls Notifuse’s transactional API. Here’s the shape of it:

**1. Square side — set up webhooks**  
Square pushes real-time events to a URL you register (must be public HTTPS, respond 2xx within 10s):

- `booking.created` / `booking.updated` — for confirmation and reminder triggers on client events
- `payment.created` / `payment.updated` — for payment confirmation emails
- You subscribe to specific event types in the Developer Console or via the Webhook Subscriptions API, and Square signs each payload so you can verify it’s legitimate.

**2. Middleware — the glue app**  
This is the piece you build (a small Node/Python/Go service works fine):

- Receives Square webhook POSTs, verifies the signature
- Parses the event (e.g., a new booking, a completed payment)
- Maps Square’s customer/booking data to a Notifuse contact + template variables
- Calls Notifuse’s transactional email REST API to send the confirmation immediately

**3. Reminders (not just confirmations)**  
Square webhooks fire on state changes, not on a countdown to an event — so “remind 24 hours before the appointment” needs your middleware to store the booking’s `start_at` time and schedule the send itself (a cron job, a queue with delayed jobs, or Notifuse’s automation/flow builder with a delay node if you feed it the right trigger data).

**4. Notifuse side**

- Create transactional email templates (confirmation, reminder) with Liquid variables like `{{ contact.first_name }}`, appointment time, etc.
- Your middleware calls the transactional API with the contact’s email and the template variables pulled from the Square payload
- Optionally sync Square customers into Notifuse’s contact list via the API so you also have them for newsletters/marketing later

**Rough flow:**

```
Square (booking/payment event) 
   → webhook POST to your server 
   → verify signature, parse event 
   → (if reminder) schedule for later, else send now 
   → call Notifuse transactional API with template + variables 
   → Notifuse sends the email
```

Want me to sketch out the actual middleware code (e.g., a Node/Express service handling the webhook verification and Notifuse API call)?

create a step by step guide and generate the needed middleware code when we reach that step in the process. Ask any questions that may be required to ensure that the connection works.

A few things will shape the middleware, so let me nail those down before writing code.

What does Square handle for you today — appointments/bookings, invoices, or one-off payments (or a mix)?Invoices API

What language/runtime should the middleware be written in?Not sure — recommend one

Where will this middleware run so Square can reach it via public HTTPS?Docker container, self-hosted

Good — I now have everything I need (Square’s Invoices webhook events, signature scheme, and Notifuse’s transactional API shape). Here’s the full guide, and I’ll generate the middleware alongside each relevant step.

Now let me build the guide and code together.

### Step 1 — Map the events you actually need

Since you’re on the **Invoices API** (not Bookings), here’s what Square can tell your middleware, and there’s one important nuance: Square has its own built-in invoice reminders (`payment_requests[].reminders`), but those are sent _by Square_, not routed anywhere — so if you want Notifuse to own reminder emails, you should leave Square’s native reminders off and let the middleware handle scheduling instead.

Square webhook events relevant to you: invoice.created, invoice.published (transitions from draft to non-draft), invoice.updated, invoice.payment_made (published when a payment associated with an invoice is completed), invoice.canceled, invoice.deleted, invoice.refunded (published when a refund is applied toward a payment of an invoice), and invoice.scheduled_charge_failed (published when an automatic scheduled payment for an invoice has failed). [Square](https://developer.squareup.com/reference/square/invoices-api/webhooks)

Useful detail: the invoice payload itself already contains the recipient’s email — primary_recipient includes email_address, given_name, family_name, and phone_number [github](https://github.com/square/connect-javascript-sdk/blob/HEAD/docs/InvoiceRecipient.md) — so the middleware never needs a separate call to Square’s Customers API just to get an email address.

### Step 2 — Square-side setup

Create/open your Square applicationIn the Square Developer Dashboard, open your existing application (or create one). You'll need it in Production mode eventually, but build against Sandbox first.

Grant the right permissionsYour access token / OAuth scope needs INVOICES_READ at minimum (INVOICES_WRITE and ORDERS_READ too if you ever create invoices via API). CUSTOMERS_READ isn't required since recipient email comes embedded in the invoice payload.

Create a webhook subscriptionIn the app's Webhooks tab, add a subscription with your notification URL (e.g. https://middleware.yourdomain.com/webhooks/square) and subscribe to: invoice.published, invoice.updated, invoice.payment_made, invoice.scheduled_charge_failed, invoice.canceled, invoice.refunded. The URL must be public HTTPS and respond with a 2xx status within 10 seconds.

Save the signature keyEach webhook subscription gets its own signing secret. Copy it — you'll use it to verify that incoming requests really came from Square, via the x-square-hmacsha256-signature header.

Turn off Square's native reminders on new invoicesWhen creating invoices (via the Dashboard or API), leave payment_requests[].reminders empty so Square doesn't also send its own reminder emails alongside Notifuse's.

1

2

3

4

5

### Step 3 — Notifuse-side setup

1. In your self-hosted Notifuse admin, create (or use) a **workspace** for this integration.
2. Under **Admins & API Keys**, generate an API key scoped to that workspace.
3. Build four **transactional templates**, and note the exact template ID for each (these IDs go in the middleware’s `.env`):
    - `invoice-sent` — “Your invoice is ready”
    - `payment-received` — payment confirmation / receipt
    - `invoice-reminder` — “Your invoice is due soon”
    - `payment-failed` — automatic charge failed, action needed
4. In each template, use Liquid variables matching what the middleware will send: `{{ invoice_number }}`, `{{ customer_name }}`, `{{ amount }}`, `{{ due_date }}`, `{{ invoice_url }}`, etc.

### Step 4 — The middleware

Now the code. It’s a small Express service with SQLite for tracking invoice state (needed because Square doesn’t send a “due soon” webhook — the middleware has to watch due dates itself) and a daily cron job for reminders.

### Step 5 — Deploy and expose it publicly

Square requires a public HTTPS URL that responds within 10 seconds — so your Docker container needs a reverse proxy in front of it (Caddy is the simplest for automatic HTTPS via Let’s Encrypt, or use whatever you already run in front of Notifuse).

### Step 6 — Test before going live

Fill in .env from .env.exampleCopy .env.example to .env and fill in your Sandbox Square signature key + webhook URL, and your Notifuse workspace/API key/template IDs.

Build and run locallycd square-notifuse-middleware && cp .env.example .env && docker compose up --build. Check that GET /health returns {"ok": true}.

Trigger sandbox events from SquareIn the Developer Dashboard's Webhooks tab, use "Send Test Event" for invoice.published and invoice.payment_made, or create/publish a real sandbox invoice via API Explorer. Watch your container logs to confirm the signature validates and Notifuse accepts the send.

Confirm the email actually arrivesCheck the target inbox (or Notifuse's activity/logs view) to confirm the template variables rendered correctly — customer name, amount, due date, invoice link.

Test the reminder path manuallyTemporarily set REMINDER_CRON to run a minute from now and REMINDER_DAYS_BEFORE high enough to catch a test invoice's due date, confirm it fires once and sets reminder_sent, then restore the normal daily schedule.

Switch to productionSwap in your production Square signature key and access token, subscribe the same event types on your production webhook subscription, and point SQUARE_WEBHOOK_URL/NOTIFUSE_API_URL at their real values.

1

2

3

4

5

6

**A couple things worth flagging before you go live:**

1. **Notifuse endpoint path** — I’ve used `/api/workspaces/{workspace_id}/messages/send` based on the request shape documented at docs.notifuse.com, but since you’re self-hosted, double-check the exact path against your instance’s own API reference (`https://your-notifuse-domain/api-reference`) — self-hosted builds can lag or diverge slightly from cloud docs.
2. **Square’s native reminders** — leave `payment_requests[].reminders` empty on invoices so you don’t get duplicate reminder emails (one from Square, one from Notifuse).
3. **Reverse proxy** — the middleware itself doesn’t terminate HTTPS; it needs to sit behind Caddy/nginx (example included) since Square requires a public HTTPS notification URL.

Want me to also add a `docker-compose` block that folds this directly into your existing Notifuse compose file, or write the SQL/logic for syncing Square customers into Notifuse contacts (so they’re also available for marketing broadcasts later)?

Server

JS

Package

Code·JSON

.env

EXAMPLE

Dockerfile

Docker compose

YML

Caddyfile

EXAMPLE

Verified existing invoice URL availability in email templates.

Yes — actually, this is already wired in. Let me confirm exactly where by checking the current file:

Confirmed — it’s already flowing through end to end:

|Where|What happens|
|---|---|
|**Square**|Every invoice object includes `public_url` — a hosted, shareable page where the client can view and pay, no login required|
|**Middleware**|`extractInvoiceFields` pulls it into `fields.public_url`, stored in SQLite as `public_url`|
|**Every email sent**|Passed as `invoice_url` in the data payload — `invoice-sent`, `deposit-received`, `invoice-confirmation`, `invoice-reminder`, and `payment-failed` all already receive it|

So in any of your five Notifuse templates, you can drop in:

```
{{ invoice_url }}
```

as a button or plain link — e.g. “View & Pay Invoice” pointing at `{{ invoice_url }}`.

A couple of things worth knowing about that link:

- **It’s the same URL for the life of the invoice** — the deposit and balance payment stages both use this one link; Square automatically shows whichever payment is currently due when the client opens it (this is the same behavior you tested manually in sandbox).
- **It’s unauthenticated by design** — anyone with the link can view and pay the invoice, which is exactly what makes it “shareable,” but also means you shouldn’t put it anywhere public (it’s fine in a 1:1 email, which is all this integration does).
- **The `invoice-confirmation` template** — since the invoice is already paid by the time that email sends, `{{ invoice_url }}` there is mostly useful as a “view your paid invoice / receipt” link rather than a payment prompt. If you’d rather that one _not_ include the link (e.g. no action needed once paid), just omit `{{ invoice_url }}` from that template — the data field will still be sent, Notifuse just won’t render it if you don’t reference it.

If instead you wanted a link into your **own branded booking/client portal** rather than Square’s hosted page, that’d need a different data source — let me know if that’s actually what you’re after and I can adjust `extractInvoiceFields` to build that URL instead.

what liquid elements can I add to my templates

Here’s exactly what’s available per template — these are pulled straight from the `data` object each `sendNotifuseEmail` call sends, so they’re guaranteed to match what your middleware actually delivers:

### `invoice-sent`

```
{{ customer_name }}   {{ invoice_number }}   {{ amount }}
{{ due_date }}        {{ service_date }}     {{ invoice_url }}
```

### `deposit-received`

```
{{ customer_name }}     {{ invoice_number }}    {{ deposit_amount }}
{{ remaining_balance }} {{ balance_due_date }}  {{ service_date }}
{{ invoice_url }}
```

### `invoice-confirmation`

```
{{ customer_name }}   {{ invoice_number }}   {{ amount_paid }}
{{ service_date }}    {{ invoice_url }}
```

### `invoice-reminder`

```
{{ customer_name }}   {{ invoice_number }}   {{ amount }}
{{ due_date }}         {{ service_date }}     {{ invoice_url }}
```

### `payment-failed`

```
{{ customer_name }}   {{ invoice_number }}   {{ amount }}
{{ service_date }}    {{ invoice_url }}
```

**Notes on the values themselves:**

- `amount`, `deposit_amount`, `remaining_balance`, `amount_paid` all arrive already formatted (e.g. `$150.00`) — don’t run them through a currency filter.
- `due_date`, `balance_due_date`, `service_date` arrive as plain `YYYY-MM-DD` strings from Square. Liquid’s `date` filter works on these if you want nicer formatting, e.g.:

```
  {{ service_date | date: "%B %d, %Y" }}
```

→ “September 10, 2026”

- Any of these can be `null`/missing (e.g. `service_date` if you left it blank on the invoice, `balance_due_date` on a non-split invoice) — wrap optional ones in a conditional so the email doesn’t render an awkward blank:

```
  {% if service_date %}
    Your service is scheduled for {{ service_date | date: "%B %d, %Y" }}.
  {% endif %}
```

**What’s _not_ available** unless we add it: line-item details, tax breakdown, your business name/logo (those should just be static in the template design, not variables), or the client’s phone number — none of that is currently extracted from the Square payload. Let me know if you want any of those piped through and I’ll add them to `extractInvoiceFields`.