# NAK Transferleistungs LaTeX-Template <!-- omit in toc -->

Ein Template für die Transferleistungen an der Nordakademie.

## Inhalt <!-- omit in toc -->

- [Kurzreferenz](#kurzreferenz)
  - [Simple Textformatierung](#simple-textformatierung)
    - [Fettgedruckt](#fettgedruckt)
    - [Kursiv](#kursiv)
    - [Unterstrichen](#unterstrichen)
  - [Abkürzungen](#abkürzungen)
    - [Erstellen](#erstellen)
    - [Im Text verwenden](#im-text-verwenden)
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
    - [Subfigures](#subfigures)
    - [Grafiken Referenzieren](#grafiken-referenzieren)
  - [Tabellen](#tabellen)
  - [Listen](#listen)
    - [Befehl](#befehl)
    - [Listensymbol ändern](#listensymbol-ändern)

# Kurzreferenz

Die Kurzreferenz ist eine Sammlung an Informationen, die ich regelmäßig gebraucht habe und hier abgelegt habe damit sie nicht immer neu recherchiert werden müssen, wenn man nach ein paar Monaten sie wieder vergessen hat. Das hier gezeigte ist auch teilweise in den Beispiel-Dateien bzw. -Code zu finden.

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

## Anhänge

Anhänge werden unter `/assets/appendix` abgelegt. Anhänge können dann mit folgendem Custom Befehl hinzugefügt werden:

```latex
\addAppendix{<tile>}{<filename>}
```

FYI der Befehl ist in `/src/internal/config.tex` zu finden.

## Bibliografie

Weiter schnelle Informationen über [BibLaTeX](https://www.ctan.org/pkg/biblatex) sind [hier](https://en.wikibooks.org/wiki/LaTeX/Bibliography_Management#biblatex) zu finden.

> Wenn zwei Attribute von einander mit einem `/` getrennt sind (z. B. `year/date = {},`) muss sich für eins entschieden werden.

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
  year/date = {},

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
  year/date={},

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
}
```

#### Online

Dieser Eingabetyp ist für reine Onlinequellen wie Websites gedacht.
Zu beachten ist, dass alle Eingabetypen das url-Feld unterstützen. Zum Beispiel, beim Zitieren eines Artikels aus einer Zeitschrift, die online verfügbar ist, ist der @article-Typ und dessen url-Feld zu verweden.

```bibtex
@online{<id>,
  % plficht
  author/editor = {},
  title = {},
  year/date = {},
  doi/eprint/url = {},

  % optional
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
  urldate = {},
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
  year/date = {},

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

### Im Dokument verwenden

```latex
\begin{figure}[H] % Grafik soll hier im Text stehen.
  \centering
  \includegraphics[width=.8\linewidth]{<graphics name>} % importiere Grafik
  \caption{<caption text>} % Bildbeschreibung
  \label{<label>} % das lable um auf die Grafik zu referieren
\end{figure}
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
