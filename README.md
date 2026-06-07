# Butlin's Bognor Regis Holiday Planner

A personalised, sensory-friendly holiday planner for **Rob, Becky & Rosie** — Butlin's Bognor Regis, 15–19 June 2026.

Installable web app that works fully offline. Built as a single self-contained page plus a service worker, so once it's loaded on your phone it works with no signal — perfect for wandering a 60-acre resort.

---

## What it does

- **Plan** — a week-at-a-glance grid pinned to the top of every screen, plus a tap-to-expand day timeline with walking times, nap protection and a live "now / next" panel while you're on resort
- **Build** — pick activities from scenarios or individually, with sensory ratings, clash detection and automatic day-balancing so no day gets overloaded
- **Book** — booking priority list, token tier calculator and a running budget
- **Guide** — sensory toolkit for Rosie, resort map, weather, an "if she gets overwhelmed" plan and interactive packing/prep checklists

Everything you select is saved to your device automatically and survives closing the browser.

---

## Deploy to GitHub Pages — step by step

You've done this before with the World Cup app, so this'll be quick. Easiest route is the **web interface** (no command line needed).

### Option A — GitHub website (easiest)

**1. Create a new repository**
- Go to [github.com/new](https://github.com/new)
- Repository name: `butlins` (or anything — this becomes part of the URL)
- Set it to **Public**
- Don't tick "Add a README" (you already have one)
- Click **Create repository**

**2. Upload the files**
- On the new empty repo page, click **uploading an existing file**
- Drag in **all** of these files together:
  - `index.html`
  - `manifest.json`
  - `sw.js`
  - `icon-192.png`
  - `icon-512.png`
  - `apple-touch-icon.png`
  - `favicon.png`
  - `README.md`
- Scroll down, click **Commit changes**

**3. Turn on GitHub Pages**
- In the repo, click **Settings** (top right)
- Left sidebar → **Pages**
- Under "Build and deployment" → Source: **Deploy from a branch**
- Branch: **main**, folder: **/ (root)**
- Click **Save**

**4. Wait ~1 minute, then visit your site**
- Your URL will be: `https://YOUR-USERNAME.github.io/butlins/`
- (For you that's likely `https://roblor-boop.github.io/butlins/`)
- The first deploy can take 1–2 minutes. Refresh if it 404s at first.

Done. That's the live site.

---

### Option B — Command line (if you prefer Git)

```bash
# In the folder containing the files
git init
git add .
git commit -m "Butlin's holiday planner"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/butlins.git
git push -u origin main
```

Then do **step 3** above (Settings → Pages) to enable hosting.

---

## Install it on your phone (so it works like an app)

Once the site is live, open the URL on your phone:

**iPhone (Safari)**
1. Tap the **Share** button (square with arrow)
2. Scroll down → **Add to Home Screen**
3. Tap **Add**

**Android (Chrome)**
1. You'll see an **"Install app"** button appear bottom-right — tap it
2. Or: tap the **⋮** menu → **Install app** / **Add to Home screen**

It'll appear on your home screen with the seaside icon, open full-screen with no browser bars, and **work completely offline**. Becky can install it too from the same link.

---

## Updating the plan later

If show times change when booking opens (~18 May), or you want to tweak anything:

**Via the website:**
1. Go to your repo → click `index.html`
2. Click the **pencil icon** (Edit)
3. Make your change → **Commit changes**
4. The live site updates in ~1 minute

**Force the app to refresh on your phone:** the service worker caches the old version, so after an update, close the app fully and reopen it. If it's stubborn, remove it from your home screen and re-add it.

> **Tip:** if you change `index.html`, also bump the cache version in `sw.js` — change `butlins-planner-v1` to `v2`. This tells phones to fetch the fresh version instead of the cached one.

---

## Sharing with Becky

- **Easiest:** just send her the URL. She opens it and adds it to her home screen.
- **In-app:** the **Share** button (top right of the app) copies the full plan as plain text to paste into WhatsApp or Notes.

---

## Files

| File | What it is |
|------|-----------|
| `index.html` | The entire app — HTML, CSS and JavaScript in one file |
| `manifest.json` | Makes it installable (app name, icon, colours) |
| `sw.js` | Service worker — caches the app for offline use |
| `icon-192.png` / `icon-512.png` | App icons (home screen, app switcher) |
| `apple-touch-icon.png` | iPhone home-screen icon |
| `favicon.png` | Browser tab icon |

No build step, no dependencies, no tracking. Pure static site.

---

## Before booking day (~18 May)

The activity times come from the Butlin's app screenshots and standard Bognor Regis scheduling. **Cross-check the live app when booking opens** — especially Peppa (Wed 11:00) and Jack (Thu 16:00). If a time has moved, update it in the **Build** tab and re-commit `index.html`.

**Booking priority:** Quiet Hour Soft Play (Tue 08:00) first — it fills fastest. Then Peppa, Jack, Mini Bow, Tots Football, Balanceability, Pottery. 4 tokens = £28.40 pre-arrival. Book the bowling lane on arrival Monday.
