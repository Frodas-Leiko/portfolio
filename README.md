# Portfolio

Statische Portfolio-Website mit Tools.

## Struktur

```
/
├── index.html              Landingpage
├── projects.html           Projektübersicht
├── about.html              Über mich
│
├── /tools/                 Standalone-Tools (eigenes CSS möglich)
│   └── skp-trainer.html
│
├── /assets/
│   ├── /css/main.css       Single source of truth — alle Tokens, Komponenten
│   ├── /js/                Globales JS (falls benötigt)
│   └── /img/
│
└── README.md
```

## Design-System

Alle Design-Entscheidungen leben in `assets/css/main.css`:

- **Schriften**: Fraunces (Serif) für Aussagen, JetBrains Mono für Funktionales
- **Farben**: dunkler Hintergrund, warm-cremiger Text, Goldgelb als Akzent
- **Spacing**: 4px-Raster (`--s-1` bis `--s-8`)
- **Komponenten**: `.card`, `.card-link`, `.btn`, `.chip`, `.input`, `.tag`, `.label`

Neue Seiten verwenden das vorhandene Vokabular — keine Stile erfinden.

## Lokal entwickeln

Einfach `index.html` im Browser öffnen, oder im Projektverzeichnis:

```bash
python -m http.server 8000
```

Dann auf dem Handy `http://localhost:8000` aufrufen.

## Deploy

GitHub Pages: in den Repo-Settings unter "Pages" den `main`-Branch und Root-Verzeichnis auswählen.
