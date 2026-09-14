# Jungle Hunt — website release notes for the owner

This file is excluded from Vercel by the existing `_templates` rule.

The public pages use the site's existing AM GAMING name and support email. A
Google Play URL and public website domain were not supplied; no download CTA,
fabricated review score, install count, rating, age group or price is shown.

## Privacy basis and remaining verification

Source project: `F:/games/My project`, Unity 6000.5.5f1.

- SaveSystem.cs stores progress, coins, inventory, upgrades and settings locally.
- No accounts, cloud-save service, ads, chat or real-money billing integration is
  present in the game code or package manifest.
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
- The game needs a visible link or policy text in its own Settings before using
  this as its final in-app/Play privacy information. This website task does not
  change or rebuild the Unity app.

## Deployment

Deploy the existing static site normally when ready. Intended clean paths are
`/games/jungle-hunt`, `/privacy/jungle-hunt` and `/data-deletion#jungle-hunt`.
After a real domain is known, use the resulting absolute URLs for Play Console
and the game's policy entry. No publishing action was performed by this task.
