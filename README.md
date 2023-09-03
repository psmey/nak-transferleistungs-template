# NAK Transferleistungs LaTeX-Template

Ein LaTeX-Template für Transferleistungen der Nordakademie.

### Inhalt <!-- omit in toc -->

- [NAK Transferleistungs LaTeX-Template](#nak-transferleistungs-latex-template)
  - [Installation und Abhängigkeiten](#installation-und-abhängigkeiten)
    - [Docker](#docker)
    - [Lokal](#lokal)
    - [VSC Erweiterungen](#vsc-erweiterungen)
  - [Entwickeln mit dem Template](#entwickeln-mit-dem-template)
    - [Navigieren des Projekts](#navigieren-des-projekts)
    - [Setup](#setup)
    - [Anpassung des Templates](#anpassung-des-templates)
      - [Erweitern von TexLive](#erweitern-von-texlive)
      - [Schriftarten](#schriftarten)
- [Kurzreferenz](#kurzreferenz)
  - [Abkürzungen](#abkürzungen)
    - [Erstellen](#erstellen)
    - [Im Text verwenden](#im-text-verwenden)
  - [Anhänge](#anhänge)
  - [Bibliografie](#bibliografie)
    - [Quelle hinzufügen](#quelle-hinzufügen)
      - [Article](#article)
      - [Book](#book)
      - [Online](#online)
    - [Zitieren](#zitieren)
  - [Grafiken](#grafiken)
    - [Im Dokument verwenden](#im-dokument-verwenden)
    - [Subfigures](#subfigures)
    - [Grafiken Referenzieren](#grafiken-referenzieren)
  - [Tabellen](#tabellen)


## Installation und Abhängigkeiten 

### Docker

Docker installieren: https://docs.docker.com/desktop/

Und nachdem die Docker Engine läuft, das Projekt einfach in einem Container neu bauen.

### Lokal

Nutz einfach Docker...

Aber das Projekt basiert auf der VS Code Erweiterung [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop), einfach den Anweisungen in [Installation and basic settings](https://github.com/James-Yu/LaTeX-Workshop/wiki/Install) folgen.

Als Backend wird latexmk verwendet, da es am besten mit [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) implementiert ist. Weitere Installationsschritte für das Projekt sind zur Not in `.devcontainer/Dockerfile` zu finden.

### VSC Erweiterungen

TBD

## Entwickeln mit dem Template

TBD

### Navigieren des Projekts

etwas out of date...

```
Transferleistungstemplate
├── .devcontainer/              // Docker
│   ├── devcontainer.json
│   └── Dockerfile
├── .vscode/                    // für lokales Entwickeln
│   └── settings.json
├── assets/
│   ├── appendix/               // Anhange wie PDFs
│   └── images/                     // Bilder
├── build/                          // Output
├── src/
│   ├── internal/                  // Präambel
│   │   ├── acronyms.tex              // Abkürzungen
│   │   ├── bibliography.bib          // Bibliographie
│   │   ├── config.tex                // Formattierungen
│   │   └── packages.tex              // Pakete
│   ├── sections/                  // eigentliches Dokument
│   └── main.tex                   // main file
├── .gitignore
├── env.tex                     // Paramters
└── README.md
```

### Setup


### Anpassung des Templates

#### Erweitern von TexLive

Wenn Pakete fehlen, können diese mit den entsprechenden Paketen unter https://packages.ubuntu.com/focal/texlive-full noch der Dockerfile (oder manuell) hinzugefügt.

#### Schriftarten

Alle TexLive eigenen Schriftarten können unter der folgenden Liste gefunden werden: https://tug.org/FontCatalogue/

In der Liste wird auch die Einbindung der Schriftarten beschrieben

Der ausgewählte Font ist aber die Schriftart der NAK Dokumente

# Kurzreferenz

Das hier gezeigte ist auch in den Beispiel-Dateien bzw. -Code zu finden.

## Abkürzungen
Für Abkürzungen wird das Paket `acro` verwendet, mehr Information dazu gibt es in der [Dokumentation](https://github.com/cgnieder/acro/blob/master/doc/acro-manual.pdf).

>❗`\printacronyms` funktioniert nicht immer beim ersten durchlauf, das Dokument muss ggf. mehrmals gebaut werden!

### Erstellen

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

### Im Text verwenden

```latex
\ac{<id>} % -> <long> (<short>)
```
```latex
\acs{<id>} % -> <short>
```
```latex
\acl{<id>} % -> <long>
```

## Anhänge

Anhänge werden unter `/assets/appendix` abgelegt. Anhänge können dann mit folgendem Custom Befehl hinzugefügt werden:

```latex
\addAppendix{<tile>}{<filename>}
```

FYI der Befehl ist in `/src/internal/config.tex` zu finden.

## Bibliografie

Weiter schnelle Informationen über [BibLaTeX](https://www.ctan.org/pkg/biblatex) sind [hier](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#biblatex) zu finden.

### Quelle hinzufügen

Quellen-Codeblöcke werden in die Datei `/src/internal/bibliography.bib` eingefügt.

#### Article

Ein Artikel in einem Journal, einer Zeitschrift, einer Zeitung oder einem anderem
Periodikum, welches einen eigenen Abschnitt mit einem eigenen Titel erhält. 

> Die Datenfelder sind gleich zu `@book` mit dem Unterschied, dass `journaltitle={}` ein Pflichtfeld ist.

```bibtex
@article{<id>,
     author={}, 
     title={}, 
     journaltitle={}, 
     year/date={},
}
```

#### Book

Ein Einzelstück, ein Buch mit einem oder mehreren Autoren, wo die Autoren alle
zusammen gearbeitet haben. 

```bibtex
@book{<id>,
  % pflicht
  title={}, 
  journaltitle={}, 
  year/date={},
  % optional 
  % (gekürzt auf die Relevanteren) 
  translator={}, 
  annotator={}, 
  commentator={},
  subtitle={},
  titleaddon={},
  language={}, 
  origlanguage={}, 
  series={},
  volume={}, 
  number={}, 
  eid={},
  version={}, 
  note={}, 
  issn={},
  doi={},
  url={},
  urldate={}
}
```

#### Online

Dieser Eingabetyp ist für reine Onlinequellen wie Websites gedacht.
Zu beachten ist, dass alle Eingabetypen das url-Feld unterstützen. Zum Beispiel, beim Zitieren eines Artikels aus einer Zeitschrift, die online verfügbar ist, ist der @article-Typ und dessen url-Feld zu verweden

```bibtex
@book{<id>,
  % pflicht
  author/editor={}, 
  title={}, 
  year/date={}, 
  url={},
  % optional
  subtitle={}, 
  titleaddon={}, 
  language={}, 
  version={}, 
  note={},
  organization={}, 
  date={}, 
  month={}, 
  year={}, 
  addendum={}, 
  pubstate={}, 
  urldate={}
}
```

### Zitieren

Im Gegensatz zu `\cite` sind bei `\parencite` die Klammern vorhanden

```latex
\parencite{<id>}
```

```latex
\parencite[vgl.][<seite>]{<id>}
```

## Grafiken

Grafiken werden in `/assets/images/` abgelegt.

### Im Dokument verwenden

```latex
\begin{figure}[h] % Grafik soll hier im Text stehen.
  \centering 
  \includegraphics[width=.8\linewidth]{<graphics name>} % importiere Grafik
  \caption{<caption text>} % Bildbeschreibung
  \label{<label>} % das lable um auf die Grafik zu referieren
\end{figure}
```

### Subfigures

```latex
\begin{figure}[h]
    \centering

    \begin{subfigure}{.4\textwidth}
        \centering
        \includegraphics[width=.8\linewidth]{<subfig filename 1>}
        \caption{<suvfig caption 1>}
        \label{<subfig label 1>}
    \end{subfigure}
    \begin{subfigure}{.4\textwidth}
        \centering
        \includegraphics[width=.8\linewidth]{<subfig filename 2>}
        \caption{<suvfig caption 2>}
        \label{<subfig label 2>}
    \end{subfigure}

    \caption{<caption>}
    \label{<fig label>}
\end{figure}
```

### Grafiken Referenzieren

```latex
\ref{fig:<label>}
```

## Tabellen

TBD
