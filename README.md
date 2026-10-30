# Jennylicious V0.22.6 – Responsive Bewertungsfußzeile

Basis: V0.22.5, ausschließlich Darstellung von Rezeptkacheln geändert.

- Titel steht unten links über einer festen Infozeile; keine Überlagerung mit Bewertungen.
- Breitere Handys (ab 390 CSS-Pixel Viewport): Kochzeit links, bis zu 5 blaue Kronen mittig, bis zu 5 goldene Sterne rechts in einer Zeile.
- Schmalere Handys (unter 390 CSS-Pixel): Kochzeit links; Bewertungen rechts übereinander, Sterne über Kronen.
- Auch Kochzeiten mit vierstelliger Minutenzahl (z. B. 1224 Min) berücksichtigt.
- Wenn keine Bewertung existiert, keine Sterne/Kronen als Platzhalter.
- Favoritenherz bleibt rechts oben; Schatten nur im unteren Kachelbereich.
- Keine Änderung von Rezeptdaten, Bewertungen, Bilderverwaltung, Backup, IndexedDB, Zutaten- oder Kochmoduslogik.
- Die Kochmodus-Schrittzutaten bleiben wie in V0.22.5 per CSS ausgeblendet.
- Kein Datenbank-Reset.

# Jennylicious V0.22.5 – Bewertungen links oben

Basis: V0.22.4. Nur Darstellung von Rezeptkacheln geändert.

- Goldene Sterne **links oben im Rezeptbild**, blaue Kronen **direkt darunter**, in unveränderter Größe.
- Titel und Kochzeit links unten **direkt untereinander**, unabhängig von den Bewertungen.
- Längere Rezeptnamen werden auf maximal vier Zeilen begrenzt, damit sie auf kleinen Displays nicht bis zu den Bewertungen reichen. Der vollständige Titel bleibt in Rezeptansicht und Daten unverändert.
- Leichte Kontrastverstärkung auf Bildern für Lesbarkeit von Bewertungen und Titel.
- Favoriten-Herz bleibt rechts oben.
- Kochmodus: Schritt-Zutatenkästen bleiben wie zuvor ausgeblendet; die Berechnung und Zuordnungen bleiben erhalten.
- Keine Änderung an IndexedDB, Rezepten, Backup/Restore, Bilddaten, Wochenplan oder Einkaufslisten.

---

# Jennylicious V0.22.4 – Einheitliche Fußzeile bei Rezeptkacheln

Basis: V0.22.3, ohne Datenmigration.

- Rezepttitel bleiben über dem unteren Informationsbereich der Kacheln.
- Rezeptdauer steht immer links unten auf gleicher Grundlinie.
- Vorhandene Sterne und Kinder-Kronen stehen immer rechts unten in gleicher Reihenfolge und bleiben unabhängig von der Titellänge verankert.
- Auch Rezepte ohne Bewertungen reservieren dieselbe Höhe für die Fußzeile.
- Blaue Kronen und goldene Sterne behalten ihre bisherige Symbolgröße.
- Kochmodus: Zutatenkästen innerhalb der Zubereitungsschritte bleiben wie in V0.22.3 ausgeblendet; Zuordnungsdaten und Mengenlogik bleiben unverändert.
- IndexedDB, Rezeptbilder, Backup/Restore und Wochenplan sind unverändert.

---

# Jennylicious V0.22.3 – Kartenbewertungen & Kochmodus-Anzeige

Basis: V0.22.2. Alle bisherigen Funktionen bleiben erhalten.

## Änderungen
- Auf Rezeptkacheln teilen sich Titel, Minutenangabe und Bewertungen jetzt einen vertikalen Layoutbereich; die Bewertungen liegen nicht mehr als Überlagerung über dem Rezepttitel.
- Blaue Kronen in Kacheln, Rezeptdetail und Editor sind optisch an die jeweiligen Sterne angepasst. Favoriten-Herz und Sterne-/Kronenbewertungen bleiben ansonsten unverändert.
- Zutaten-Kästchen pro Zubereitungsschritt im Kochmodus sind **ausschließlich per CSS ausgeblendet**. Die Zuordnungen, Teilmengen, Portionenberechnung und Editor-Funktionen bleiben im Datenmodell erhalten.
- Keine Änderung an Rezepten, Bildern, Einkaufslisten, IndexedDB, Backupformat oder Caches außer der Versionskennung.

## Prüfpunkte nach dem GitHub-Upload
1. Kategorie mit langem Titel (z. B. „Der perfekte Pfannkuchen“) und 5 Sternen + 5 Kronen: Titel und Bewertungen dürfen sich nicht überlagern.
2. Rezept ohne Bewertung und mit nur einer Bewertungsart prüfen.
3. Rezept mit Bewertungen in Detailansicht und Editor prüfen.
4. Kochmodus: keine Schritt-Zutatenkästen; Zubereitungstext und Gesamtzutatenliste bleiben erhalten.
5. Rezepteditor: Zutatenzuordnungen weiterhin editierbar, ohne Datenverlust.

## Technische Prüfung
- Kein IndexedDB-Upgrade und keine Datenmigration.
- Keine Änderung des Verhaltens beim Speichern, Laden und Importieren.

---

## Bisheriger Stand (V0.22.2)
# Jennylicious V0.22.2 – Schritt-Zutaten nur beim Kochen

Ausgangsbasis: V0.22.1, alle bisherigen Funktionen enthalten.

## Änderungen

- In der normalen Rezeptdetailansicht bleiben Gesamtzutaten und der vollständige Zubereitungstext erhalten; die zusätzlichen Zutaten-Kärtchen je Zubereitungsschritt sind dort ausgeblendet.
- Im Kochmodus erscheinen die kompakt gestalteten gelben Schritt-Zutatenkarten aus V0.22.1 weiterhin. Die Zutatenmengen folgen der gewählten Portionszahl.
- Automatische Zuordnung erfolgt über alle Schritte eines Rezepts hinweg. Eine bloße spätere Erwähnung einer zuvor verwendeten Zutat zählt nicht mehr automatisch als erneute vollständige Menge.
- Werden explizite Teilmengen pro Schritt eindeutig erkannt und überschreiten zusammen nicht die Gesamtmenge, werden sie entsprechend zugeordnet. Unklare Verteilungen werden **nicht** frei geschätzt.
- Ein Button **Zuordnung prüfen** im Rezepteditor zeigt die ermittelten Zutaten pro Schritt und kennzeichnet mögliche Mehrfachverwendungen. Manuelle Zuordnungen/Teilmengen bleiben erhalten und haben Vorrang.
- Neu angelegte und importierte Rezepte erhalten die berechnete Zuordnung. Bei bestehenden Rezepten wird sie ohne Datenmigration und ohne ungefragtes Überschreiben gespeicherter manueller Zuordnungen ermittelt; sie kann im Editor geprüft und beim Speichern übernommen werden.
- Kompatibel mit älteren Rezepten, auch wenn das Feld `stepIngredients` noch nicht vorhanden ist.

## Sicherheit

- Keine Änderungen an IndexedDB-Struktur, Bildspeicher oder Backupformat.
- Kein Datenreset und keine automatische Bestandsänderung bei Start der App.
- Die Rezepte behalten ihre vollständigen Original-Zubereitungstexte; Portionsmengen im Text werden nur bei eindeutigem Match dynamisch dargestellt, nicht permanent umgeschrieben.
- Die Bereinigung/Umformulierung alter Rezepttexte über exportierte Backup-Daten erfolgt **nicht** in dieser Version.

## Manuelle Tests nach GitHub-Upload

1. Ein bestehendes Rezept in der normalen Rezeptansicht öffnen: **keine** gelben Schritt-Zutatenkarten.
2. Kochmodus starten: gelbe kompakte Zutatenkarten erscheinen; Portionswechsel skalieren Mengen.
3. Mehrfach verwendete Zutaten prüfen (z. B. Nudeln kochen und später im Auflauf verwenden): nicht zweimal die gesamte Menge anzeigen.
4. Rezepteditor öffnen: „Zuordnung prüfen“ und gegebenenfalls Teilmengen manuell korrigieren.
5. Neu importiertes Rezept sowie ein bestehendes Rezept mit manuellen Teilmengen testen.
