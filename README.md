# AM-Games — website

A **static** multi-game site (studio landing page + one page per game + a privacy
policy per game). No build step, no backend — just HTML/CSS. Perfect for Vercel.

## Jungle Hunt updated — September 14, 2026

- `/games/jungle-hunt` — description, all 20 regions and their 200 chapters,
  20–80% difficulty, 600 stars, 54 creatures, four arrow types, coin pack prices,
  Workshop ranks, controls, health diamonds, optional Google cloud saves, ads,
  Android requirements, settings, FAQ and studio support.
- `/privacy/jungle-hunt` — local saves, Google/Firebase account and cloud data,
  Analytics, Crashlytics, AdMob, support correspondence and Unity diagnostics.
- `/data-deletion#jungle-hunt` — cloud-account deletion through the top-right
  Camp user icon, local data clearing and email requests when the app is inaccessible.
- The homepage and Contact page link to Jungle Hunt alongside Math Puzzle IQ.

Jungle Hunt uses the existing **AM-Games** identity and
**sarkermit.apps@gmail.com** support contact. Its Google Play URL has not been
provided or verified, so the game page currently links to gameplay and controls
without an install button or an unverified store-availability claim. Add the real
store link to its hero CTA when available.

The icon is the verified `01-app-icon/app-icon-512x512.png` from the game's
Play Console assets folder. The banner is the latest
`02-feature-graphic/jungle-hunt-feature-source-v2.png` (1794×877). These files are
copied byte-for-byte; the website banner does not require a 1024×500 export.
Four existing gameplay captures are shown with a development-build note. The
old 20-chapter menu images have been replaced in the gallery by the current
932×430 Journey render from `Artifacts/Campaign-200`. The new splash and live
loading UI renders come from `Artifacts/Branding/Launch-Implementation` (1672×941).
All seven gallery images load lazily. No generated fake gameplay or external
image/font dependencies were added. Unused older captures remain on disk.

Before publishing the Jungle Hunt privacy policy or using its URL in Play Console,
review the actual release and Unity Dashboard data settings. The current Unity
project enables runtime diagnostics; a disabled Analytics package alone does not
prove that no data is collected. See `_templates/jungle-hunt-release-review.md`.
The pages describe Jungle Hunt's own optional Google/Firebase and AdMob code.
AdMob still uses test IDs; production ad serving and signed-device cloud backup
need verification before release. Special arrows and upgrades use game coins;
there is no Jungle Hunt real-money billing integration.

Local browser verification covers the five affected routes at 320, 390, 768 and
1440 pixels, image loading, local links and anchors, FAQ keyboard behavior and the
homepage card. Evidence is stored at
`F:/games/My project/Artifacts/Jungle-Hunt-Website-Update/`. No Git push or deployment
was performed for this update. The existing Math Puzzle IQ game/privacy pages
and store links were preserved.

```
website/
├─ index.html                      ← homepage (studio + games grid)
├─ games/
│  └─ math-puzzle-iq.html          ← one page per game
├─ privacy/
│  └─ math-puzzle-iq.html          ← one privacy policy per game (Play requires this)
├─ assets/
│  ├─ css/style.css                ← shared styles
│  └─ img/                         ← <slug>-icon.png (512) and <slug>-feature.png (1024×500)
├─ _templates/                     ← copy these to add a new game (not deployed)
├─ vercel.json                     ← clean URLs
└─ .vercelignore
```

## Deploy to Vercel (easy)

**Option A — drag & drop (fastest):** go to [vercel.com/new](https://vercel.com/new),
drag the **`website`** folder onto the page. Done.

**Option B — Vercel CLI:**
```
npm i -g vercel
cd D:\AllApps\MathWorld\website
vercel          # preview
vercel --prod   # go live
```

**Option C — Git (auto-deploys on push):** import the repo in Vercel and set
**Root Directory = `website`**. Framework preset: **Other**. Build command: *(none)*.
Output directory: *(leave empty / `.`)*.

> The one thing that matters: the site's root must be the **`website`** folder, so
> paths like `/assets/css/style.css` resolve. Options A/B do this automatically;
> for Git (Option C) set the Root Directory to `website`.

After deploy you get a URL like `https://your-project.vercel.app`. Add a custom
domain later in Vercel → Settings → Domains if you want.

## Use these URLs in Google Play Console

Once live, in each app's Play Console listing:
- **Privacy policy** → `https://YOUR-DOMAIN/privacy/math-puzzle-iq`
- **Website** (optional, Store listing → Contact details) → `https://YOUR-DOMAIN/games/math-puzzle-iq`

(Clean URLs are on, so no `.html` needed.)

## Add a new game (3 steps)

1. **Images** → drop into `assets/img/`:
   - `assets/img/<slug>-icon.png` (512×512)
   - `assets/img/<slug>-feature.png` (1024×500)
2. **Pages** → copy the templates and replace the `{{PLACEHOLDERS}}`:
   - `_templates/game-template.html` → `games/<slug>.html`
   - `_templates/privacy-template.html` → `privacy/<slug>.html`
   - In the privacy page, keep only the data-collection lines that actually apply to that game.
3. **Homepage card** → in `index.html`, copy the `<!-- GAME CARD -->` block and point it
   at `/games/<slug>` with the new icon, name and tags.

Redeploy (push to Git, or re-run `vercel --prod`).

## Editing the studio brand
The studio name **"AM-Games"**, the 🎮 logo, and the contact email
`sarkermit.apps@gmail.com` appear across the pages — search & replace to change them.
Colors live at the top of `assets/css/style.css` (`:root` variables).

## Note on the privacy policy
`privacy/math-puzzle-iq.html` describes the data Math Puzzle IQ actually uses
(Firebase Auth/Analytics/Firestore, AdMob, Google Play Billing, a device id for the
"Remove Ads" subscription). Review it and adjust the developer/legal name before you
rely on it for a real store submission.
