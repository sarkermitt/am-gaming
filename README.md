# AM GAMING — website

A **static** multi-game site (studio landing page + one page per game + a privacy
policy per game). No build step, no backend — just HTML/CSS. Perfect for Vercel.

## Jungle Hunt added — September 14, 2026

- `/games/jungle-hunt` — complete game page: description, 20 chapters, 54 creatures,
  four arrow types, eight actual game screenshots, controls, progression, Android
  requirements, settings, FAQ and studio support.
- `/privacy/jungle-hunt` — game-specific privacy text covering local saves,
  support correspondence and Unity runtime diagnostics.
- `/data-deletion#jungle-hunt` — local data clearing and privacy-request instructions.
- The homepage and Contact page link to Jungle Hunt alongside Math Puzzle IQ.

Jungle Hunt uses the existing **AM GAMING** identity and
**sarkermit.play@gmail.com** support contact. Its Google Play URL has not been
provided or verified, so the game page currently links to gameplay and controls
without an install button or an unverified store-availability claim. Add the real
store link to its hero CTA when available.

Artwork comes from `F:/games/My project/Play console assets/06-source-art/`.
The icon and feature illustration retain their original 1254×1254 and 1794×876
PNG bytes; these website sources are not exact-size Play Console exports.
Eight 1920×1080 screenshots are under `assets/img/jungle-hunt/`, loaded lazily.
They depict the actual shared game in Unity Editor Play Mode. No generated fake
gameplay images or external image/font dependencies were added.

Before publishing the Jungle Hunt privacy policy or using its URL in Play Console,
review the actual release and Unity Dashboard data settings. The current Unity
project enables runtime diagnostics; a disabled Analytics package alone does not
prove that no data is collected. See `_templates/jungle-hunt-release-review.md`.
The page does not copy Math Puzzle IQ's Firebase, Ads or real-money billing claims.

Local browser verification covers the five affected routes at 320, 390, 768 and
1440 pixels, image loading, local links and anchors, FAQ keyboard behavior and the
homepage card. Evidence is stored at
`F:/games/My project/Artifacts/Jungle-Hunt-Website/`. No Git push or deployment was
performed for this addition. The user's existing Math Puzzle IQ store-link edit
was preserved.

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
The studio name **"AM GAMING"**, the 🎮 logo, and the contact email
`sarkermit.play@gmail.com` appear across the pages — search & replace to change them.
Colors live at the top of `assets/css/style.css` (`:root` variables).

## Note on the privacy policy
`privacy/math-puzzle-iq.html` describes the data Math Puzzle IQ actually uses
(Firebase Auth/Analytics/Firestore, AdMob, Google Play Billing, a device id for the
"Remove Ads" subscription). Review it and adjust the developer/legal name before you
rely on it for a real store submission.
