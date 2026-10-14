# chiptune-data

Ergänzende Beispiele für die Chiptune-Bibliothek vom [@KChaot](http://github.com/kchaot) unter **[chiptune.kchaot.de](https://chiptune.kchaot.de)**:  
kleine 8-Bit-Stücke als Textdateien (multi-content markdown). Auch inspiriert von: [Markdown-Slides](https://gist.github.com/defautset/2db959b84fbc343995950470d45b78d1)

## Der Hintergrund

Chiptune ist ein Lernprojekt im Rahmen des [t1s.ch](https://t1s.ch). Aus dem Wunsch, ein paar DJ-Basics im Zusammenspiel mit Bits bzw. Beats & Bytes vermittelt zu bekommen, entstand eine Bibliothek, in der jeder „Song“ eine einfache Textdatei ist. Wer einen Song lesen kann, kann ihn ändern, und wer ihn ändern kann, kann einen eigenen schreiben.

## Wie ist das hier eingebunden?

Die oben genannte Chiptune-Seite holt sich u.a. dieses Repo als Quelle. In ihrer `etc/sources.json` steht dafür:

- Repo `ek9r/chiptune-data`, Branch `main`
- Ordner `kalkig/`, auf der Seite als Quelle **Kalkiges** mit dem Pfad `/kalkig/...`

Jeder Push auf `main` wird beim nächsten Build von der Seite berücksichtigt.  
Der Build läuft dort täglich sowie bei allen Änderungen am Code.  
Ein neuer Song von hier erscheint dort also nicht sofort.

## Inhalt

| Ordner                   | Inhalt |
|--------------------------|----------------------------------------------------------------------------|
| `kalkig/`                | Einzelne Songs („Projekt 0“, „Projekt 1“ (Layer))                          |
| `kalkig/beat-fuer-beat/` | Album zum Mitmachen: Schritt für Schritt, jeder Song fügt eine Sache hinzu |
| `kalkig/mixbausteine/`   | Album mit kurzen Loops zum Spielen mit dem Mixer                           |

Alben sind Unterordner.  
 Die optionale Datei `_album.md` darin legt Informationen wie Titel und Künstler fest sowie eine Beschreibung und Schlagworte ("Tags").

## Ein Song in Kürze:

Ein Song ist eine Markdown-Datei im experimentellen ["multi-content"-Format](https://github.com/tempestphp/markdown/issues/17).  
Oben steht ein Kopf mit Titel, Künstler und Tempo, darunter folgt je Spur (Track) ein Block:

````markdown
---
title: "02: Mein Song"
artist: Kalkie
bpm: 128
---
Ein Text zum Song, den man auf der Seite liest.

<!-- track: kick -->
---
instrument: drums
volume: 0.3
---
```grid
k . . . | k . . . | k . . . | k . . .
```

<!-- track: bass -->
---
instrument: saw
volume: 0.26
gate: 0.5
---
```grid
. . E2 . | . . E2 . | . . G2 . | . . D2 E2
```
````

- Jede Zeile im `grid` ist ein Takt aus 16 Schritten (vier Gruppen zu vier). Ein `.` ist eine Pause, `-` hält den Ton.
- Instrumente: `square`, `pulse`, `triangle`, `saw`, `sine` und `drums`. Die Drums kennen `k` (Kick), `s` (Snare), `c` (Clap), `h` (Hi-Hat) und `o` (offene Hi-Hat).
- Haben Spuren unterschiedlich viele Zeilen, wiederholen sie sich. So bleibt ein Song kurz, auch wenn ein Teil länger ist.
- In einer Spur können auch zusätzliche Textinformationen hinterlegt werden, wie hier: 

Wer weitere Beispiele sucht, findet sie z.B: im Album `beat-fuer-beat`:   
Die Songs bauen wie ein "Tutorial" aufeinander auf, jeder zeigt eine weitere Sache und ist beschrieben.
