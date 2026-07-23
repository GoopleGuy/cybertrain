# CyberTrain — Night City Strength OS

Personal workout tracker PWA. Double-progression engine, per-exercise tuning,
rest timers, haptics, offline-first.

## One-time setup

1. Create a GitHub repo (e.g. `cybertrain`) and upload everything in this folder,
   keeping the structure (including `.github/workflows/deploy.yml`).
2. Repo **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. Wait ~1 min for the Action to finish (green check in the Actions tab).
4. App URL: `https://<your-username>.github.io/<repo-name>/`
5. On your phone: open that URL in Chrome → ⋮ menu → **Add to Home screen → Install**.

## Iterating

`CyberTrain.jsx` at the repo root is the single source of truth — the entire app
in one file. To change anything:

1. Give the file (or its raw GitHub URL) to Claude and describe the change.
2. Take the updated `CyberTrain.jsx` back.
3. On GitHub: open `CyberTrain.jsx` → ✏️ Edit → select-all, paste, **Commit**.
4. The Action rebuilds and deploys automatically (~1 min). The service worker
   cache version is stamped with the commit SHA, so no manual cache-busting.
5. On your phone: open the app (it fetches the update in the background),
   close it, open it again — you're on the new version.

## Your data is safe across updates

Workout logs live in your phone's localStorage, keyed to the site URL — they are
NOT part of the deploy, so updates never touch them. They would only be lost if
you uninstall the PWA, clear Chrome's site data, or change the repo/username
(which changes the URL). Before any big experiment: **DATA tab → ⇪ EXPORT
BACKUP**, paste into your notes app. Restore anywhere with ⇩ IMPORT.

## Local build (optional)

```
npm install esbuild react react-dom
node build.mjs
npx serve dist   # or any static server
```
