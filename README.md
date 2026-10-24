# Jennylicious V0.22.0 – Zutaten pro Zubereitungsschritt

Basis: V0.21.10 (blaue Kronen). Datenmodell bleibt abwärtskompatibel. Keine IndexedDB-Versionserhöhung, kein Reset.

## Neu
- Unter jeder Schrittüberschrift erscheint eine Zutatenliste für genau diesen Schritt, oberhalb der Zubereitungsanleitung.
- Beim Ändern der Portionszahl skalieren die Zutatenlisten im Rezeptdetail und im Kochmodus dynamisch.
- Mengen im Text werden nur dann skaliert, wenn eine exakt passende, erkennbare Mengen-/Einheitenangabe eindeutig einer Zutat dieses Schritts zugeordnet werden kann. Temperaturen, Zeiten und andere Zahlen bleiben unverändert.
- Bei älteren Rezepten versucht die App, aus dem Zubereitungstext genannte Zutaten vorzuschlagen. Wird eine Zutat in mehreren Schritten genannt, kennzeichnet die App eine unklare Verteilung mit **gesamt**; die tatsächliche Teilmenge sollte im Rezepteditor festgelegt werden.
- Im Rezepteditor befindet sich unter jedem Zubereitungsschritt die Schaltfläche **Zutaten für diesen Schritt zuordnen**. Dort sind Zutaten und bei Bedarf Teilmengen für die ursprüngliche Portionszahl auswählbar.
- Diese neuen Zuordnungen werden als optionales `stepIngredients`-Feld direkt mit dem Rezept gespeichert und ebenso durch bestehende Backup-Funktionen gesichert.

## Sicherheit und Einschränkungen
- Bisherige `steps` bleiben wortgetreu gespeichert; die App verändert nicht stillschweigend Quelltexte. Dynamische Skalierung erfolgt nur bei der Anzeige.
- Bei unklaren Zutatenaufteilungen ist menschliche Prüfung erforderlich; die App nimmt keine willkürlichen Teilmengen an.
- Die gespeicherte `stepIngredients`-Liste besteht aus geordneten Listen je Schritt: `{ingredientIndex, share, inferred}`. Die `share` bezieht sich auf die Gesamtmenge der Zutatenliste zur Original-Portionsgröße.
- Bestehende Datenbanken, Bilder, Einkaufsliste, Wochenplan, Bewertungen und Backup-Logik bleiben unangetastet.
- Nach dem Upload Test auf Android und iPhone: bestehendes Rezept und neues Rezept; Portionswechsel 2→4; Teilmengen; Rezepteditor-Speichern; App-Neustart.

---

## V0.21.10 – Blaue Kronen für Kinderbewertung

Basis: V0.21.9. Keine Datenbankmigration, kein Reset.

Neu in V0.21.10:
- Kinderbewertung verwendet jetzt eine eigene kindgerechte Krone statt Brachiosaurier.
- Krone in klarem Blau (#1687d9), inaktive Kronen hellblau.
- Einheitliches Kronen-SVG in Rezeptansicht, Rezeptkacheln, Editor und Suchfiltern.
- Texte auf „Krone/Kronen“ angepasst.
- Bestehende kidsRating-Werte bleiben unverändert erhalten.

## V0.21.9 – Dino-Darstellung

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


### V0.21.9
- Kinderbewertung nutzt echte eingebettete SVG-Brachiosaurier statt CSS-Masken.
- Dunkel-goldene Dino-Farbe für bessere Erkennbarkeit.
- Dinos im Rezepteditor zuverlässig sichtbar und klickbar.
- Gleiche Dino-Symbole auf Rezeptseite, Rezeptkacheln und in Suchfiltern.
- Dino-Reihe auf der Rezeptseite höher positioniert, damit sie nicht an der Bildkante abgeschnitten wird.
