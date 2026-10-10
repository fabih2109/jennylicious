## V0.19.8.corr – Einkaufsliste: Ladenmarken & kompakte Bearbeitung

Basis: V0.19.7. Keine Datenbankmigration, kein Reset.

Neu:
- lokale, offline-fähige visuelle Marken für Kaufland, Lidl, Aldi und dm; freie Ladennamen bleiben normale Textlisten
- Standardläden können beim Anlegen schnell ausgewählt oder frei eingetippt werden
- während des aktiven Einkaufs verschwindet die große JENNYLICIOUS/Einkauf-Kopfzeile; oben stehen nur Zurück sowie Ladenmarke/-name zentriert
- permanente Kategorie-Dropdowns pro Artikel entfernt; die Kategorie ist bereits über den Abschnitt sichtbar
- ein Stift pro Artikel öffnet die Bearbeitung der Einkaufskategorie; bei manuellen Artikeln können dort zusätzlich Name/Menge geändert werden
- Wochenplan-/Extra-Logik aus V0.19.7 sowie Performance/Data-Safety bleiben unverändert


### Korrekturen in 0.19.8.corr
- Einkaufslisten-Auswahl zeigt lokale Ladenmarker; Abbrechen ist optisch getrennt.
- + Wochenplan steht in einer eigenen oberen Zeile; Ladenname erhält die volle Breite.
- Plus/Minus bei Rezeptartikeln ohne Einheit verwendet dieselbe Einheit statt künstlich „Stk.“.
- Knoblauchzehen und Zehen Knoblauch werden als derselbe Einkaufsartikel mit Einheit „Zehen“ normalisiert.
- Bestehende, bereits getrennte Knoblauch-Einträge werden beim Rendern sicher zusammengeführt.
