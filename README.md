# Bountiful Properties Realtor Network

A broker platform where realtors around the world sell properties, ongoing builds and land by **Bountiful Properties**, earn commission automatically at closing, and build a referral team.

## Commission model

Each closed sale pays a 10% commission pool, split as follows.

| Who | Share of sale price |
|---|---|
| Realtor who sells | 6% |
| Their upline (who invited them) | 1% |
| Bountiful Properties (agency) | 3% |

A realtor earns 7% in total when they sell and also have an upline. If a realtor has no upline, the 1% goes to the agency.

## Features

- Landing page with a live commission calculator
- Realtor signup with referral code and upline name
- Personal referral link (`#ref-CODE`)
- Dashboard with listings, earnings ledger and network
- Auto-generated commission agreement (name, upline, Bountiful Properties), saved as PDF from the print dialog
- Sidebar and account dropdown with profile and settings
- Sky blue and white theme with automatic dark mode

## Run locally

Open `index.html` in a browser, or run `python3 -m http.server` and visit http://localhost:8000.

## Deploy with GitHub Pages

1. Push this repo to GitHub on the `main` branch.
2. Go to **Settings > Pages** and set **Source** to **GitHub Actions**.
3. The workflow in `.github/workflows/pages.yml` publishes the site on every push.

## Structure

```
index.html            (the whole app: HTML, CSS and JavaScript in one file)
.github/workflows/pages.yml
```

## Status

Front-end prototype. Data is kept in the browser's `localStorage`. Next steps: a real backend (database, login, upline lookup, automatic payouts) and server-side PDF generation.
