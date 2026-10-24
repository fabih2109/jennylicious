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
