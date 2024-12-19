# NAK Transferleistungs LaTeX-Template <!-- omit in toc -->

Ein Template für die Transferleistungen an der Nordakademie, basierend auf der [Visual Studio Code](https://code.visualstudio.com/) Erweiterung [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)

## Inhalt

- [Inhalt](#inhalt)
- [Voraussetzungen](#voraussetzungen)
- [Nutzung](#nutzung)
- [Simple Textformatierung](#simple-textformatierung)
  - [Fettgedruckt](#fettgedruckt)
  - [Kursiv](#kursiv)
  - [Unterstrichen](#unterstrichen)
  - [Inline Code ohne Syntax-Highlighting](#inline-code-ohne-syntax-highlighting)
- [Abkürzungen](#abkürzungen)
  - [Erstellen](#erstellen)
  - [Im Text verwenden](#im-text-verwenden)
- [Cross referencing](#cross-referencing)
  - [Usage](#usage)
    - [Vollständiges Label](#vollständiges-label)
  - [Label Abkürzungen Tabelle](#label-abkürzungen-tabelle)
- [Anhänge](#anhänge)
- [Bibliografie](#bibliografie)
  - [Quelle hinzufügen](#quelle-hinzufügen)
    - [Book](#book)
    - [Article](#article)
    - [Online](#online)
    - [Misc (Interne Quellen/Präsentationen)](#misc-interne-quellenpräsentationen)
  - [Zitieren](#zitieren)
    - [indirektes Zitieren](#indirektes-zitieren)
    - [direkte Zitate](#direkte-zitate)
- [ChkTeX](#chktex)
  - [Unterdrücken von Warnungen](#unterdrücken-von-warnungen)
- [Grafiken](#grafiken)
  - [Im Dokument verwenden](#im-dokument-verwenden)
    - [Bild trimmen](#bild-trimmen)
  - [Subfigures](#subfigures)
  - [Textwrapping](#textwrapping)
  - [Grafiken Referenzieren](#grafiken-referenzieren)
- [Tabellen](#tabellen)
- [Listen](#listen)
  - [Befehl](#befehl)
  - [Listensymbol ändern](#listensymbol-ändern)
- [Code](#code)
  - [Verwendung](#verwendung)
    - [Codeblöcke als Listing](#codeblöcke-als-listing)
    - [Code innerhalb einer Zeile](#code-innerhalb-einer-zeile)
  - [Anpassungen](#anpassungen)
    - [Quelltextverzeichnis](#quelltextverzeichnis)
    - [Quelltextüberschrift](#quelltextüberschrift)
    - [Syntax-Highlighting](#syntax-highlighting)
    - [Codeblock](#codeblock)
    - [Zeilennummerierung der Codeblöcke](#zeilennummerierung-der-codeblöcke)

# Anleitung

## Voraussetzungen

- [Visual Studio Code](https://code.visualstudio.com/) installieren.
- Die [Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack) Erweiterung für Visual Studio Code installieren (das kann in VSC unter dem "Extensions" Tab erfolgen).
- [Docker](https://docs.docker.com/get-docker/) installieren (FYI man benötigt keinen Account).

## Nutzung

1. Docker starten, die Docker Engine muss im Hintergrund laufen.
2. Visual Studio Code öffnen und den Ordner fürs Template öffnen.
   1. Ganz unten links auf den Button "Open a Remote Window" klicken.
   2. Oben die Option "Reopen in Container" anklicken.

# Kurzreferenz

Die Kurzreferenz ist eine Sammlung an Informationen, die ich regelmäßig gebraucht und hier abgelegt habe, damit ich sie nicht immer neu recherchieren muss, wenn man nach ein paar Monaten sie wieder vergessen hat. Das hier gezeigte ist auch teilweise in den Beispiel-Dateien bzw. -Code zu finden.

## Simple Textformatierung

### Fettgedruckt

Das ist ein Beispiel für **fettgedruckt**.

```latex
\textbf{<text>}
```

### Kursiv

Das ist ein Beispiel für *kursiv*.

```latex
\textit{<text>}
```

### Unterstrichen

Das ist ein Beispiel für <u>Unterstrichen</u>.

```latex
\underline{<text>}
```

### Inline Code ohne Syntax-Highlighting

Das ist ein Beispiel für `monospace`

```tex
\texttt{<text>}
```

## Abkürzungen

Für Abkürzungen wird das Paket `acro` verwendet, mehr Information dazu gibt es in der [Dokumentation](https://github.com/cgnieder/acro/blob/master/doc/acro-manual.pdf).

>❗`\printacronyms` funktioniert nicht immer beim ersten durchlauf, das Dokument muss ggf. mehrmals gebaut werden!

### Erstellen

Abkürzungen werden in der folgenden Datei abgelegt:

```dir
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

## Cross referencing

### Usage

#### Vollständiges Label

```tex
\cref{}
```

> Wird durch das Paket `hyperref` ermöglicht

### Label Abkürzungen Tabelle

| label | type |
| --- | --- |
| ch  | chapter |
| sec |  section |
| subsec |  subsection |
| fig |  figure |
| tab |  table |
| eq | equation |
| lst |  code listing |
| itm |  enumerated list item |
| alg |  algorithm |
| app |  appendix subsection |

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

#### Book

Ein Einzelstück, ein Buch mit einem oder mehreren Autoren, wo die Autoren alle
zusammen gearbeitet haben.

```bibtex
@book{<id>,
  % pflicht
  author = {},
  title = {},
  date = {},

  % optional
  editor = {},
  editora = {},
  editorb = {},
  editorc = {},
  translator = {},
  annotator = {},
  commentator = {},
  introduction = {},
  foreword = {},
  afterword = {},
  subtitle = {},
  titleaddon = {},
  maintitle = {},
  mainsubtitle = {},
  maintitleaddon = {},
  language = {},
  origlanguage = {},
  volume = {},
  part = {},
  edition = {},
  volumes = {},
  series  = {},
  number = {},
  note = {},
  publisher = {},
  location = {},
  isbn = {},
  eid = {},
  chapter = {},
  pages = {},
  pagetotal = {},
  addendum = {},
  pubstate = {},
  doi = {},
  eprint = {},
  eprintclass = {},
  eprinttype = {},
  url = {},
  urldate = {},
  year = {},
}
```

#### Article

Ein Artikel in einem Journal, einer Zeitschrift, einer Zeitung oder einem anderem
Periodikum, welches einen eigenen Abschnitt mit einem eigenen Titel erhält.

> Die Datenfelder sind gleich zu `@book` mit dem Unterschied, dass `journaltitle={}` ein Pflichtfeld ist.

```bibtex
@article{<id>,
  % pflicht
  author={},
  title={},
  journaltitle={},
  date={},

  % optional
  editor = {},
  editora = {},
  editorb = {},
  editorc = {},
  translator = {},
  annotator = {},
  commentator = {},
  introduction = {},
  foreword = {},
  afterword = {},
  subtitle = {},
  titleaddon = {},
  maintitle = {},
  mainsubtitle = {},
  maintitleaddon = {},
  language = {},
  origlanguage = {},
  volume = {},
  part = {},
  edition = {},
  volumes = {},
  series  = {},
  number = {},
  note = {},
  publisher = {},
  location = {},
  isbn = {},
  eid = {},
  chapter = {},
  pages = {},
  pagetotal = {},
  addendum = {},
  pubstate = {},
  doi = {},
  eprint = {},
  eprintclass = {},
  eprinttype = {},
  url = {},
  urldate = {},
  year = {},
}
```

#### Online

Dieser Eingabetyp ist für reine Onlinequellen wie Websites gedacht.
Zu beachten ist, dass alle Eingabetypen das url-Feld unterstützen. Zum Beispiel, beim Zitieren eines Artikels aus einer Zeitschrift, die online verfügbar ist, ist der @article-Typ und dessen url-Feld zu verweden.

```bibtex
@online{<id>,
  % plficht
  author = {},
  title = {},
  date = {},
  url = {},
  urldate = {},

  % optional
  doi = {},
  eprint = {},
  editor = {},
  subtitle = {},
  titleaddon = {},
  language = {},
  version = {},
  note = {},
  organization = {},
  month = {},
  addendum = {},
  pubstate = {},
  eprintclass = {},
  eprinttype = {},
  year = {},
}
```

#### Misc (Interne Quellen/Präsentationen)

Eine Fallbacklösung für Quellen, die sonst in keine Kategorie passen. Das Feld
`howpublished` kann hilfreich sein für eine Klarifizierung wo die Quelle herkommt.
Ein Augenmerk sei auch auf `type` zu legen um zu klären, was die Quelle überhaupt
darstellt.

Es sollte auch `unpublished` erwähnt werden, jedoch fehlt da das `organization` Feld, welches jedoch bei internen Quellen benötigt wird.

```latex
@misc{<id>,
  % pflicht
  author/editor = {},
  title = {},
  date = {},

  % optional
  subtitle = {},
  titleaddon = {},
  language = {},
  howpublished = {},
  type = {},
  version = {},
  note = {},
  organization = {},
  location = {},
  month = {},
  addendum = {},
  pubstate = {},
  doi = {},
  eprint = {},
  eprintclass = {},
  eprinttype = {},
  url = {},
  urldate = {}
}
```

### Zitieren

#### indirektes Zitieren

Im Gegensatz zu `\cite` sind bei `\parencite` die Klammern vorhanden

```latex
\parencite{<id>}
```

```latex
\parencite[vgl.][<seite>]{<id>}
```

#### direkte Zitate

Direkte Zitate sollten zwar möglichst vermieden werden, jedoch sind sie ab und zu
nötig oder nützlich. Das Paket `csqoutes` bietet eine große Auswahl an Möglichkeiten. Mit dem folgenden Befehl wird eine ansehnliche weise des Zitierens verwendet, welche sich aus dem Text hervorhebt.

(Die Klammern werden schon von der Umgebung `displayquotes` gesetzt, daher kann `\cite` verwendet werden.)

```latex
\begin{displayquote}[\cite{<bibid>}]
    \emph{<text>}
\end{displayquote}
```

## ChkTeX

### Unterdrücken von Warnungen

Pro Zeile:

```latex
% chktex <cktex_warning_number>
```

Mehrere Warnungen in einer Zeile (für jede Warnung muss mit einem neuen chktex angekündigt werden):

```latex
% chktex <cktex_warning_number> chktex <cktex_warning_number>
```

Für das ganze Projekt können Regeln in der `.chktexrc` unterdrückt werden mit:

```txt
-n<cktex_warning_number>
```

Zum Beispiel

```txt
-n44
# 44: User Regex: -2:Use \toprule, midrule, or \bottomrule from booktabs.
# Because: booktabs my have a better handeling of tables but the difference in linethickness is very offputting with smaller tables and \hline is sufficient.
```

> Ein Kommentar um welche Regel es sich handelt und warum sie deaktiviert ist kann hier sehr hilfreich sein!

## Grafiken

Grafiken werden in `/assets/images/` abgelegt.

| Verfügbare Dateiformate |
| --- |
| .png .jpg .pdf |

### Im Dokument verwenden

```latex
\begin{figure}[H] % Grafik soll hier im Text stehen.
  \centering
  \includegraphics[width=.8\linewidth]{<graphics name>} % importiere Grafik
  \caption{<caption text>} % Bildbeschreibung
  \label{<label>} % das lable um auf die Grafik zu referieren
\end{figure}
```

#### Bild trimmen

Anstelle von `\includegraphics[]{}` verwenden:

```latex
\adjincludegraphics[%
  width=\linewidth,
  trim={{.125\width} 0 {.125\width} 0},
  % <left> <lower> <right> <upper>
  clip%
]{<file name>}
```

### Subfigures

```latex
\begin{figure}[H]
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

### Textwrapping

>❗Wenn es keinen Text gibt, der die Grafik einschließt beeinflusst die Grafik die Überschriften des Dokuments auf unkontrollierbare Weise!

| location | Description |
| --- | --- |
| r  R | right side of the text |
| l  L |  left side of the text |
| i  I |  inside edge–near the binding (in a twoside document) |
| o  O |  outside edge–far from the binding |

```latex
\begin{wrapfigure}{<location>}{.3\textwidth}
  \centering
  \includegraphics[width=.8\linewidth]{<file name>}
  \def\captionValue{<caption>}
  \caption[\captionValue]{\captionValue{} <reference>}
  \label{<label>}
\end{wrapfigure}
```

### Grafiken Referenzieren

```latex
\ref{fig:<label>}
```

## Tabellen

TBD

## Listen

### Befehl

```Latex
\begin{itemize}
    \item Item 1
    \item Item 2
    \item Item 3
\end{itemize}
```

### Listensymbol ändern

```Latex
\renewcommand{\labelitemi}{<symbol>}
```

## Code

Codeblöcke werden mit dem Paket [minted](https://www.ctan.org/tex-archive/macros/latex/contrib/minted/) realisiert.

### Verwendung

#### Codeblöcke als Listing

```latex
\begin{listing}[H]
    \begin{minted}{c} % sprache festlegen (hier c)
        int main() {
            // print hello world
            printf("hello, world!");
            return 0;
        }
    \end{minted}
    \caption{Hello world in C}
    \label{lst:listing}
\end{listing}
```

#### Code innerhalb einer Zeile

```latex
\mintinline{c}|int i = 1|.
```

### Anpassungen

#### Quelltextverzeichnis

Festgelegt in `src/transferleinstung/transferleistung.tex`

```latex
% list of code
\renewcommand{\headingValue}{Quelltext}
\renewcommand\listoflistingscaption{\headingValue} % Name ändern (original List of Listings)
\listoflistings
\addcontentsline{toc}{section}{\headingValue}
\newpage
```

#### Quelltextüberschrift

Festgelegt in `config/config.tex`

```latex
\renewcommand{\listingscaption}{Quelltext}
```

#### Syntax-Highlighting

Festgelegt in `config/config.tex`

```latex
\usemintedstyle{vs}
```

#### Codeblock

Festgelegt in `config/config.tex`

```latex
\setminted{%
    autogobble,
    linenos, % enable line numbers
    % numbers = left, % default none
    % numbes is essentially the same as linenos exceot the side can be specified
    tabsize = 4 % default 8
}
```

#### Zeilennummerierung der Codeblöcke

Festgelegt in `config/config.tex`

Muss separat über das Makro `\theFancyVerbLine` angepasst werden.

```latex
\renewcommand{\theFancyVerbLine}{%
    \textcolor{gray}{%
        \ttfamily
        \scriptsize
        \oldstylenums{\arabic{FancyVerbLine}}
    }
}
```
