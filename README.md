# AM GAMING — website

A **static** multi-game site (studio landing page + one page per game + a privacy
policy per game). No build step, no backend — just HTML/CSS. Perfect for Vercel.

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
