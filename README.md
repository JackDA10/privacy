# Privacy policy & support pages

Static pages backing the **Privacy Policy URL** and **Support URL** fields for the iOS
apps. No build step, no dependencies — plain HTML and one stylesheet, so an App Review
browser on a bad connection renders them instantly.

Served by GitHub Pages from the repository root.

## URLs

| Page | URL |
|---|---|
| Shared policy | `https://jackda10.github.io/privacy/` |
| Racetrack: IFR Hold Trainer | `https://jackda10.github.io/privacy/racetrack/` |
| Pitot-Static | `https://jackda10.github.io/privacy/pitot-static/` |
| Airspace Trainer | `https://jackda10.github.io/privacy/airspace-trainer/` |
| Partial Panel Trainer | `https://jackda10.github.io/privacy/partial-panel/` |
| IFR Clearance Trainer | `https://jackda10.github.io/privacy/ifr-clearance/` |
| VOR & HSI Trainer | `https://jackda10.github.io/privacy/vor-hsi/` |
| Top of Descent Calculator | `https://jackda10.github.io/privacy/top-of-descent/` |
| Constant Speed Prop Trainer | `https://jackda10.github.io/privacy/constant-speed/` |
| AutoPilot | `https://jackda10.github.io/privacy/autopilot/` |

Use the **per-app** URL in App Store Connect, for both the Privacy Policy and Support
fields — not the shared one. Every app gets its own page from day one even when the text
is identical, because changing a privacy URL on a live app costs a metadata update and
another review pass.

## Adding an app

1. `cp TEMPLATE.html <app-slug>/index.html`
2. Replace `APP NAME` and `DATE`.
3. Correct the "What this app stores" section to what that app actually persists — find
   the real `UserDefaults` keys, and confirm whether the app has a control that clears
   them. Not every app does: Partial Panel has none, and Racetrack stores only its best
   Entry Trainer streak and two rating-request values, with no clearing control, which is
   why the shared policy says *most* apps rather than *every* app.
4. If the app opens any URL — a citation chip, the *More from AutoPilot* screen — give it
   a "Links out of the app" section. The flat "no network requests" bullet alone
   misdescribes what the user watches happen.
5. Add it to the app list in `index.html` and to the URL table above.
6. Point that app's two URL fields at `https://jackda10.github.io/privacy/<app-slug>/`.

## The one rule

**This page and the App Privacy answers in App Store Connect have to agree.** Review
checks them against each other, and a mismatch is a rejection. Today every study app
answers "Data Not Collected" across the board, which is true — there is no networking
code in any of them. AutoPilot is the exception: a connected service, so its page is a
complete standalone policy matching its three declared data types (email address, user
ID, user content — all app functionality, no tracking) — see `autopilot/index.html`'s
header comment for the documents that must stay in sync.

If an app ever gains analytics, sync, or an account, that is not a small edit: update
that app's page, update the shared policy, and change the App Privacy answers in the
same submission.

## Setup

Settings → Pages → Source: *Deploy from a branch* → `main` / `/ (root)`. The `.nojekyll`
file disables Jekyll processing so files are served exactly as committed.
