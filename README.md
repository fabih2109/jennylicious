## V0.21.5 – Konfigurierbarer Wochenbeginn

Basis: V0.21.3. Keine Datenbankmigration, kein Reset.

Neu in V0.21.5:
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


### V0.21.5 – Compact UI & Shopping Fix
- Startseite: Suchfeld, Introtexte und „Alle Rezepte“ entfernt.
- Wochenplan: Untertitel und „Was sollen wir essen?“ entfernt.
- Wochenplan-Rezeptsuche: Trefferliste aktualisiert sich ohne Neuaufbau des Eingabefelds; Tastatur/Fokus bleiben stabil.
- Einkauf: große Seitenüberschrift entfernt, kompakter Kopf.
- Einkauf: tatsächlich vorhandene Kategorien werden immer gerendert, sodass z. B. Sahne/Kühlung nicht unsichtbar werden kann.
