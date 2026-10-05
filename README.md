# Jennylicious V0.15.5 – corrected build

This replaces the first V0.15.5 build.

Important:
- No database reset.
- No IndexedDB schema change.
- Shopping learning/custom categories remain included.
- Removed the aggressive service-worker update/reload chain from the first V0.15.5.
- No automatic `location.reload()` on service-worker controller changes.
- Service worker uses a versioned registration URL and network-first navigation.
- Existing local recipe/category/shopping data remain untouched.

Upgrade note for a device still controlled by the old V0.15.3 worker:
The old worker may continue serving its cached index until it receives the new worker.
Opening the deployed page once with a cache-busting query such as `?v=155fix` is a safe bootstrap;
after the corrected worker activates, normal launches should use the current network version.
Do not clear site data, because that can remove IndexedDB.
