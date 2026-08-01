# Music – Offline PWA

Offline-fähiger Musik-Player als Progressive Web App. Läuft nach dem ersten Öffnen vollständig ohne Internetverbindung.

## Dateien im Repository

```
/
├── index.html          ← Die komplette App
├── manifest.json       ← PWA-Konfiguration (Name, Icon, Farbe)
├── sw.js               ← Service Worker (Offline-Cache)
├── App_Music_Icon.png  ← App-Icon (512×512 px, schwarz mit Musiknote)
└── README.md
```

---

## Deployment auf GitHub Pages

1. Repository auf GitHub erstellen
2. Alle Dateien in den `main`-Branch pushen
3. **Settings → Pages**
4. Source: **Deploy from a branch**, Branch: **main**, Ordner: **/ (root)**
5. **Save**

Die App ist dann erreichbar unter:
```
https://DEIN-USERNAME.github.io/REPO-NAME/
```

---

## Musik laden

### Option 1 – Einzelne Dateien
Auf **„+ Musik laden"** tippen und Audiodateien auswählen.

Dateinamen-Format für automatische Metadaten:
```
Titelname_Künstler_Album.mp3
```

### Option 2 – Ordner laden (empfohlen)
Auf **📁** tippen und einen Musik-Ordner auswählen. Die App liest die Ordnerstruktur aus:

```
MeinMusik/
  AC_DC/                        ← Künstlername
    Back_in_Black/              ← Albumname
      cover.jpg                 ← Album-Cover (optional)
      Hells_Bells.mp3
      Back_in_Black.mp3
    Highway_to_Hell/
      Cover/                    ← Cover-Unterordner geht auch
        cover.jpg
      Songs/                    ← Songs-Unterordner geht auch
        Song1.mp3
  Beatles/
    Abbey_Road/
      cover.jpg
      Come_Together.mp3
```

- Unterordner namens `Songs`, `Cover`, `Covers` werden transparent ignoriert
- Bilder direkt im Künstler-Ordner → Künstler-Cover
- Bilder im Album-Ordner oder dessen `Cover/`-Unterordner → Album-Cover

---

## Backup

Das Backup enthält **nur Playlists, Cover und Einstellungen** — keine Audiodaten.

**Exportieren:** Einstellungen → Backup exportieren → im Musik-Ordner speichern  
**Automatischer Import:** `Music_Backup.json` einfach in den Musik-Ordner legen. Beim nächsten Ordner-Import wird es automatisch erkannt und angewendet.  
**Manueller Import:** Einstellungen → Backup importieren (nur die JSON-Datei nötig, Musik muss bereits geladen sein)

---

## Funktionen

- **Titelliste** mit drei Tabs: Alle Titel · Künstler · Playlists
- **Künstler-Browser:** Künstler → Alben → Titel, je mit eigenem Cover
- **Playlists:** erstellen, sortieren (Drag & Drop), Titel hinzufügen/entfernen
- **Sperrbildschirm:** Vor-/Zurückskippen, Song-Scrubbing per Fortschrittsbalken
- **Wiedergabe-History:** Zurück-Taste spielt immer den tatsächlich zuletzt gespielten Titel
- **EQ / Song-Tuner:** Bass, Mitten, Höhen anpassen, Live-Vorschau, Export als .m4a
- **Shuffle & Repeat**
- **Nur mit Kopfhörern** – optionale Wiedergabesperre

---

## Als App installieren

- **iOS/iPadOS:** Safari → Teilen-Symbol → *Zum Home-Bildschirm*
- **Android:** Chrome → Drei-Punkte-Menü → *App installieren*
- **Desktop (Chrome/Edge):** Adressleiste → Install-Symbol

---

## Offline-Funktion

- Erster Besuch (muss online sein): Service Worker cached die App-Shell
- Alle weiteren Besuche: App startet sofort aus dem Cache, auch ohne WLAN
- Audiodaten werden in IndexedDB des Browsers gespeichert

## Lizenz

MIT License — Copyright (c) 2026
