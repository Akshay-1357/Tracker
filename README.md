# Fit — Fitness Journal

A minimal, mobile-first web app for tracking a lean bulk: gym workouts, nutrition, body measurements, and running. Built to be opened, updated in under two minutes, and closed.

## Features

- **Today** — today's weight, workout status, calorie/protein/water/sleep progress, and a 7-day weight trend, with one-tap quick-add buttons.
- **Workout** — six-day push/pull/legs split (Push A/B, Pull A/B, Legs A/B). Each exercise shows your previous performance, personal best, and a suggested next target. Sets log with steppers, "repeat last set," and one-tap add.
- **Progress** — body tab (weight chart, 7-day average, measurements) and strength tab (progression charts for nine tracked lifts).
- **Nutrition** — daily calories, protein, water, fiber, and sleep against your targets.
- **Running** — distance, time, pace (auto-calculated), walk breaks, difficulty, and notes, with a distance trend chart.
- **Monthly check-in** — every four weeks, log weight, measurements, three progress photos, biggest improvement, weakest area, and next month's goal.
- **Editable workout plans** — add or remove exercises from any day, and choose which day(s) a new exercise belongs to.
- **Dark mode** — system, light, or dark, toggle in the top bar.
- **Works offline, installs like an app** — PWA with a service worker and home screen icon.

## Data storage

All data is stored locally on your device using **IndexedDB** — nothing is sent to a server, and no account or login is required. Data does **not** sync across devices; if you use the app on two phones, they'll have independent data. Use **More → Settings → Export data** periodically to download a JSON backup.

## Running it locally

Just open `index.html` in a browser. No build step, no dependencies to install.

For the offline/installable features (service worker, "Add to Home Screen") to work properly, the app needs to be served over HTTP(S) rather than opened directly as a file — see deployment below.

## Deploying (free)

**Netlify Drop** (easiest):
1. Go to [app.netlify.com/drop](https://app.netlify.com/drop).
2. Drag this whole folder onto the page.
3. You'll get a live HTTPS URL immediately — no account required to try it, but create a free account if you want the URL to stay stable so you can redeploy updates later.

**Alternatives:** GitHub Pages or Vercel work the same way — upload this folder and point the host at `index.html`.

## Installing on your phone

1. Open your deployed URL in Safari (iOS) or Chrome (Android).
2. **iOS:** tap Share → Add to Home Screen.
3. **Android:** tap the menu (⋮) → Add to Home screen / Install app.
4. The app opens full-screen with its own icon, no browser bar.

If you redeploy an update, remove the home screen icon and re-add it to pick up any icon or name changes (the OS caches those at install time).

## File structure

```
index.html      the entire app — markup, styles, and logic
manifest.json   PWA metadata (name, icons, theme color)
sw.js           service worker for offline caching
icon-192.png    home screen icon (small)
icon-512.png    home screen icon (large)
```

## Customizing

- **Daily targets** (calories, protein, water): More → Settings.
- **Workout plans**: More → Exercise plans, or add exercises on the fly from the Workout tab.
- **Tracked lifts on the Strength chart**: edit the `STRENGTH_EXERCISES` array near the top of the `<script>` in `index.html`.
- **Colors**: edit the CSS custom properties (`--bg`, `--accent`, etc.) at the top of `index.html`.
