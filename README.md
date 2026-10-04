# Jennylicious PWA V0.12.0

Erster PWA-Build auf Basis von Jennylicious V0.11.17.

## Was in diesem Schritt geändert wurde
- PWA Manifest ergänzt
- Service Worker für App-Shell/Offline-Start ergänzt
- iOS/PWA Meta-Tags ergänzt
- App-Icons ergänzt
- Version auf V0.12.0 gesetzt
- Browser-Titel korrigiert

## Bewusst noch NICHT geändert
- Bestehende UI und Fachlogik
- Persistenz der App-Daten
- Umstellung auf IndexedDB

Die IndexedDB-Migration folgt nach dem ersten erfolgreichen HTTPS-/iPhone-PWA-Test.

## Wichtig
Eine PWA funktioniert nicht korrekt, wenn `index.html` einfach lokal als Datei geöffnet wird.
Der Ordner muss über HTTPS bereitgestellt werden (oder lokal über localhost für Entwicklung).

## iPhone-Test nach Deployment
1. HTTPS-Adresse in Safari öffnen.
2. Teilen-Schaltfläche öffnen.
3. „Zum Home-Bildschirm“ wählen.
4. Jennylicious über das neue Home-Screen-Icon starten.
5. Flugmodus/Offline-Verhalten anschließend separat testen.


## GitHub-Mobile-Upload

Diese Variante ist absichtlich ohne Unterordner aufgebaut.
Auf Android können alle acht Dateien gemeinsam in das Root-Verzeichnis des GitHub-Repositories hochgeladen werden.
