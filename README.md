## V0.21.4 – Konfigurierbarer Wochenbeginn

Basis: V0.21.3. Keine Datenbankmigration, kein Reset.

Neu in V0.21.4:
- Neue Einstellung **Wochenbeginn** unter Einstellungen.
- Wählbar: Montag bis Sonntag.
- Die Auswahl wird in den bestehenden App-Einstellungen lokal gespeichert und beim nächsten App-Start automatisch wiederhergestellt.
- Beispiel: Bei **Freitag** wird der Wochenplan als Freitag → Samstag → Sonntag → Montag → Dienstag → Mittwoch → Donnerstag dargestellt.
- Dieselbe Reihenfolge gilt auch für:
  - Rezept → „Zum Wochenplan hinzufügen“
  - „Mit anderem Tag tauschen“
  - Auswahl „Tage & Extras zum Einkauf“
  - Wochenplan-Badges am Rezept
- Die internen Wochentags-Slots bleiben unverändert (Montag=0 … Sonntag=6). Bestehende Planungen, `planEntryId`, Resteverwertung und Einkaufsbeiträge werden deshalb nicht migriert oder neu angelegt.

Enthalten aus V0.21.3:
- Alphabetische Sortierung von Rezepten, die direkt in einer Hauptkategorie liegen.
- Gekoppelte Akzent-/Hintergrundfarben für Lila, Grün, Blau, Rot und Gold.
- iOS-sicherer ZIP-Backup-Export aus V0.21.1.
- Rezeptbewertungen und einmalige In-App-Bewertungserinnerung.
- Einkaufsliste, Gewürz-/Einheitenlogik und Performance-/Data-Safety-Optimierungen der vorherigen Versionen.

Unverändert:
- IndexedDB-Version und Store-Struktur.
- Bildspeicher-/WebP-Logik.
- Rezeptdaten und Wochenplan-Datenmodell.
- Keine automatische Löschung oder Rücksetzung lokaler Daten.
