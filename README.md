# Jennylicious PWA V0.19.0 – Data Safety

Current app version: V0.19.0

Base: V0.18.4 Image & History Fix.


## V0.19.0 – Data Safety
- Normal saves no longer clear and rebuild the complete `recipes` store. Existing recipe records are only upserted.
- A normal autosave is not allowed to reduce the last known recipe-ID set. Unexpected empty or partial in-memory recipe lists are blocked from overwriting the stored recipe inventory.
- Recipe deletion is the only normal path allowed to reduce the recipe set and is persisted explicitly in a dedicated transaction.
- Recipe writes are serialized to prevent overlapping autosaves from racing each other.
- Startup restore is completed before writes are enabled. If restore fails, automatic writes stay disabled for that session instead of writing defaults over local data.
- The old V0.15.2 production-baseline marker remains, but its reset routine is now permanently non-destructive. A missing marker never clears user data.
- `visibilitychange` and `pagehide` only flush through the same guarded save path; they can no longer clear the recipe store.
- A `lastKnownGoodRecipes` snapshot and recipe safety state are maintained in the existing `meta` store. Missing expected recipes are automatically reconstructed from the last known good snapshot when possible.
- Up to 7 daily recipe snapshots are retained locally. A daily snapshot is created on the first successful open/save after 17:00 local device time.
- `Mehr → Export / Backup → Lokale Rezept-Sicherungen` allows explicit restoration of a stored recipe snapshot. Categories and image files are not deleted by this recipe-only recovery.
- Full external `JennyliciousBackup` export remains the recommended independent backup.
- IndexedDB remains version 2; no schema bump and no destructive migration.

## V0.18.8 – Recipe Readability & Import Categories
- Tip and Mealprep are collapsible in the normal recipe detail view.
- Internal paragraphs, line breaks and blank lines in preparation steps, Tip and Mealprep are preserved through import, editing and saving and rendered with preserved whitespace.
- Import subcategories use checkboxes: import suggestions are shown first; existing subcategories are shown separately.
- Existing subcategories are marked green; genuinely new import suggestions are marked red. Suggested categories that already exist are shown once and marked green.
- Only checked subcategories are assigned. New subcategories are created only when the recipe is finally saved; unchecked suggestions create no empty categories.
- Changing the main category refreshes the existing-subcategory choices without creating categories.
- No database reset or schema change.

## V0.18.6 – Shopping mode UI cleanup
- In active shopping mode, per-item category chips are hidden because the category is already shown as the group heading.
- Outside active shopping mode, category chips remain available so assignments can still be corrected and learned.
- No database reset or schema change.

## V0.18.5 – Import Cleanup Fixes
- Recipe images are never used as automatic fallback images for main or subcategories. New categories stay image-free until a category image is explicitly assigned.
- Imported ingredients without a numeric amount no longer render as `0 n. B.`; `n. B.` is displayed as `nach Belieben`.
- Shopping category inference covers common vegetables, poultry and pantry spices more reliably while learned manual overrides retain priority.
- No IndexedDB schema bump and no production reset change.

## V0.18.4 – Image & History Fix
- Imported recipe images are restored through the existing `IMG[...]` image-key architecture after app restart.
- Existing V0.18.3 image Blobs stored as `recipe:<recipeId>` remain recoverable.
- New imported recipes no longer inherit cooking history from a previously deleted recipe whose numeric ID could otherwise be reused.
- New recipe IDs also take IDs already present in cook history into account.
- No IndexedDB schema bump.
- No production reset change; the V0.15.2 production baseline marker remains unchanged.

## V0.18.3 – Blocker Fixes
- iOS: `.jenny` file picker no longer restricts the unknown custom extension via an `accept` filter. Package validity is checked by the importer.
- Imported `recipe.webp`/PNG is persisted as a Blob in the IndexedDB `images` store under `recipe:<recipeId>`.

## V0.18.2 – Step Formatting
- Preparation headings are bold with a colon.
- Step descriptions appear indented below the heading.
- Same formatting in recipe view and cooking mode.

## V0.18.1 – UI & Cooking Fix
- Recipe metadata chips wrap across multiple lines.
- Tip and mealprep are no longer numbered preparation steps.
- Tip and mealprep are optional collapsed sections in cooking mode.

## V0.18.0 – Recipe Import V1
- `JennyliciousRecipe` formatVersion 1.
- `.jenny`/ZIP package with `recipe.json` and optional `recipe.webp`/PNG.
- Optional 0..n subcategories and 0..n specials.
- Editable import preview.
- Recipe tip and mealprep preserved and editable.
- No database reset / no schema bump.

## V0.17.2 – Flexible Recipe Classification
- Subcategories are optional.
- A recipe may belong to multiple subcategories.
- Recipes without a subcategory appear directly in the main category.
- Optional `Besonderheiten` field.
- Existing recipes with a single `sub` remain backward-compatible.

## V0.17.1 – Weekly Plan Identity & Leftovers
- Stable `planEntryId` for planned meal occurrences.
- Moving a meal preserves its identity.
- Duplicate recipes can be marked as `cook` or `leftovers`.

## V0.17.0 – Shopping Improvements
- Shopping aggregation with source-separated quantities.
- Fast manual input, +/- manual quantity adjustment and manual-item editing.
- Shopping-category rename/delete.

## Backup / Restore
- Backup format remains `JennyliciousBackup`, formatVersion 1.
- Structured stores include recipes, images, categories, settings, weeklyPlan, shopping, cookHistory and meta.
- Older supported backups may omit stores added later; missing current stores are initialized during restore.
- Unknown future backup formats remain blocked.

## Safety
- IndexedDB remains version 2.
- The V0.15.2 production baseline marker is retained for compatibility but is non-destructive from V0.19.0 onward.
- No automatic code path may clear the recipe store during ordinary startup, autosave, app minimization or page hide.
- External full backups remain strongly recommended because internal snapshots live in the same browser storage.



## V0.18.8
- Regression behoben: globale Formular-Controls erhalten keine Import-Layoutabstände mehr.
- Import-Unterkategorien sind wieder echte sichtbare Checkboxen mit rot/grüner Kennzeichnung.
- Unterkategorien im manuellen Rezepteditor sind wieder echte anklickbare Checkboxen.
- Absatz-/Leerzeilen-Erhalt bleibt ausschließlich auf Rezept-Langtexte beschränkt.
