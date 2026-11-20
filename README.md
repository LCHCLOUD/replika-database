# Airsoft HQ: Waffenkatalog

Die App lädt `katalog.json` beim Start aus diesem Repository. Änderungen an der Datei
erscheinen in der App, ohne dass ein App-Update nötig ist.

## Aufbau

```json
{
  "version": 1,
  "aktualisiert": "2026-11-20",
  "waffen": [
    { "hersteller": "G&G", "modell": "CM16 Raider 2.0", "typ": "Sturmgewehr", "antrieb": "AEG", "fps": 330 }
  ]
}
```

| Feld | Erlaubte Werte |
|---|---|
| `typ` | `Sturmgewehr`, `DMR`, `Sniper`, `SMG`, `LMG`, `Pistole`, `Shotgun` |
| `antrieb` | `AEG`, `GBB`, `HPA`, `Federdruck` |
| `fps` | Richtwert mit 0,20-g-BBs als Ganzzahl |

Einträge mit unbekanntem `typ` oder fehlenden Feldern überspringt die App.
Ist die ganze Datei kaputt oder leer, behält die App den bisherigen Katalog.
Setze `aktualisiert` bei jeder Änderung auf das aktuelle Datum.
