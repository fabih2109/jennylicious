# Jennylicious PWA V0.15.0 – Full Local Persistence

Built on the successfully tested V0.14.0 structured IndexedDB version.

Now persisted:
- recipes and separate WebP image blobs
- custom categories and settings
- weekly plan (`plan`)
- weekly shopping ledger
- shopping lists for Kaufland/Lidl/Aldi
- active shopping store
- store-specific recurring/reminder items
- store-specific aisle/category order
- shopping started state
- cooking history and notes

The existing V0.14 database schema and recipe/image migration are retained.

Not yet made persistent in this build:
- transient modal/editor drafts
- running timer state / cooking-session resume

Recommended test:
1. Verify the two existing V0.13/V0.14 test recipes remain.
2. Change several days in the weekly plan.
3. Add/check shopping items in at least two stores.
4. Mark one recipe cooked and add a note.
5. Fully close Jennylicious.
6. Reopen and verify all three areas.
