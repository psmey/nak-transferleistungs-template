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

Geschriebene Inhalte gehören nach `transferleistungs_template/src/sections` werden in die `main.tex` importiert und arrangiert.

Externe Inhalte wie Grafiken und Anhänge werden in `transferleistungs_template/assets/` abgelegt.

### Navigieren des Projekts

```
Transferleistungstemplate
├── .devcontainer/              // Docker
│   ├── devcontainer.json   
│   └── Dockerfile  
├── .vscode /                   // for lokal development
│   └── settings.json
├── assets/                     // figures, images
├── build/                      // output
├── src/                        
│   ├── internal/               // preamble
│   │   ├── config.tex             // config like formats
│   │   └── packages.tex           // package imports
│   ├── sections/               // document files
│   └── main.tex                // main file
├── .gitignore  
├── bibliography.bib            // bibliography
├── env.tex                     // external parameters
└── README.md
```

#### Schriftarten

Alle TexLive eigenen Schriftarten können unter der folgenen Liste gefunden werden: https://tug.org/FontCatalogue/

In der Liste wird auch die Einbindung der Schriftarten beschrieben

Der ausgewählte Font ist aber die Schriftart der NAK Dokumente