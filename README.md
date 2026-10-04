# Jennylicious PWA V0.14.0 – Structured IndexedDB

V0.14.0 migrates the working V0.13.1 `core/state` snapshot into separate stores:
`recipes`, `images`, `categories`, `settings`, `weeklyPlan`, `shopping`, `cookHistory`, `meta`.

The legacy `core` store is deliberately retained for rollback safety.

Recipe and custom category images that exist as Data URLs are resized to max. 1280 px, converted to WebP (quality 0.78), and stored separately as Blob records in `images`.

For this build, recipes/categories/settings are connected to the new stores. Weekly plan, shopping and cook history stores exist but will be connected in the next migration step.

Test after deployment:
1. Verify a recipe created in V0.13.1 is still present.
2. Create a new recipe with a new image.
3. Fully close and reopen Jennylicious.
4. Verify both recipe and image remain.
