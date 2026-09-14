# Jungle Hunt — website release notes for the owner

This file is excluded from Vercel by the existing `_templates` rule.

The public pages use the site's existing AM-Games name and support email. A
Google Play URL and public website domain were not supplied; no download CTA,
fabricated review score, install count, rating, age group or price is shown.

## Privacy basis and remaining verification

Source project: `F:/games/My project`, Unity 6000.5.5f1.

## Current website content and images

- Verified against CampaignBuilder/CampaignTuning: 200 chapters, 10 per region,
  20 named night regions, 20–80% difficulty, up to four waves and 600 stars.
- ArrowCatalog supplies all four arrow abilities, the 20% Ember Fang speed bonus
  and coin prices for 2/5/10/15 packs. Workshop data comes from SaveSystem and
  GameManager: three ranks per item, 90/180/270 coins, +6 base damage, +20 maximum
  health or -0.06 seconds reload per rank. HealthDiamondDrops restores up to 20 HP.
- Normal eye hits use the combat damage multiplier; the website promises extra
  damage, not a guaranteed instant defeat at every draw strength or enemy HP.
- Cloud-save, privacy, contact and deletion instructions now use the top-right
  Camp user icon beside Settings, matching CloudSaveScreen.cs. Disconnect and
  deleting the cloud account are explained separately from clearing device data.
- The new 512×512 icon and 1794×877 feature source are copied unchanged into
  website assets. Current Journey, splash and loading images are genuine Unity
  UI renders; four older combat captures are labeled as development-build images.
  Old menu captures showing a 20-chapter campaign are no longer in the gallery.
- Source/content and browser checks are saved under
  `F:/games/My project/Artifacts/Jungle-Hunt-Website-Update/`.

- SaveSystem.cs stores progress, coins, inventory, upgrades and settings locally.
- Optional Google sign-in, Firebase Authentication, Firestore cloud saves,
  Analytics and Crashlytics were integrated on September 14, 2026. AdMob 11.5.0
  now shows an interstitial after won/lost attempts, with no reward. Test IDs are
  configured. No chat or real-money billing was added. Google Play Games is not used.
- The Firebase UID scopes cloud progress. Google/Firebase handle basic profile
  and account data; Analytics and Crashlytics handle gameplay/technical data.
  Android advertising-ID collection is disabled. The privacy and deletion pages
  now describe account backup, disconnect and in-app deletion.
- UnityConnectSettings.asset enables `InsightsSettings.m_EngineDiagnosticsEnabled`.
  The project is cloud-connected. The SDK/runtime and Dashboard settings for the
  exact uploaded build still need verification, so the privacy page discloses
  possible technical transmission and does not claim “no data collected.”
- Unity describes essential diagnostic collection when this setting is enabled:
  [Collection settings](https://docs.unity.com/en-us/cloud/developer-data/collection-settings).
  Provider handling and privacy choices:
  [Unity Game Player and App User Privacy Policy](https://unity.com/legal/game-player-and-app-user-privacy-policy).
- Check enabled Unity services, additional-data settings, data usage, actual
  network behavior and retention before finalizing the release's Data safety
  answers. Update the website text if the build configuration changes.
- Review the support-retention and privacy-request wording against the studio's
  actual practices. No fixed child age group or regulatory rating was invented.
- The game needs a visible link or policy text in its own Settings. A signed
  Jungle Hunt 1.0 AAB now exists and its package, signature and bundle checks pass.
  Its standard AD_ID permission is absent, but Android advertising-service
  permissions remain; do not equate that with no SDK identifiers or data collection.
  Android device tests and remote console settings remain separate release checks.
- The privacy/deletion content was updated from the current code and public
  provider documentation. It describes automatic telemetry for guests, test-ad
  behavior, Gmail support, active account deletion, provider cleanup and local data.
  No fixed email-deletion deadline or Analytics retention setting was assumed.
  Browser evidence is under `F:/games/My project/Artifacts/Privacy-Update/`.

## Deployment

Deploy the existing static site normally when ready. Intended clean paths are
`/games/jungle-hunt`, `/privacy/jungle-hunt` and `/jungle-hunt-data-deletion`.
The existing `/data-deletion#jungle-hunt` route carries the same instructions.
After a real domain is known, use the resulting absolute URLs for Play Console
and the game's policy entry. No publishing action was performed by this task.
