## V0.21.7 – EKL Toggle Layout, Knoblauchzehen & Rezept-Zurücknavigation

Basis: V0.21.6. Keine Datenbankmigration und kein Reset.

### Neu / korrigiert
- Mengen-/Einheiten-Schalter in der normalen Einkaufsliste als echter 28-px-Kreis umgesetzt.
- Der Kreis hat damit exakt denselben Durchmesser wie die −/+ Buttons und sitzt in derselben Zeile bzw. auf derselben Mittelachse.
- Einkaufsmodus (`Einkauf starten`): Der Mengen-Schalter wird nicht mehr angezeigt. Dort bleibt nur die kompakte Checkbox-/Artikeldarstellung.
- Die zuvor festgelegte Sichtbarkeit von Menge+Einheit bleibt im Einkaufsmodus trotzdem wirksam.
- Knoblauch mit Einheit `Zehe/Zehen` bleibt semantisch als Knoblauchzehe(n) erkennbar:
  - sichtbar: `1 Knoblauchzehe`, `2 Knoblauchzehen`
  - Menge ausgeblendet: `Knoblauchzehen`
- `Knoblauchpulver` bleibt ein eigenständiger Artikel und wird nicht als Knoblauchzehe behandelt.
- Rezeptdetail-Zurücknavigation repariert:
  - Rezept mit Unterkategorie → passende Unterkategorie wird neu aufgebaut und geöffnet.
  - Rezept ohne Unterkategorie → Hauptkategorie wird neu aufgebaut und geöffnet.
  - Damit entsteht nach dem Speichern eines neuen Rezepts keine leere Zwischenansicht mehr.

### Weiterhin enthalten
- V0.21.6 Mengenanzeige pro Einkaufsartikel.
- V0.21.5 kompakte Hauptansichten und EKL-Kategorie-Fix.
- V0.21.4 konfigurierbarer Wochenbeginn.
- iOS-sicheres Backup, Bewertungen, Einkaufsnormalisierung sowie bestehende Bild-/Daten-Safety-Logik.
