## V0.19.9 – Einheitenlose Zutaten & Gewürze

Basis: V0.19.8.corr. Keine Datenbankmigration, kein Reset.

Neu:
- Im Zutateneditor ist eine leere Einheit ausdrücklich auswählbar; neue Zutaten starten ohne erzwungene Einheit.
- Leere Mengen werden intern als fehlende Menge (`null`) statt als künstliche `0` gespeichert.
- Importierte, nicht standardmäßige Einheiten (z. B. `Zehen`) bleiben beim Bearbeiten erhalten und werden nicht still auf `g` zurückgesetzt.
- Neue feste Einkaufskategorie `Gewürze`, standardmäßig vor `Vorrat`.
- Breite Gewürzerkennung u. a. für Salz, Pfeffer, Chili, Curry, Kurkuma, Zimt, Kreuzkümmel, Kardamom, Muskat, Senfkörner, Oregano, Thymian, Rosmarin, Basilikum, Lorbeer, Gewürzmischungen usw.
- Eindeutig frische Kräuter (`frisch`, `Bund`, `Topf`) bleiben bei Obst & Gemüse.
- Bereits vorhandene automatisch als `Vorrat`/`Sonstiges` einsortierte Gewürze werden schonend nach `Gewürze` verschoben; manuelle Kategoriezuweisungen bleiben erhalten.
- Performance/Data-Safety, Einkaufslisten-UI und Wochenplanlogik aus V0.19.8.corr bleiben unverändert.

Regel-Update:
- Flexible Mengenangaben wie `Pfeffer nach Belieben` werden im Jennylicious-JSON künftig als `amount: null`, `unit: ""`, `name: "Pfeffer"` exportiert. Der Hinweis zum Abschmecken kann in der Zubereitung erhalten bleiben.
