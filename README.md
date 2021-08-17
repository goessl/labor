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
 - [Anmerkungen](#anmerkungen)
 - [Danksagung & hilfreiche Links](#danksagung---hilfreiche-links)
 - [Lizenz (MIT)](#lizenz--mit-)

Fertige Protokolle, welche mit dieser Vorlage gefertigt wurden sind auf [https://www.student.tugraz.at/goessl/](https://www.student.tugraz.at/goessl/) einsehbar.


## Verwendung/Vorbereitung
Es wird checklistenmäßig aufgezählt, wie dieses Template an die verschiedenen Autoren und Experimente angepasst wird um einheitlich gleiche Protokolle zu erhalten.

### Deckblatt
Das Deckblatt kann auch händisch ausgefüllt und dem Protokoll beigelegt werden. Bei den durch Corona bedingten Onlineabgaben ist es jedoch meist effizienter die Datei am PC zu bearbeiten.
Es sind die Deckblätter für das Labor 1 & 2 als `.doc` oder `.pdf` in dem Unterordner `cover` enthalten.
 1. Übungstitel: Titel laut Rotationsschema eintragen. Z.B. `TU1: Dünne Linsen`
 2. Betreuer: Im Online-Verzeichnis ([TeachCenter](tc.tugraz.at) & [Moodle](moodle.uni-graz.at)) gibt es meist eine Datei mit den Betreuern der jeweiligen Experimente. Bei Unsicherheit in der Einheit nach dem Namen fragen. In den Onlinesystemen (online.tugraz.at & online.uni-graz.at) kann man in der Personensuche die vollständigen Titel herausfinden. Z.B. `Mag. Dipl.-Ing. Dr. Max Mustermann, BSc MSc PhD`
 3. Gruppennummer laut Rotationsschema. Z.B. `4`
 4. Namen der Gruppenmitglieder in alphabetischer Reihenfolge inklusive Kennzeichnung des Schriftführers. Sollte es keinen einzelnen Schriftführer geben, ist die Bezeichnung wegzulassen. Z.B.
    ```
    Sebastian Gössl (Schriftführer)
    Max Mustermann
    ```
 5. Kennzahl des Studiums. In den Onlinesystemen unter `Mein Studium > Meine Studien anzeigen` einsehbar. Z.B. `UF 033 678` (Physik-Bachelor 2017-Curriculum)
 6. Matrikelnummer der Gruppenmitglieder in der gleichen Reihenfolge der Namen. Z.B.
    ```
    12345678
    90123456
    ```
 8. Datum des Tages an welchem das Experiment durchgeführt wurde. Z.B. `12.04.2021`
 9. Semester, nur mehr das Jahr eintragen. Wird das Deckblatt elektronisch ausgefüllt, is bei Möglichkeit eine Umänderung zum Format `YY[W/S]S` zu empfehlen, da dieses Format kürzer, leserlich und beim Dateimanagment nützlicher ist.

### main.tex
 1. Für den Titel wird das Format `Labor [N] - [Experimentname]`, wie z.B. `Labor 2 - TU1: Dünne Linsen` um mit dem Titelblatt einheitlich zu bleiben, empfohlen.
 2. Autor ist der Schriftführer, im Format `[Vor- und Nachname] - [Matrikelnummer]`
 Sollten sich Autor und Titel in der Kopfzeile überlappen oder mehrere Gruppenmitglieder Schriftführer sein, soll eine zweizeilige Kopfzeile verwendet werden: `Labor [N] - \\ [Experimentname]` und `[Vor- und Nachname 1] - [Matrikelnummer 1] \\ [Vor- und Nachname 2] - [Matrikelnummer 2]`
Bei mehrzeiliger Kopfzeile muss die `headheight` des Packages `geometry` beim Importieren von `15pt` auf `28pt` erhöht werden.
 3. Datum wie am Deckblatt.
 4. Das richtige Deckblatt muss mit `\includepdf{cover/Deckblatt}` eingefügt werden. Dazu ist schlicht der Suffix `1` oder `2` anzuhängen so dass die richtige Datei verwendet wird. Voreingestellt ist Labor `1`.
 5. Da zum Zeitpunkt des Verfassens dieser Vorlage noch immer eine viele Labore im Onlinemodus geführt werden, ist das Kapitel `Anmerkung` standardmäßig in der Vorlage enthalten. Dieses beschreibt dass das Experiment nur per Video untersucht wurde und die Grundlagen aus den Unterlagen übernommen wurde. Dieses Kapitel ist entsprechend den aktuellen Ausführungen anzupassen/zu entfernen.

### Design Patterns
Hier noch kurz die empfohlenen Design Patterns für die grundlegenden Bausteine eines Protokolls:

#### Text & Mathematik
Text ohne spezielle Effekte, maximal um wichtige Ausdrücke herauszuheben `\emph{}` verwenden.
Mathematische Ausdrücke im Fließtext mit `$` einklammern. Einzeilige Rechnungen in der Umgebung `equation`, mehrzeilige im `gather` oder `align` (oder  `gather` mit eingebettetem `aligned` falls zwischendurch zentrierte Zeilen benötigt werden).
Nur Rechnungen zu welchen referenziert wird sind zu numerieren, meist nur manche im Abschnitt Grundlagen. Angewandte Rechnungen sind nicht zu numerieren (mit `*` Suffix, z.B. `equation*`).
Bei angewandten Rechnungen sind diese als Formel in eine Zeile zu schreiben, und darunter die erhaltenen Werte. Wenige Ergebnisse können in eine Zeile mit `\qquad` getrennt geschrieben werden.
Bei der Formeln hat die Unsicherheitsberechnung direkt gleichzeitig zu geschehen und die Quellen von errechneten Werten hat immer unmittelbar nachvollziehbar sein, z.B
```
Aus den Messwerten kann durch die folgende Formel
(umgeformte Glg. \ref{eq:gleichung}) das Ergebnis
ermittelt werden.
\begin{gather*}
    c = a + b \qquad \Delta c = \Delta a + \Delta b \\
    c = \SI{25+-2}{\m}
\end{gather*}
```

#### Werte
Einheiten in `\si{}` (z.B. `\si{\m}` für Meter). Werte mit Einheiten in `\SI{}{}` (z.B. `\SI{2,0+-0,1}{\m}` für zwei Meter). Als Dezimalzeichen ist das Komma eingestellt.
Unsicherheiten immer mit `+-` zum Wert dazu.
Oft gebrauchte, jedoch nicht standardmäßig implementierte Einheiten wie `VA` (Voltampere), `var` (Voltampere Reaktiv), `U` (Umdrehungen), usw., wurden bereits hinzugefügt. Ansonsten mit `\DeclareSIUnit\code{Text}` hinzufügen, nachdem die [siunitx-Dokumentation](ctan.org/pkg/siunitx) durchsucht wurde, ob die gesuchte Einheit nicht bereits vorhanden ist.
Einheitenlose Werte in `\num{}`.

#### Bilder
Bilder sind in eine zentrierte `figure` einzubetten. Diese ist in den meisten Fällen als Float `H` am besten positioniert (Bild wird genau an dieser Stelle im Text und nirgendwo anders eingefügt).
Die Breite ist nur bei Bedarf zu verändern. Z.B. `width=0.5\linewidth`.
Der Dateiname ist ohne Endung zu verwenden, da damit bei größeren Projekten niedrig aufgelöste Bilder für schnelle Vorschauen und hochaufgelöste Bilder für engültige Ergebnisse verwendet werden können. 
Beschreibungen sind bei allen Grafiken zu verwenden.
Labels sind nur bei später auch referenzierten Grafiken, mit `\ref{}` zu verwenden.
```
\begin{figure}[H]
    \centering
    \includegraphics[width=\linewidth]{fileWithoutExtension}
    \caption{Beschreibung}
    \label{fig:name}
\end{figure}
```
Bei mehreren Grafiken nebeneinander sind `subfigure`s in `minipage`s zu verwenden.

#### Tabellen
Tabellen sind, ähnlich wie Grafiken, in einem Float `H` `table`, welcher mit einer `caption` und bei Bedarf einem `label` versehen wurde, einzubetten. Die Zellen sind in einem `tabular`, mit `|`s und `\hbar`s einfach umrandet und einer abgetrennten Kopfzeile, einzutragen.
Für Spalten mit Werten ist das mit `siunix` bereitgestellte `s` (für kommaausgerichtete Zahlen).
Kopfzeilen sind den Universität-Richtlinen nach im Format `{$x \ / \si{\u}$}` zu halten (`{}` damit der Mathemodus `$$` in `s`-Spalten funktioniert).
Bei so gut wie allen Tabellen ist in der Beschreibung auf die Quelle zu referenzieren, z.B. `ausgerechnete Konstanten lt. Glg. \ref{eq:formel} mit den Werten aus Tab. \ref{tab:tabelle}`, und im Fließtext auf den Eintrag in die Tabelle zu verweisen, z.B. `anschließend werden die Konstanten mithilfe von Glg. \ref{eq:formel} und den Messwerten aus Tab. \ref{tab:messw} ausgerechnet und in Tab. \ref{tab:erg} eingetragen`.
```
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
```

### Bibliography
Zitieren mit `\cite{}` z.B. `$F=\SI{2.0+-0.5}{\N}$ lt. \cite{boege} Tab 23.11`.
Die TeachCenter-Kurse & Moodle-Kurse sind ebenfalls bereits in der Bibliography enthalten, jedoch ist der Link zu aktualisieren, da jedes Semester ein neuer Kurs und damit eine neue Adresse angelegt wird.

In der Bibliography-Datei wurden bereits mehrere möglicherweise nützliche Bücher eingetragen. Unter anderem die in Experimentalphysik 1 & 2 bereitsgestellten Demtröder, die Wiley-Custom-Version von Krane's Modern Physics und mehrere HTL-Bücher, welche sehr oft nützliche Vergleichswerte enthalten. Es wurden immer die bereitsgestellten Versionen/Jahre verwendet (Demtröder als PDF, manche HTL Bücher als Softcover), außer neuere Editionen sind zugänglich, was fast bei allen Springer Büchern über die TU der Fall ist.
Bei Springer kann man den `.bib`-Eintrag von Büchern downloaden (ein Kapitel auswählen, dann `Cite chapter`>`.bib` und die kapitelspezifischen Felder rauslöschen), weshalb bei diesen Einträgen meist redundante Informationen vorhanden sind (z.B. doi & doi-url). Diese wurden jedoch belassen so dass der Autor nur die Felder, welche er nicht inkludiert haben möchte löschen, und nicht die fehlenden ergänzen muss.

## Anmerkungen
 - Da dies meist falsch gemacht wird, ist besonders auf richtiges Runden zu achten.
 - Protokolle sind im Präsenz (Gegenwart) zu verfassen.
 - In den Universitätsunterlagen wird meist die Reihenfolge `Vorname Nachname` verwendet, weshalb diese übernommen wurde.
 - Da das Protkollieren insgesamt viel Zeit in Anspruch nimmt, wurde hier eher auf Effizienz beim Schreiben als auf Best-practice-Implementierungen geachtet (z.B. wurden schlicht alle möglicherweise relevanten Packages inkludiert).
 - Als Sprache für dieses Readme wurde Deutsch, der Lehrveranstaltung entsprechend, gewählt, so dass dies jeder Besucher der Lehrveranstaltung auch verstehen kann. Im Projekt selber (Dateinamen, Kommentare, etc.) wird jedoch, gleich wie die Befehle in Latex, Englisch verwendet.
 - Der Autor hat sich Latex mit verschiedenen Quellen selbst beigebracht und ist ein Amateur, weshalb hier nicht trotz aller Bemühungen von hochwertigem Latex auszugehen ist.

## Danksagung & hilfreiche Links
Diese Vorlage wurde hauptsächlich auf Overleaf mithilfe dessen
[sehr nützlichen Dokumentation](https://www.overleaf.com/learn), in welcher schnell und übersichtliche Erklärungen gefunden werden können, entwickelt.

Für ausführlichere und genauere Angaben sind die Dokumentationen der Packages auf [ctan.org](ctan.org) zu verwenden.

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
