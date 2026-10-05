# Jennylicious PWA V0.15.3 – Cross-Platform UI Fix

Built directly on the successfully tested V0.15.2 Clean Production Baseline.

Changes:
- Normalizes button/input/select/textarea typography and inherited text color.
- Removes native iOS Safari button appearance where it caused blue text/icons.
- Explicitly keeps `menurow` and recipe/category `tile` text dark on iOS and Android.
- Anchors inherit Jennylicious component colors rather than Safari's native blue.
- Bottom navigation keeps its intentional Jennylicious component colors.

Data behavior:
- NO database reset was added.
- NO IndexedDB schema or persistence logic was changed.
- The one-time V0.15.2 production-baseline marker remains unchanged.
- Existing local categories, recipes and images remain local and should survive this update.

Test on Android + iPhone:
1. Open Mehr: menu labels/icons should no longer be iOS blue.
2. Open Start: category-card title should no longer be iOS blue.
3. Check bottom navigation: selected item remains purple.
4. Create/reopen a test category if desired to confirm persistence is unchanged.
