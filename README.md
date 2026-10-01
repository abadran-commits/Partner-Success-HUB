# Partner Success Hub

Internal leadership platform for the WalaPlus Partner Success team — KPI management,
revenue pipeline tracking, special promo logging, and merchant portfolio intelligence.

The whole application is a single self-contained file, `index.html`. It needs no build
step and no server-side dependencies: React, ReactDOM, and Babel load from a CDN and the
app compiles in the browser.

## Modules

| Module | What it does |
|---|---|
| **KPI Management** | 13 tracked KPIs with baseline/target/current, QTD pace and gap, and status. Click any KPI row to open its detail view. |
| **Revenue Pipeline** | Full opportunity tracker — quotation, invoice, and payment stages, linked to real merchant records. |
| **Special Promos** | Offer pipeline logged per Account Manager: ongoing vs. special offer, campaign tagging, competitive read, tier and type. |
| **Tier A Dashboard** | Performance segmentation across the Tier A merchant cohort. |
| **Overall Dashboard** | Full portfolio view across every tier. |
| **AM Operations Hub** | Daily workspace — offers, renewals, marketing, meetings, and relationship health. |
| **Teams / Merchants** | Team directory and the complete merchant record set. |

## KPI detail view

Clicking a KPI opens a detail modal containing:

- **Performance Trend** — quarterly actuals plotted against the annual target
- **Quarterly Tracking** — editable target and actual per quarter, with closed quarters
  locked behind a padlock that can be reopened
- **Lock history** — every lock and unlock, with who did it
- **Recent changes** — every target/actual edit, showing previous value, new value, and
  who made the change

## Running it

Open `index.html` in a browser, or serve the folder over HTTP:

```bash
python -m http.server 8791
```

Then visit `http://localhost:8791`.

## Hosting it on Replit

The repo carries `.replit` and `replit.nix`, so Replit can run it with no setup.

**Import it (do not copy the file by hand — `index.html` is 1.6 MB):**

1. In Replit: **Create Repl → Import from GitHub**
2. Paste `https://github.com/abadran-commits/Partner-Success-HUB`
3. Press **Run** — the webview serves the app on port 8000
4. Press **Deploy → Static** for a permanent URL that stays up when the Repl sleeps

Two things must be done for a new domain, or sign-in will not work:

**1. Register the Replit URL with Google.** The Google sign-in button only works on
origins listed in the Google Cloud Console. Open the OAuth client
(`3366206189-…apps.googleusercontent.com`) → **Authorized JavaScript origins** → add the
Replit URL exactly, with no trailing slash, for example:

```
https://partner-success-hub.<your-replit-username>.repl.co
```

Until that is added, Google sign-in fails on Replit while continuing to work on GitHub
Pages. Add the deployment URL too if it differs from the dev URL.

**2. Decide who can reach it.** The email/password box on the sign-in screen accepts
**any password** — it is a demo shortcut, not authentication, and there is no backend to
check anything against. A public Replit URL therefore means anyone with the link is in.
To actually restrict access, either make the Repl private, or remove the password
shortcut so Google (which is domain-locked to `@walaplus.com`) is the only way in.

## Data and persistence

Edits made in the UI — promo rows, pipeline rows, KPI targets and actuals, the change log
— are held in browser memory for the session only. There is no backend yet, so a page
refresh resets them. Wiring this to a real datastore is the next step if the team wants
edits to persist and to be shared between users.
