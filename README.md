# Portfolio

Statische Portfolio-Website mit Tools. Kein Framework, kein Backend —
alles läuft client-seitig, alle Daten bleiben im localStorage des Nutzers.

## Struktur

```
/
├── index.html                       Landingpage mit Tool-Grid
├── projects.html                    Projektübersicht (Detailliste)
├── about.html                       Über mich · Kontakt · Impressum
│
├── /tools/                          Standalone-Tools (eigenes inline CSS)
│   ├── skp-trainer.html             Karteikarten — Sachkundeprüfung § 34a GewO
│   ├── uzwgbw-trainer.html          Karteikarten — UZwGBw
│   ├── waffg-trainer.html           Karten & Quiz — Waffengesetz
│   ├── russisch-trainer.html        Vokabeln & Alphabet — Russisch
│   ├── multi-timer.html             Intervall-Timer mit Workout-Presets
│   └── arbeitszeiterfassung.html    Stunden, Strecken & Spesen
│
├── /assets/
│   ├── /css/main.css                Single source of truth — alle Tokens, Komponenten
│   ├── /js/                         Globales JS (falls benötigt)
│   └── /img/
│
└── README.md
```

## Konventionen

- **Dateinamen**: kleingeschrieben, Bindestriche (`waffg-trainer.html`)
- **localStorage-Keys**: `toolname_version` (z. B. `skp_trainer_v1`) —
  localStorage ist pro Origin geteilt, daher eindeutige Präfixe
- **Tools sind eigenständig**: jedes Tool ist eine einzelne HTML-Datei mit
  eigenem inline CSS und bleibt ohne die Website lauffähig. Einzige
  Verbindung zur Site: der Zurück-Button (`← `, oben links) führt
  per relativem Link auf `../index.html`
- **Site-Seiten** (index, projects, about) ziehen ihr komplettes Styling
  aus `assets/css/main.css` — dort keine Stile duplizieren

## Design-System

Alle Design-Entscheidungen leben in `assets/css/main.css`:

- **Schriften**: Fraunces (Serif) für Aussagen, JetBrains Mono für Funktionales
- **Farben**: dunkler Hintergrund, warm-cremiger Text, Goldgelb als Akzent
- **Spacing**: 4px-Raster (`--s-1` bis `--s-8`)
- **Komponenten**: `.card`, `.card-link`, `.btn`, `.chip`, `.input`, `.tag`, `.label`

Neue Seiten verwenden das vorhandene Vokabular — keine Stile erfinden.
Ausnahme: die Arbeitszeiterfassung hat bewusst ein eigenes, helles Design.

## Neues Tool hinzufügen

1. HTML-Datei nach `/tools/` legen (Namensschema beachten)
2. Zurück-Button in den Tool-Header einbauen (Link auf `../index.html`)
3. Karte in `index.html` ergänzen (`.card-link` im Grid)
4. Eintrag in `projects.html` ergänzen (`.list-plain`-Item)
5. README-Strukturbaum aktualisieren

## Offene Punkte für den Produktivbetrieb

- [ ] Impressum in `about.html` mit echten Angaben füllen (Platzhalter markiert)

## Lokal entwickeln

Einfach `index.html` im Browser öffnen, oder im Projektverzeichnis:

```bash
python -m http.server 8000
```

Dann auf dem Handy `http://localhost:8000` aufrufen.

## Deploy

GitHub Pages: in den Repo-Settings unter "Pages" den `main`-Branch und
Root-Verzeichnis auswählen.

**Hinweis nach diesem Update:** `Russisch_Trainer.html` wurde zu
`russisch-trainer.html` umbenannt. Alte Datei nach dem Übernehmen löschen,
gespeicherte Lernstände bleiben erhalten (localStorage hängt an der Domain,
nicht am Dateinamen).
