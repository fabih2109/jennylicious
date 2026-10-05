# Jennylicious V0.15.5 – Shopping Learning & PWA Updates

Base: V0.15.4. No database reset.

## Shopping
- Add custom shopping categories per shopping list/store.
- Change category of an item already on the shopping list.
- Change category of reminder items in Einkaufseinstellungen.
- Sparse local learning via `articleCategoryOverrides`: only manual corrections are persisted.
- Example: WC-Reiniger changed once to Haushalt -> future WC-Reiniger uses Haushalt automatically.
- No visible master article database and no preloaded thousands of products.
- Priority: learned override -> existing saved category -> automatic guess.
- Overrides are persisted inside IndexedDB `shopping/state`.

## PWA update behavior
- Service worker cache V0.15.5.
- Navigation is network-first with offline fallback.
- SW registration uses `updateViaCache: none` and explicitly checks for updates.
- New workers skip waiting and claim clients.
- Old cache versions are removed on activation.
- Local IndexedDB data is not cleared.

## Previous V0.15.4 features retained
- Alphabetical recipes/main/subcategories.
- White recipe-count badge.
- Editable category images.
- Add/delete shopping lists.
- Kitchen timer removed.
