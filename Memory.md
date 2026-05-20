# Projekt: Kinofilme-CH

> Persönliche Übersichts-Website für Kinostarts in der Schweiz – läuft als Single-File-PWA, gehostet auf GitHub Pages.

**Start:** 2026-05-20
**Status:** in Entwicklung – lokale Bauphase

---

## Ziel

Eine Website, auf der JB sieht, welche Filme aktuell im Schweizer Kino laufen und welche in den nächsten 6 Monaten starten. Lokal auf Windows 11 erreichbar (per Datei) und später öffentlich über GitHub Pages.

## Entscheidungen (festgelegt am 2026-05-20)

| Thema | Entscheidung | Begründung |
|---|---|---|
| Datenquelle | TMDB-API (v3) | Gratis, automatisch aktuell, CH-Region-Filter möglich |
| Region | Schweiz (`region=CH`) | Primärmarkt für JB |
| Zeitraum | Aktuell im Kino + nächste 6 Monate | Zwei Sektionen nebeneinander |
| Funktionen | Trailer (YouTube), Suche, Filter, Watchlist | Watchlist via localStorage |
| Hosting | GitHub Pages (öffentliches Repo) | Gratis, von überall erreichbar |
| API-Key-Speicherung | localStorage (Browser-seitig) | Repo bleibt sauber, Key nicht im Code |
| Designsystem | Apple Dark Mode (DeepMind 04_design_system.md) | Konsequente Linie mit allen JB-Projekten |

## Technische Eckpunkte

- **Stack:** Single-File `index.html` mit Vanilla JS, kein Framework
- **TMDB-Endpunkte:**
  - `/movie/now_playing?region=CH&language=de-DE` für aktuelle Filme
  - `/movie/upcoming?region=CH&language=de-DE` für kommende
  - `/discover/movie?primary_release_date.gte=...&primary_release_date.lte=...&region=CH` für 6-Monats-Range
  - `/movie/{id}` für Details
  - `/movie/{id}/videos` für Trailer
- **Bilder:** `https://image.tmdb.org/t/p/w500/{poster_path}`
- **Cache:** localStorage mit 6-Stunden-TTL, Key `kinofilme_v1_cache`
- **Watchlist-Key:** `kinofilme_v1_watchlist`
- **API-Key-Storage:** `kinofilme_v1_tmdb_key`

## Apple-Dark-Mode-Tokens (aus Designsystem)

- bg: #000000, bg2: #1C1C1E, bg3: #2C2C2E
- l1: #FFFFFF, l2: #A1A1A6, l3: #3A3A3C
- Akzente: blue #0A84FF, green #30D158, orange #FF9F0A, red #FF453A
- Cards: radius 16px, padding 16-20px
- Font: -apple-system, BlinkMacSystemFont, SF Pro Display

## Offene Punkte

- [ ] GitHub-Repo-Name festlegen (Vorschlag: `kinofilme-ch`)
- [ ] GitHub Pages aktivieren nach Push
- [ ] Eventuell zweite Sprache (it/fr) für mehrsprachige CH-Regionen – aktuell nur Deutsch

## Änderungs-Log

- **2026-05-20:** Projekt gestartet, Anforderungen geklärt (Klärungsfragen via AskUserQuestion), TMDB-Key beschafft, Architektur festgelegt.
