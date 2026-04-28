# MCServer1523 Homepage

Homepage für einen Minecraft-Server mit statischem Frontend.

Das Frontend nutzt:

- `Tailwind CSS` per CDN
- `Lucide Icons` per CDN
- lokale Speicherung für Theme, aktive Seite und Sidebar-Reihenfolge
- Live-Status über die `mcstatus.io` API
- News-Feed mit Markdown-Unterstützung über einen separaten JSON-/Medien-Server auf Port `9339`

## Funktionen

- Sidebar im ChessHub-Stil
- Seiten für `Home`, `News`, `Map`, `Regeln` und `Modpack`
- Einstellungen als Popup
- Admin-Login im Einstellungsfenster
- Admin-Panel zum Erstellen, Bearbeiten und Löschen von News-Posts
- Mobile Navigation
- Live-Anzeige für:
  - Serverstatus
  - Online-Spieler
  - MOTD
  - Server-Icon
- Fallback auf `assets/pack.png`, wenn der Server offline ist
- Modpack-Download über `assets/modpack.mrpack`
- Mod-Liste aus einem Modrinth-`.mrpack`, falls vorhanden
- Upload von Bildern und Videos für News-Posts

## Projektstruktur

```text
.
├── index.html
├── README.md
└── assets/
```

## Deployment mit GitHub Pages

Da die Seite rein statisch ist, reicht es aus, das Repository auf GitHub hochzuladen und GitHub Pages für den Branch mit `index.html` zu aktivieren.

Typischer Ablauf:

1. Repository auf GitHub pushen
2. In GitHub unter `Settings -> Pages` den Branch auswählen
3. Root-Verzeichnis deployen

## Lokal testen

Das Frontend kann direkt im Browser geöffnet werden. Für realistischeres Verhalten mit Fetch/Assets ist ein lokaler Webserver besser, zum Beispiel:

```bash
python3 -m http.server 8000
```

Dann:

```text
http://localhost:8000
```

## Wichtige Anpassungen

Die wichtigsten Frontend-Konstanten stehen in `index.html`:

- Server-IP: `SERVER_IP`
- Server-Port: `SERVER_PORT`
- Pack-Icon: `PACK_ICON`
- Modpack-Datei: `MODPACK_URL`
- News-API: `NEWS_API_ORIGIN`

Aktuell verwendet die Seite:

- Server: `mcserver1523.duckdns.org`
- Port: `25565`

## Hinweise

- Ein echter roher TCP-Portscan ist in einer normalen GitHub-Pages-Seite im Browser nicht möglich.
- Der Serverstatus wird deshalb über `https://api.mcstatus.io/v2/status/java/...` geladen.
- Die aktuelle Modpack-Datei `assets/modpack.mrpack` bildet den Stand `v1.4.0` ab.
- Wenn `assets/modpack.mrpack` kein lesbares Modrinth-Pack ist, zeigt die Modpack-Seite einen Fallback-Hinweis.
- Der News-Feed erwartet eine API auf Port `9339`.
