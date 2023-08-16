# NAK Transferleistungs LaTeX-Template
Ein LaTeX-Template für Transferleistungen der Nordakademie.

## Installation und Abhängigkeiten 
### Docker
Docker installieren: https://docs.docker.com/desktop/

Und nachdem die Docker Engine läuft, das Projekt einfach in einem Container neu bauen.

### Lokal
Nutz einfach Docker...

Aber das Projekt basiert auf der VS Code Erweiterung [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop), einfach den Anweisungen in [Installation and basic settings](https://github.com/James-Yu/LaTeX-Workshop/wiki/Install) folgen.

Als Backend wird latexmk verwendet, da es am besten mit der Erweiterung implementiert ist. Weitere Installationsschritte für das Projekt sind in `.devcontainer/Dockerfile` zu finden.

### Erweitern von TexLive

#### Pakete

Wenn packages fehlen, können diese mit den entsprechenden Paketen unter https://packages.ubuntu.com/focal/texlive-full noch der Dockerfile (oder manuell) hinzugefügt.

## Entwickeln mit dem Template

### Navigieren des Projekts

```
Transferleistungstemplate
├── .devcontainer/              // Docker
│   ├── devcontainer.json
│   └── Dockerfile
├── .vscode /                   // für lokales Entwickeln
│   └── settings.json
├── assets/                     // Grafiken und Tabellen
├── build/                      // Output
├── src/
│   ├── internal/                  // Präambel
│   │   ├── acronyms.tex              // Abkürzungen
│   │   ├── bibliography.bib          // Bibliographie
│   │   ├── config.tex                // Formattierungen
│   │   └── packages.tex              // Pakete
│   ├── sections/                  // eigentliches Dokument
│   └── main.tex                   // main file
├── .gitignore
├── env.tex                     // Paramter
└── README.md
```

#### Schriftarten

Alle TexLive eigenen Schriftarten können unter der folgenen Liste gefunden werden: https://tug.org/FontCatalogue/

In der Liste wird auch die Einbindung der Schriftarten beschrieben

Der ausgewählte Font ist aber die Schriftart der NAK Dokumente

# Kurzreferenz

Dokumentiert wird wie folgt:

```
\befehl{<variable>} -> output
```

## Abkürzungen
Für Abkürzungen wird `acro` verwendet, mehr information dazu gibt es in der [Dokumentation](https://github.com/cgnieder/acro/blob/master/doc/acro-manual.pdf).

<span style="color:LightCoral">❗`\printacronyms` funktioniert nicht immer beim ersten durchlauf, das Dokument muss ggf. mehrmals gebaut werden!</span>

### Abkürzungen erstellen

Abkürzungen werden in der folgenden Datei abgelegt:

```
transferleistungs_template/src/internal/acronyms.tex
```

Eine Abkürzung wird wie folgt angelegt (in der Dokumentation gibt noch weitere Parameter, die aber optional sind):

```latex
\DeclareAcronym{<id>}{
    short = <short>,
    long = <long>
}
```

### Abkürzungen im Text verwenden

```latex
\ac{<id>} -> <long> (<short>)
```
```latex
\acs{<id>} -> <short>
```
```latex
\acl{<id>} -> <long>
```

## Anhang

PDF unter folgendem Pfad ablegen:

```
transferleistungs_template/assets
```

Anhang mit folgendem custom Befehl können Anhänge hinzugefügt werden:

```latex
\addAppendix{<tile>}{<filename>}
```