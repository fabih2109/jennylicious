# Jennylicious PWA V0.13.0 – IndexedDB Test

Erster Persistenz-Build auf Basis der auf iPhone und Android bestätigten PWA V0.12.0.

## In IndexedDB gespeichert
- Rezepte einschließlich Favoriten und manueller Rezeptbilder
- selbst angelegte Haupt- und Unterkategorien
- selbst gewählte Kategoriebilder
- Grundeinstellungen: Standard-Portionen, Startansicht, Designfarbe

Beim allerersten Start wird der mitgelieferte Demo-Bestand automatisch als Ausgangsbestand in IndexedDB geschrieben.

## Noch bewusst nicht persistent
- Wochenplan
- Einkaufslisten / Reminder / Gangreihenfolge
- Kochhistorie
- aktive Kochsession / Timer
- vollständiges Backup/Restore

## Test
1. V0.13.0 über GitHub committen und Pages aktualisieren lassen.
2. PWA öffnen.
3. Ein Testrezept manuell anlegen.
4. Optional Favorit/Theme/Standard-Portionen ändern.
5. App vollständig schließen.
6. App erneut vom Home-Bildschirm öffnen.
7. Prüfen, ob Änderungen erhalten bleiben.

Wichtig: Browser-/Website-Daten für fabih2109.github.io nicht löschen, denn dabei kann IndexedDB ebenfalls gelöscht werden.
