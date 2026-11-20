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

| Feld | Pflicht | Bedeutung |
|---|---|---|
| `hersteller`, `modell` | ja | Anzeige und Gruppierung im Menü |
| `typ` | ja | `Sturmgewehr`, `DMR`, `Sniper`, `SMG`, `LMG`, `Pistole`, `Shotgun` |
| `antrieb` | ja | `AEG`, `GBB`, `HPA`, `Federdruck` |
| `fps` | ja | Richtwert mit 0,20-g-BBs als Ganzzahl |
| `bbGewicht` | nein | in Gramm, z. B. `0.25`. Standard: `0.20` |
| `akkuArt` | nein | `LiPo`, `Li-Ion`, `NiMH`, `NiCd`, `LiFePO4`. Standard bei AEG: `LiPo` |
| `akku` | nein | Freitext, z. B. `"7,4 V 1200 mAh"` |
| `gasArt` | nein | `Green Gas`, `Red Gas`, `Black Gas`, `CO2`. Standard bei GBB: `Green Gas` |
| `hopUp` | nein | Freitext, z. B. `"Gummi 60°, Hop-up 3/4"` |
| `zubehoer` | nein | Liste, z. B. `["Magazin", "Rotpunktvisier"]` |
| `notizen` | nein | Freitext |
| `foto` | nein | Pfad im Repository (z. B. `"fotos/cm16-raider.jpg"`) oder vollständige `https://`-Adresse |

Die Mündungsenergie berechnet die App selbst aus `fps` und `bbGewicht`.

## Fotos

Lege Bilder im Ordner `fotos/` ab und trage den Pfad im Feld `foto` ein. Die App lädt das Bild,
wenn jemand das Modell auswählt, verkleinert es auf 1400 px und speichert es auf dem Gerät.
Ein Foto, das der Nutzer schon hinterlegt hat, wird nie überschrieben.

Verwende nur Bilder, an denen du die Nutzungsrechte hast: eigene Fotos oder ausdrücklich
freigegebene Herstellerbilder. Dieses Repository ist öffentlich.
Maximal 8 MB pro Bild, nur `https`.

Einträge mit unbekanntem `typ` oder fehlenden Feldern überspringt die App.
Ist die ganze Datei kaputt oder leer, behält die App den bisherigen Katalog.
Setze `aktualisiert` bei jeder Änderung auf das aktuelle Datum.

## Spielfelder (`spielfelder.json`)

Die App lädt zusätzlich `spielfelder.json`. Im Missions-Formular öffnet das Listen-Symbol neben dem
Spielfeld eine Auswahl mit Suche: oben die bisher genutzten Spielfelder, darunter dieser Katalog.
Wer ein Feld nicht findet, tippt den Namen direkt ein.

```json
{
  "version": 1,
  "aktualisiert": "2026-11-20",
  "spielfelder": [
    { "name": "Beispielfeld", "ort": "50667 Köln", "art": "Wald", "website": "https://example.org" }
  ]
}
```

| Feld | Pflicht | Bedeutung |
|---|---|---|
| `name` | ja | wird als Spielfeld in die Mission übernommen |
| `ort` | nein | z. B. PLZ und Stadt, erscheint unter dem Namen |
| `art` | nein | z. B. `Wald`, `CQB`, `Gebäude`, `Gemischt` |
| `website` | nein | für spätere Verwendung |

Die Liste darf leer sein. Einträge ohne `name` überspringt die App, eine kaputte Datei lässt den
bisherigen Stand stehen. Trage nur Felder ein, deren Angaben du geprüft hast: Das Repository ist öffentlich.
