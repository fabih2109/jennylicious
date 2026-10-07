# Jennylicious Recipe Package V1

Technische Schnittstelle für den Rezeptimport in Jennylicious.

## Paket
Eine `.jenny`-Datei ist technisch eine ZIP-Datei mit:
- `recipe.json` – Pflicht
- `recipe.webp` oder `recipe.png` – optional; der Dateiname steht in `image`

## JSON
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
    {"amount": 500, "unit": "g", "name": "Hackfleisch"}
  ],
  "steps": [
    {"title": "Sauce vorbereiten", "text": "Hackfleisch anbraten und die Sauce zubereiten."}
  ],
  "recipeTip": "Tipp aus der Quelle.",
  "mealPrep": "Hinweise zum Vorbereiten, Aufbewahren und Aufwärmen.",
  "image": "recipe.webp"
}
```

## Regeln
- `title`: Pflicht. Darf vor dem Import in Jennylicious editiert werden.
- `category.main`: Pflicht. Aktuell ein Vorschlag; darf editiert werden.
- `category.subcategories`: optional. Leeres Array `[]` ist ausdrücklich gültig. Beliebig viele Unterkategorien sind erlaubt.
- `specials`: optional. Beispiele: `Thermomix`, `Ofenmeister`, `Ofenhexe`, `Achtung Alkohol`. Diese Begriffe werden von Jennylicious durchsucht.
- `servings.value`: Portionszahl, wenn zuverlässig bekannt.
- `servings.status`: `confirmed`, wenn aus der Quelle sicher erkannt; sonst `unknown`. Bei `unknown` verlangt Jennylicious vor dem Speichern eine manuelle Portionszahl.
- `minutes`: gesamte bzw. sinnvoll geschätzte Rezeptzeit in Minuten. Wenn die Quelle keine Zeit nennt, vorsichtig angeben.
- `ingredients`: mindestens eine Zutat. Keine unbemerkten erfundenen Mengen.
- `steps`: mindestens ein Schritt. Überschrift und Text dürfen getrennt geliefert werden.
- `recipeTip`: optional; Tipp aus der Quelle. Nicht erfinden.
- `mealPrep`: optional; darf als ergänzende Empfehlung formuliert werden, wenn dies klar als Ergänzung behandelt wurde.
- `image`: optionaler Dateiname des Food-Bildes im Paket.

## Abwärtskompatibilität
Der Importer akzeptiert zusätzlich ältere Jennylicious-Feldnamen (`main`, `sub`, `subs`, `serv`, `mins`) und Zutaten als Arrays. Neue Dateien sollen jedoch ausschließlich das oben dokumentierte V1-Format verwenden.
