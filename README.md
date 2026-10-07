# Jennylicious V0.18.3 – Shopping List Improvements

Base: corrected and user-tested V0.15.5.

## Backup
Mehr → Export / Backup → Backup exportieren.
Creates a versioned JSON file:
`Jennylicious_Backup_YYYY-MM-DD_HH-MM.json`

Backup format:
- format: JennyliciousBackup
- formatVersion: 1
- appVersion: 0.16.0
- IndexedDB database version
- timestamp
- all structured Jennylicious IndexedDB stores
- image Blobs encoded losslessly as Base64 inside the JSON

Included:
recipes, images, categories, settings, weeklyPlan, shopping,
cookHistory, meta. This includes custom shopping categories and
the sparse `articleCategoryOverrides` learned in V0.15.5.

## Restore
- Select JSON backup.
- Validate format and required stores before any destructive operation.
- Show explicit overwrite warning.
- On confirmation, replace all structured local stores in one IndexedDB transaction.
- Reload app after successful restore.
- Invalid files do not modify local data.

## Safety / migration
- No new production reset.
- V0.15.2 production baseline marker remains unchanged.
- No IndexedDB schema bump.
- Corrected V0.15.5 service-worker strategy retained (no forced controller-change reload).


## V0.16.1
Backup/Restore compatibility layer: older supported backups may omit stores added by later app versions; missing current stores are initialized empty during restore. Unknown future backup formats remain blocked.


## V0.18.3
Shopping aggregation with source-separated quantities, fast manual input (Enter / “weiter”), +/- manual quantity adjustment, manual-item editing, and shopping-category rename/delete.

Current app version: V0.18.3

## V0.18.3 – Flexible recipe classification
- Unterkategorien sind optional.
- Ein Rezept kann mehreren Unterkategorien derselben Hauptkategorie zugeordnet werden.
- Rezepte ohne Unterkategorie erscheinen direkt in der Hauptkategorie.
- Neues optionales Feld „Besonderheiten“ (z. B. Thermomix, Ofenmeister, Achtung Alkohol).
- Besonderheiten und alle Unterkategorien werden in der Rezeptsuche berücksichtigt.
- Bestehende Rezepte mit einfachem `sub` bleiben rückwärtskompatibel.

## V0.18.3 – Recipe Import V1
- JennyliciousRecipe formatVersion 1
- .jenny/ZIP package: recipe.json + optional recipe.webp/png
- optional 0..n subcategories
- optional 0..n specials
- editable import preview
- recipe tip and meal-prep fields preserved and editable
- no database reset / no schema bump


## V0.18.3
- Rezept-Metadaten-Chips umbrechen sauber über mehrere Zeilen.
- Tipp und Mealprep sind keine nummerierten Zubereitungsschritte mehr.
- Tipp und Mealprep sind im Kochmodus optional einklappbar und standardmäßig geschlossen.


## V0.18.3
- Zubereitungsüberschriften fett mit Doppelpunkt.
- Beschreibung darunter eingerückt.
- Einheitlich in Rezeptansicht und Kochmodus.


## V0.18.3 – Blocker fixes
- iOS: .jenny file picker no longer restricts unknown custom extension via accept filter. Package validity is checked by the importer.
- Imported recipe images: recipe.webp/png Blob is persisted directly to IndexedDB images store as recipe:<recipeId>.
- No IndexedDB schema bump and no production reset change.
