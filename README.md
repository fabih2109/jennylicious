## V0.21.8 – Kinderbewertung, Suchfilter & EKL-Kategorien

Basis: V0.21.7. Keine Datenbankmigration, kein Reset.

Neu in V0.21.8:
- Einkaufskategorien können direkt in der Gangreihenfolge über ✎ umbenannt werden.
- Zugeordnete Einkaufsartikel, Reminder und gelernte Kategoriezuordnungen werden beim Umbenennen mitgeführt.
- Rezeptsuche sucht nicht mehr live bei jedem Tastendruck: Suchtext eingeben und mit Enter oder dem Suchbutton bestätigen.
- „Mehr → Meine Rezepte“ entfernt.
- Neue optionale Kinderbewertung „Wie hat’s den Kindern geschmeckt?“ mit 1–5 grasgrünen Brachiosaurier-Symbolen.
- Kinderbewertung wird auf Rezeptkacheln direkt unter den Sternen und im Rezeptdetail angezeigt.
- Im Rezepteditor liegt die Kinderbewertung direkt unter der normalen Sternebewertung; 1 Dino = kam nicht gut an, 5 Dinos = Kinderliebling.
- Neue Zusatzfilter in der Suche: ★ 4+, ★ 5, Dino 4+, Dino 5.
- Sterne- und Dino-Filter sind unabhängig kombinierbar und gelten sowohl für Rezeptsuche als auch Suche nach Zutaten.
- Bestehende Rezepte ohne kidsRating bleiben unverändert und gelten als noch nicht kinderbewertet.
- Import akzeptiert optional rating und kidsRating; bestehende V1-Pakete ohne diese Felder bleiben kompatibel.

Unverändert:
- IndexedDB-Struktur und Datenbankversion.
- Backup-/Restore-Logik.
- Wochenplan- und Einkaufsdatenmodell.
- Bildspeicher-/WebP-Logik.
- Keine automatische Löschung oder Rücksetzung lokaler Daten.
