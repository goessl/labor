# Labor Vorlage

Dies ist eine Latex-Vorlage für die Labore des Physik-Bachelors an der TU Graz & KF Graz.
 - [Verwendung/Vorbereitung](#verwendung-vorbereitung)
     - [Deckblatt](#deckblatt)
     - [main.tex](#maintex)
     - [Design Patterns](#design-patterns)
         - [Text & Mathematik](#text---mathematik)
         - [Werte](#werte)
         - [Bilder](#bilder)
         - [Tabellen](#tabellen)
     - [Bibliography](#bibliography)
 - [Entscheidungen & Begründungen, Anmerkungen](#entscheidungen---begründungen--anmerkungen)
 - [Danksagung & hilfreiche Links](#danksagung---hilfreiche-links)
 - [Lizenz (MIT)](#lizenz--mit-)

Fertige Protokolle, welche mit dieser Vorlage gefertigt wurden sind auf [https://www.student.tugraz.at/goessl/](https://www.student.tugraz.at/goessl/) einsehbar.


## Verwendung/Vorbereitung

Es wird checklistenmäßig aufgezählt, wie dieses Template an die verschiedenen Autoren und Experimente angepasst wird um einheitlich gleiche Protokolle zu erhalten.

### Deckblatt

Das Deckblatt kann auch händisch ausgefüllt und dem Protokoll beigelegt werden. Bei den durch Corona bedingten Onlineabgaben ist es jedoch meist effizienter die Datei am PC zu bearbeiten.
Es sind die Deckblätter für das Labor 1 & 2 als `.doc` oder `.pdf` in dem Unterordner [cover](cover/) enthalten. Das passende, ausgefüllte Deckblatt sollte in das Hauptverzeichnis gezogen werden, dessen `1`- oder `2`-Suffix entfernt werden und der verbleibende Ordner gelöscht werden.
 1. Übungstitel: Titel laut Rotationsschema eintragen; z.B. `TU1: Dünne Linsen`.
 2. Betreuer: Im Online-Verzeichnis ([TeachCenter](tc.tugraz.at) & [Moodle](moodle.uni-graz.at)) gibt es meist eine Datei mit den Betreuern der jeweiligen Experimente. Bei Unsicherheit in der Einheit nach dem Namen fragen. In den Onlinesystemen (online.tugraz.at & online.uni-graz.at) kann man notfalls versuchen mit der Personensuche den vollständigen Namen herauszufinden. Der Name ist ohne Titel anzugeben; z.B. `Gössl, Sebastian`
 3. Gruppennummer laut Rotationsschema; z.B. `4`
 4. Namen der Gruppenmitglieder in alphabetischer Reihenfolge inklusive Kennzeichnung des Schriftführers. Sollte es keinen einzelnen Schriftführer geben, ist die Bezeichnung wegzulassen; z.B.
        Angermann, Leo
        Gössl, Sebastian (Schriftführer)
 6. Kennzahl des Studiums. In den Onlinesystemen unter `Mein Studium > Meine Studien anzeigen` einsehbar; z.B. `UF 033 678` (Physik-Bachelor 2017-Curriculum)
 7. Matrikelnummer der Gruppenmitglieder in der gleichen Reihenfolge der Namen; z.B.
        12345678
        90123456
 8. Datum des Tages, an welchem das Experiment durchgeführt wurde, im österreichisch gewöhnten `DD.MM.YYYY`-Format.
 9. Semester im Format `YYSS`.

### main.tex

 1. Für den Titel wird das Format `Labor [N] \\ [Experimentname]`, wie z.B. `Labor 2 \\ TU1: Dünne Linsen` um mit dem Titelblatt einheitlich zu bleiben, empfohlen.
 2. Autor ist die Gruppe mit den Namen der Gruppenteilnehmer, im Format `Gruppe [N] \\ [Nachname] \& [Nachname]`.
Sollte nur der Schriftführer als Autor erwünscht sein, ist eben nur dieser als `Gruppe [N] \\ [Nachname]` anzuführen.
 4. Datum als `YYSS \\ DD.MM.YYYY`.
Sollte die Kopfzeile einzeilig möglich sein (normalerweise nicht möglich da sich der Text überlappen würde), ist dies zu nutzen indem die Zeilenumbrüche durch einen Bindestrich ersetzt werden und die `headheight` des Packages `geometry` beim Importieren von `28pt` auf `15pt` verringert wird. 
 6. Das richtige Deckblatt muss mit `\includepdf{Deckblatt}` eingefügt werden.
 7. Da zum Zeitpunkt des Verfassens dieser Vorlage noch immer eine viele Labore im Onlinemodus geführt werden, ist das Kapitel `Anmerkung` standardmäßig in der Vorlage enthalten. Es folgen die Standardfloskeln für ein Videolabor und eine Hintereinanderausführung:
    > Dies ist ein 3rd-Hand Protokoll. Das Experiment wurde nicht vom Autor durchgeführt, sondern hat dieser eine Videoaufzeichnung \cite{teachcenter} vom Experiment protokolliert. Weiters stammen das Titelblatt (vom Autor ausgefüllt) und die ersten drei Kapitel (inhaltlich) ebenfalls aus diesem Verzeichnis.

    > Aufgrund der herrschenden COVID-19-Maßnahmen, wurde die Laborübung nicht von beiden Gruppenmitglieder gleichzeitig durchgeführt, sondern zuerst von Angermann, Leo und anschließend erneut von Gössl, Sebastian. Beide führten alle Aufgaben vollständig durch und werteten ihre jeweiligen Daten, über gleiche Rechenwege, getrennt aus. Wird nur ein Ergebnis angegeben, is es nur dies des Schriftführers (Zwischenergebnis \& Diagramme, zu besseren Übersicht), ansonsten werden die jeweiligen Ergebnise der Laboranten nebeneinander angeführt, so dass diese verglichen werden können.

### Design Patterns

Hier noch kurz die empfohlenen Design Patterns für die grundlegenden Bausteine eines Protokolls:

#### Text & Mathematik

Text ohne spezielle Effekte, maximal um wichtige Ausdrücke herauszuheben `\emph{}` verwenden.

Mathematische Ausdrücke im Fließtext mit `$` einklammern. Einzeilige Rechnungen in der Umgebung `equation`, mehrzeilige im `gather` oder wenn nötig `align` (oder `gather` mit eingebettetem `aligned` falls in den ausgerichteten Rechnungen zentrierte Zeilen benötigt werden).

Nur Gleichungen zu welchen referenziert wird sind zu numerieren, meist sind dies nur manche im Abschnitt Grundlagen. Angewandte Rechnungen sind nicht zu numerieren (mit `*` Suffix, z.B. `equation*`).

Bei angewandten Rechnungen sind diese als Formel in eine Zeile zu schreiben, und darunter die erhaltenen Werte. Wenige Ergebnisse können in eine Zeile mit `\qquad` getrennt geschrieben werden.

Wird im Math-Mode Text benötigt, wird `\text{}` verwendet.

Bei der Formeln hat die Unsicherheitsberechnung direkt gleichzeitig zu geschehen und die Quellen von errechneten Werten hat immer unmittelbar nachvollziehbar sein, z.B

    Mit der gemessenen Spannung $U$ und Strom $I$ aus Tab. \ref{tab:messwerte} wird mithilfe von Glg. \ref{eq:ohm} der gesuchte Widerstand $R$ berechnet:
    \begin{gather*}
        R = \frac{U}{I} \qquad \Delta R = R \left( \frac{\Delta U}{U} + \frac{\Delta I}{I} \right) \\
        R = \SI{25+-2}{\ohm}
    \end{gather*}

#### Werte

Einheiten in `\si{}` (z.B. `\si{\m}` für Meter). Werte mit Einheiten in `\SI{}{}` (z.B. `\SI{2,0+-0,1}{\m}` für zwei Meter). Als Dezimalzeichen ist das Komma eingestellt.

Unsicherheiten immer absolut mit `+-` zum Wert dazu angeben.

Oft gebrauchte, jedoch nicht standardmäßig implementierte Einheiten wie `VA` (Voltampere), `var` (Voltampere Reaktiv), `U` (Umdrehungen), usw., wurden bereits hinzugefügt. Ansonsten mit `\DeclareSIUnit\code{Text}` hinzufügen, nachdem die [siunitx-Dokumentation](ctan.org/pkg/siunitx) durchsucht wurde, ob die gesuchte Einheit nicht bereits vorhanden ist.

Einheitenlose Werte in `\num{}`.

#### Bilder

Bilder sind in eine zentrierte `figure` einzubetten. Diese ist in den meisten Fällen als Float `H` am besten positioniert (Bild wird genau an dieser Stelle im Text und nirgendwo anders eingefügt).

Die Breite ist nur bei Bedarf zu verändern; z.B. `width=0.5\linewidth`.

Der Dateiname ist ohne Endung zu verwenden, da damit bei größeren Projekten niedrig aufgelöste Bilder für schnelle Vorschauen und hochaufgelöste Bilder für engültige Ergebnisse verwendet werden können. 

Beschreibungen sind bei allen Grafiken zu verwenden.

Labels sind nur bei später auch referenzierten Grafiken, mit `\ref{}` zu verwenden.

    \begin{figure}[H]
        \centering
        \includegraphics[width=\linewidth]{fileWithoutExtension}
        \caption{Beschreibung}
        \label{fig:name}
    \end{figure}

Bei mehreren Grafiken nebeneinander sind `subfigure`s in `minipage`s zu verwenden.

#### Tabellen

Tabellen sind, ähnlich wie Grafiken, in einem Float `H` `table`, welcher mit einer `caption` und bei Bedarf einem `label` versehen wurde, einzubetten. Die Zellen sind in einem `tabular`, mit `|`s und `\hbar`s einfach umrandet und einer abgetrennten Kopfzeile, einzutragen.

Für Spalten mit mathematischen Ausdrücken sind die links, zentriert und rechts ausgerichteten Makros `L C R` bereits implementiert, für Spalten mit Werten ist das mit `siunix` bereitgestellte `s` (für kommaausgerichtete Zahlen).

Kopfzeilen sind den Universität-Richtlinen nach im Format `{$x \ / \si{\u}$}` zu halten (`{}` damit der Mathemodus `$$` in `s`-Spalten funktioniert).

Bei so gut wie allen Tabellen ist in der Beschreibung auf die Quelle zu referenzieren, z.B. `ausgerechnete Konstanten lt. Glg. \ref{eq:formel} mit den Werten aus Tab. \ref{tab:tabelle}`, und im Fließtext auf den Eintrag in die Tabelle zu verweisen, z.B. `anschließend werden die Konstanten mithilfe von Glg. \ref{eq:formel} und den Messwerten aus Tab. \ref{tab:messw} ausgerechnet und in Tab. \ref{tab:erg} eingetragen`.

    \begin{table}[H]
        \centering
        \caption{Beschreibung}
        \label{tab:name}
        \begin{tabular}{| l | *{1}{S|}}
            \hline
            Nr.    & {$x \ / \ \si{u}$} \\
            \hline
            1      & 1,0 \\
            \hline
        \end{tabular}
    \end{table}

### Bibliography

Zitieren mit `\cite{}` z.B. `$F=\SI{2.0+-0.5}{\N}$ lt. \cite{boege} Tab 23.11`.

Die TeachCenter-Kurse & Moodle-Kurse sind ebenfalls bereits in der Bibliography enthalten, jedoch ist der Link zu aktualisieren, da jedes Semester ein neuer Kurs und damit eine neue Adresse angelegt wird.

In der Bibliography-Datei wurden bereits mehrere möglicherweise nützliche Bücher eingetragen. Unter anderem die in Experimentalphysik 1 & 2 bereitsgestellten Demtröder, die Wiley-Custom-Version von Krane's Modern Physics und mehrere HTL-Bücher, welche sehr oft nützliche Vergleichswerte enthalten. Es wurden immer die bereitsgestellten Versionen/Jahre verwendet (Demtröder als PDF, manche HTL Bücher als Softcover), außer neuere Editionen sind zugänglich, was fast bei allen Springer Büchern über die TU der Fall ist.

Bei Springer kann man den `.bib`-Eintrag von Büchern downloaden (ein Kapitel auswählen, dann `Cite chapter > .bib` und die kapitelspezifischen Felder rauslöschen), weshalb bei diesen Einträgen meist redundante Informationen vorhanden sind (z.B. doi & doi-url). Diese wurden jedoch belassen so dass der Autor nur die Felder, welche er nicht inkludiert haben möchte löschen, und nicht die fehlenden ergänzen muss.

## Entscheidungen & Begründungen, Anmerkungen

 - Das Semester sollte generell immer als `YYSS`, z.B. `21WS` angegeben werden, da dieses Format kürzer, trotzdem gut leserlich und beim Dateimanagment nützlicher ist. Daten im üblichen `DD.MM.YYYY`, Uhrzeiten in 24h-Format `hh:mm`.
 - Namen werden den [Regeln für die alphabetische Katalogisierung](https://de.wikipedia.org/wiki/Regeln_f%C3%BCr_die_alphabetische_Katalogisierung) entsprechend im Format `Nachname, Vorname` (bei Spezialfällen, wie `Peter von der Mühll > Mühll, Peter von der` bei Anahme der deutschen Sprache als Herkunft lt. §314a, ist auf die Regeln zu achten). Titulaturen sind nicht anzusetzten (§326 in der 2. Auflage, 2006). Dies verbessert die Orientierung in Listen, Vereinfacht das Lesen, erfordert weniger Nachbesserungen und wirkt dem in Österreich herschenden Titelfetischismus entgegen.


 - Protokolle sind im Präsenz (Gegenwart) zu verfassen.
 - Da dies meist falsch gemacht wird, ist besonders auf richtiges Runden zu achten.
 - Da das Protkollieren insgesamt viel Zeit in Anspruch nimmt, wurde hier eher auf Effizienz beim Schreiben als auf Best-practice-Implementierungen geachtet (z.B. wurden schlicht alle möglicherweise relevanten Packages inkludiert).
 - Als Sprache für dieses Readme wurde Deutsch, der Lehrveranstaltung entsprechend, gewählt, so dass dies jeder Besucher der Lehrveranstaltung auch verstehen und an eigenen Projekten anwenden kann. Im Projekt selber (Dateinamen, Kommentare, etc.) wird jedoch, gleich wie die Befehle in Latex, Englisch verwendet.
 - Der Autor hat sich Latex mit verschiedenen Quellen selbst beigebracht und ist ein Amateur, weshalb hier nicht trotz aller Bemühungen von hochwertigem Latex auszugehen ist.

## Danksagung & hilfreiche Links

Der größte Dank geht an **Angermann, Leo**, welcher mit dem Autor zusammen als Gruppe die Einführungen und ersten beiden Laborlehrveranstaltungen besucht hat. Die zahlreichen Protokolle, durch welche diese Vorlage entstanden ist, wurden mit ihm gemeinsam verfasst. Ohne seine Hilfe wären solch ausgezeichnete Abgaben und auch Durchführungen nicht möglich gewesen.

Diese Vorlage wurde hauptsächlich auf Overleaf mithilfe dessen
[sehr nützlichen Dokumentation](https://www.overleaf.com/learn), in welcher schnell und übersichtliche Erklärungen gefunden werden können, entwickelt.

Für ausführlichere und genauere Angaben sind die Dokumentationen der Packages auf [ctan.org](https://ctan.org/) zu verwenden.

## Lizenz (MIT)

MIT License

Copyright (c) 2021 Sebastian Gössl

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
