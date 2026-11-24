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
| `fps` | nein | Richtwert mit 0,20-g-BBs als Ganzzahl. Ohne Angabe bleibt FPS in der App offen (0) und du trägst es selbst ein |
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
    {
      "name": "Beispielfeld",
      "ort": "Musterstraße 1, 50667 Köln",
      "art": "Wald",
      "website": "https://example.org",
      "logo": "logos/beispielfeld.png",
      "beschreibung": "Waldfeld mit Dorf und Bunkeranlage, rund 4 ha.",
      "regeln": ["Maximal 1,0 Joule", "Schutzbrille Pflicht", "Keine Pyrotechnik"],
      "preise": [{ "titel": "Tageskarte", "preis": "25 €" }, { "titel": "Leihausrüstung", "preis": "15 €" }],
      "karte": "karten/beispielfeld.jpg",
      "lat": 50.9375,
      "lon": 6.9603
    }
  ]
}
```

| Feld | Pflicht | Bedeutung |
|---|---|---|
| `name` | ja | wird als Spielfeld in die Mission übernommen |
| `ort` | nein | z. B. PLZ und Stadt, erscheint unter dem Namen |
| `art` | nein | z. B. `Wald`, `CQB`, `Gebäude`, `Gemischt` |
| `website` | nein | `https`-Adresse, erscheint als Knopf „Website“ |
| `logo` | nein | Logo für die Spielfeld-Übersicht: Pfad im Repository (z. B. `"logos/mr-airsoft.png"`) oder `https`-Adresse, max. 8 MB. Ohne Logo zeigt die App ein Karten-Symbol |
| `beschreibung` | nein | Kurzvorstellung, erscheint in der Liste und im Steckbrief |
| `regeln` | nein | Liste mit Regeln, je Eintrag ein Punkt |
| `preise` | nein | Liste aus `titel` und `preis` (beides Text) |
| `karte` | nein | Taktikkarte als Bild: Pfad im Repository (z. B. `"karten/beispielfeld.jpg"`) oder `https`-Adresse, max. 8 MB |
| `lat`, `lon` | nein | Koordinaten für die Navigation. Ohne Angabe nutzt die App `ort` als Adresse |

Unter **Mehr → Spielfelder** zeigt die App jedes Spielfeld als Steckbrief. Was nicht ausgefüllt ist, wird ausgeblendet.
Der Knopf „Navigation“ öffnet die Routenplanung der Karten-App mit dem Spielfeld als Ziel.

Die Liste darf leer sein. Einträge ohne `name` überspringt die App, eine kaputte Datei lässt den
bisherigen Stand stehen. Trage nur Felder ein, deren Angaben du geprüft hast: Das Repository ist öffentlich.
