# Jennylicious Recipe Package V1 – Standalone Exportformat für Jenny

Diese Datei ist die verbindliche technische Schnittstelle für den Export eines bereits fertig erstellten Rezepts nach Jennylicious.

Sie setzt **keine weiteren Jennylicious-Regeldateien** voraus. Rezepttext und Rezeptbild werden vor dem Export mit Jennys eigenen bewährten Prompts erstellt. Der Export ist anschließend ausschließlich eine **Formatumwandlung**, keine neue kreative Rezeptbearbeitung.

## Workflow

Wenn im selben Chat bereits ein finales Rezept und ein finales Rezeptbild vorliegen und der Befehl sinngemäß lautet:

- `Für Jennylicious exportieren.`
- `Für Jennylicious importieren.`
- `Jennylicious-Paket erstellen.`

ist wie folgt vorzugehen:

1. Das bereits finale Rezept vollständig übernehmen.
2. Keine kochrelevanten Informationen kürzen, zusammenfassen oder weglassen.
3. Zutaten nach den unten definierten Normalisierungsregeln strukturieren.
4. Das bereits finale Rezeptbild unverändert als Rezeptbild verwenden.
5. `recipe.json` erzeugen.
6. Rezeptbild bevorzugt als `recipe.webp`, alternativ als `recipe.png`, beilegen.
7. Beides in eine `.jenny`-Datei bündeln. Eine `.jenny`-Datei ist technisch eine ZIP-Datei.

Falls das bereits erzeugte Bild im Chat technisch nicht als Datei zugänglich ist, darf **kein neues Bild generiert werden**. Stattdessen soll dieselbe finale Bilddatei erneut bereitgestellt bzw. hochgeladen werden.

## Paketinhalt

Eine `.jenny`-Datei enthält:

- `recipe.json` – Pflicht
- `recipe.webp` – bevorzugt
- alternativ `recipe.png`, wenn WebP technisch nicht möglich ist

Der in `recipe.json` unter `image` angegebene Dateiname muss exakt zur enthaltenen Bilddatei passen.

## JSON-Struktur

```json
{
  "format": "JennyliciousRecipe",
  "formatVersion": 1,
  "title": "Lasagne",
  "category": {
    "main": "Hauptgerichte",
    "subcategories": ["Aufläufe", "Familienessen"]
  },
  "specials": ["Ofenmeister", "Achtung Alkohol"],
  "servings": {
    "value": 4,
    "status": "confirmed"
  },
  "minutes": 60,
  "ingredients": [
    {"amount": 500, "unit": "g", "name": "Hackfleisch"},
    {"amount": null, "unit": "", "name": "Pfeffer"}
  ],
  "steps": [
    {"title": "Sauce vorbereiten", "text": "Hackfleisch anbraten und die Sauce zubereiten."}
  ],
  "recipeTip": "Tipp aus dem finalen Rezept.",
  "mealPrep": "Hinweise zum Vorbereiten, Aufbewahren und Aufwärmen.",
  "image": "recipe.webp"
}
```

## Feldregeln

- `title`: Pflicht.
- `category.main`: Pflicht. Vorschlag für die Hauptkategorie; kann später in Jennylicious geändert werden.
- `category.subcategories`: optional. Leeres Array `[]` ist gültig. Mehrere Unterkategorien sind erlaubt.
- `specials`: optional. Beispiele: `Thermomix`, `Ofenmeister`, `Ofenhexe`, `Schnellkochtopf`, `Achtung Alkohol`.
- `servings.value`: Portionszahl, wenn im finalen Rezept zuverlässig vorhanden.
- `servings.status`: `confirmed`, wenn die Portionszahl sicher bekannt ist; sonst `unknown`.
- `minutes`: gesamte Rezeptzeit in Minuten, wenn zuverlässig aus dem finalen Rezept bestimmbar. Keine unbegründete Präzision erfinden.
- `ingredients`: mindestens eine Zutat.
  - `amount`: konkrete Zahl, wenn vorhanden; sonst `null`.
  - Ein fehlender Wert darf **nie** zu `0` umgedeutet werden.
  - `unit`: konkrete Einheit, wenn vorhanden; sonst ausdrücklich `""`.
  - Es darf **keine Einheit erfunden** werden, insbesondere nicht automatisch `g`, `Stk.` oder ähnliche Ersatzwerte.
  - `name`: reiner Zutatenname ohne Mengen- oder Einheitsteile.
- `steps`: mindestens ein Schritt. Überschrift und Text werden getrennt gespeichert.
  - Die Umwandlung in JSON ist **keine Zusammenfassung**.
  - Alle kochrelevanten Details des finalen Rezepts müssen erhalten bleiben.
  - Absatzstruktur und relevante Leerzeilen innerhalb eines Schritts sollen erhalten bleiben.
- `recipeTip`: optional. Bestehenden Tipp vollständig übernehmen; nicht neu erfinden.
- `mealPrep`: optional. Bestehende Hinweise vollständig übernehmen; nicht unnötig kürzen.
- `image`: Dateiname des bereits finalen Rezeptbildes im Paket; bevorzugt `recipe.webp`.

## Verbindliche Normalisierung flexibler Zutatenangaben

Flexible Mengenangaben ohne konkrete Menge werden beim JSON-Export auf den **reinen Zutatenname** reduziert.

Beispiele:

- `Pfeffer nach Belieben` → `{"amount": null, "unit": "", "name": "Pfeffer"}`
- `Salz nach Geschmack` → `{"amount": null, "unit": "", "name": "Salz"}`
- `Muskat zum Abschmecken` → `{"amount": null, "unit": "", "name": "Muskat"}`
- `Chili nach Bedarf` → `{"amount": null, "unit": "", "name": "Chili"}`
- `Basilikum nach Belieben` → `{"amount": null, "unit": "", "name": "Basilikum"}`

Die Zusätze

- `nach Belieben`
- `nach Geschmack`
- `zum Abschmecken`
- `nach Bedarf`
- sinngleiche flexible Dosierhinweise

gehören **nicht** in `name`, wenn keine konkrete Menge genannt ist.

Falls die flexible Dosierung für das sichere Nachkochen relevant ist, soll sie im passenden Zubereitungsschritt erhalten bleiben.

### Konkrete Ausgangsmenge bleibt erhalten

Wenn eine konkrete Menge genannt ist, bleibt sie bestehen.

Beispiel:

`1 TL Pfeffer, nach Belieben mehr`

wird nicht auf eine leere Menge reduziert, sondern z. B. als

```json
{"amount": 1, "unit": "TL", "name": "Pfeffer"}
```

exportiert. Der Hinweis, dass später nach Geschmack nachgewürzt werden kann, kann im Zubereitungsschritt verbleiben.

## Rezeptbild und Kategoriebilder

Das Bild im `.jenny`-Paket ist **ausschließlich das Rezeptbild**.

Das Paket enthält keine Haupt- oder Unterkategoriebilder. Das Rezeptbild darf niemals automatisch als Kategoriebild verwendet werden.

## Abwärtskompatibilität

Der Jennylicious-Importer kann zusätzlich ältere Feldnamen wie `main`, `sub`, `subs`, `serv`, `mins` sowie ältere Zutaten-Arrays akzeptieren.

Neue Exporte sollen ausschließlich das oben dokumentierte V1-Format verwenden.
