# Bountiful Properties Realtor Network

A broker platform where realtors around the world sell properties, ongoing builds and land by **Bountiful Properties**, earn commission at closing, and build a referral team.

Backend: **Firebase** (Authentication + Firestore) on the free Spark plan. No card needed, and no server to run.

## Commission model

Each confirmed sale pays a 10% pool: **6%** to the selling realtor, **1%** to their upline, **3%** to the agency. With no upline, the agency keeps the 1%. `firestore.rules` rejects any confirmation whose amounts do not match these rates.

## Files

| File | Purpose |
|---|---|
| `index.html` | Realtor app: signup/login, referral link, listings, submit closings, earnings, team, profile, **PDF agreement download** |
| `admin.html` | Admin dashboard: stats, confirm/reject closings, mark paid, manage listings, realtors list, CSV export |
| `firestore.rules` | Security rules for the database |
| `.github/workflows/pages.yml` | Publishes the site to GitHub Pages |

## Setup (about 10 minutes)

1. Go to https://console.firebase.google.com and **Add project** (stay on the free Spark plan).
2. **Build > Authentication > Get started**, then enable **Email/Password**.
3. **Build > Firestore Database > Create database** (production mode, any region). Open the **Rules** tab, paste the contents of `firestore.rules`, and **Publish**.
4. **Project settings (gear) > Your apps > Web (`</>`)**, register an app, and copy the config values.
5. Paste them into the `FB` block at the top of the script in **both** `index.html` and `admin.html`.
6. Push to GitHub, set **Settings > Pages > Source** to **GitHub Actions**. Then add `YOURNAME.github.io` under Firebase **Authentication > Settings > Authorized domains**.
7. Open the site, sign up, then copy your **User UID** from Firebase **Authentication > Users**.
8. In Firestore, **Start collection** named `admins`, with **Document ID = your UID** and any field (for example `role` = `admin`). Now `admin.html` will let you in.
9. In `admin.html > Listings`, tap **Load 6 sample listings** or add your own.

## How a sale flows

1. A realtor submits a closing on a listing (`pending`).
2. An admin confirms it in `admin.html` (the final price can be adjusted) and the 6/1/3 amounts are recorded.
3. After paying out, the admin marks it `paid`.

## Free plan limits

Spark allows roughly 50,000 reads and 20,000 writes per day, plenty for a launch. Heavy use needs the paid Blaze plan.
