# Jennylicious PWA V0.15.2 – Clean Production Baseline

IMPORTANT: This version intentionally performs a ONE-TIME HARD RESET of previous Jennylicious test data.

On the first successful start of V0.15.2:
- all structured IndexedDB stores are cleared
- the legacy `core` store is cleared
- a `productionBaseline = 0.15.2` marker is written
- embedded demo recipes are gone
- embedded demo recipe images are gone
- default/demo recipe categories are gone
- the weekly plan starts empty
- old V0.13 migration is permanently disabled

After that first reset, the marker prevents V0.15.2 from resetting data again.

Most important behavior:
An empty `recipes` store is now a VALID persisted state. Zero recipes no longer triggers migration or reseeding.

Expected first-start state after deployment:
- 0 recipes
- 0 recipe-created main/sub categories
- empty weekly plan
- empty shopping lists
- empty cook history
- no active cooking session/timer

Test:
1. Deploy V0.15.2 and open/reload Jennylicious.
2. Verify 0 recipes and no old recipe categories.
3. Create a test main category + subcategory + recipe.
4. Close and reopen: they must remain.
5. Delete the recipe and categories so the app returns to 0 recipes.
6. Close and reopen again.
7. It MUST remain at 0 recipes. Nothing may reappear.
