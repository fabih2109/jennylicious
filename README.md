# Jennylicious PWA V0.18.8 – Recipe Readability & Import Categories

Current app version: V0.18.8

Base: V0.18.4 Image & History Fix.

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
- No new production reset.
- V0.15.2 production baseline marker remains unchanged.
- No IndexedDB schema bump.


## V0.18.8
- Regression behoben: globale Formular-Controls erhalten keine Import-Layoutabstände mehr.
- Import-Unterkategorien sind wieder echte sichtbare Checkboxen mit rot/grüner Kennzeichnung.
- Unterkategorien im manuellen Rezepteditor sind wieder echte anklickbare Checkboxen.
- Absatz-/Leerzeilen-Erhalt bleibt ausschließlich auf Rezept-Langtexte beschränkt.
