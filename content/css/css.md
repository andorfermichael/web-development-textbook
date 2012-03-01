---
title: Geschichte der Cascading Style Sheets
order: 20
---
Von Anfang an sollte eine HTML-Datei keine Information darüber enthalten, wie der Text dargestellt werden soll - keine Schriftart oder Schriftgröße. HTML sollte nur strukturelle Information enthalten („das ist eine Überschrift“ aber nicht „Helvetica 24pt“). Die Formatierungs-Information sollte in sogenannten „Stylesheets“ gespeichert werden, das Format für die Stylesheets war aber noch nicht definiert. Im Jahre 1993 sah eine typische Webseite so aus

    <html><body>
    <h1>Das Studium</h1>
    <p>Studienziel ist es, breit gefächerte technische und kreative Kompetenzen...
    </body></html>

Da es keine Stylesheets gab „erfand“ Netscape ab 1994 zusätzliche HTML-Tags, die die Darstellung der Webseite festlegen. Andere Browser übernahmen diese Tags von Netscape. 

    <html><body>
    <h1><font face="Arial" color="blue">Das Studium</font></h1>
    <p><font size="+1">S</font>tudienziel ist es, breit gefächerte technische und kreative Kompetenzen...</p>
    <p><font size="+1">P</font>rojekte und Praxissemster stellen schon während des Studiums die Verbindung...</p>
    </body></html>

Durch das Hinzufügen der Tags für Formatierung wurde der HTML-Code komplizierter und unübersichtlicher. Erst ab ab 1995 wurde endlich an den Standards für Stylesheets gearbeitet, seit den frühen 2000ern ist die Unterstützung in den gängigen Browsern vorhanden. So sieht nun eine HTML-Seite mit separatem Stylesheet aus:

Die html-Datei

    <link rel="stylesheet"
          type="text/css"
          href="fh.css">
    </head><body>
    <h1>Das Studium</h1>
    <p>Studienziel ist es, breit gefächerte technische und wirtschaftliche Kompetenzen...
    </body></html>

Die Datei fh. css

    h1 { 
        font-family: Arial;
        color: blue; 
    }
    p:first-letter {

        font-size: large;
    }

Mit der Trennung von Stylesheet und HTML wurde HTML wieder einfacher und übersichtlicher. Besonders das nachträgliche Verändern der Gestaltung wurde vereinfacht. 
Wichtige Argumente für den Einsatz von Stylesheets sind:

* Zusätzliche Gestaltungsmöglichkeiten
* Einheitliche Gestaltung von mehreren Webseiten
* Arbeitsteilung zwischen DesignerInnen (die CSS erstellen) und RedakteuerInnen (die Inhalte erstellen)

Aber Achtung: CSS ist nicht die Lösung jedes Problems:

* Mit Stylesheets können Sie nur Elemente verändern, die schon in der HTML-Datei vorhanden sind. Es können keine neuen Elemente eingefügt werden. 
* Um ein Stylesheet zu erstellen, muss die DesignerIn die HTML-Tags kennen, z. B. wissen, dass h1, h2, h3 für die Überschriften stehen. 
* Damit das Stylesheet wirkt, muss die RedakteurIn, die das HTML-Dokument erstellt, die richtigen HTML-Tags verwenden, z. B. Überschriften wirklich mit h1, h2, h3 formatieren, und nicht mit b, i, font. 

Stylesheet Syntax
------------------

Beispiel

    h1,h2 {
      font-family: Arial, Helvetica, sans-serif;
      color: lightblue;
    }
    body {
      margin-left: 150px;
      background-color: white;
    } 
    p {
      text-align: justify;
    }

Eine Stylesheet-Regel („Rule“)  besteht aus einem Selektor gefolgt von einer geschwungenen Klammer die eine oder mehrere Deklarationen enthalten kann. 

Der einfachste Selektor besteht aus dem Namen eines einzelnen HTML-Tags. Sie können auch mehrere Elemente durch ein Komma trennen. In diesem Falle werden für alle Elemente die selben Style -Angaben definiert, (siehe h1,h2 in obigem Beispiel). 

Sie können beliebig Zeilenumbrüche einfügen, diese werden ignoriert. 

 Style für mehrere Seiten

Die Seiten einer gesamten Website haben meist ein einheitliches Aussehen. Dies können Sie erreichen, wenn Sie für jede Webseite dieselbe CSS Datei verwenden. Dazu müssen Sie in jede HTML-Datei die CSS Datei mittels folgender Anweisung einbinden:

<link rel="stylesheet" href="mystyle.css">
Diese Zeile sollte innerhalb des head Bereiches der HTML-Datei stehen (da sonst die Darstellung der Seite verzögert werden kann5). mysyle.css könnte etwa so aussehen wie im vorigen Beispiel. 

 Style für eine Seite

Wenn Sie einen Style  nur auf einer einzigen Webseite verwenden, können Sie die Style-Angaben direkt in die HTML-Datei schreiben, und zwar innerhalb des head Bereiches. 

    <style>
        h1,h2 {
          font-family: Arial, Helvetica, sans-serif;
          color: lightblue
        }
    </style>

 Style für einen Tag

Style Angaben können auch direkt in einen einzelnen HTML-Tag geschrieben werden. In diesem Fall gilt die Angabe nur für diesen ganz speziellen Tag. 

Um einen style für einen einzelnen Tag zu definieren, müssen Sie innerhalb des Tags das Attribut style verwenden. 

    <h1 style="color:red; text-align:center;">Rote, zentrierte Überschrift</h1>

 Gültigkeitsbereich einer Style Angabe

Sie können innerhalb einer HTML-Datei sowohl eine externe Style Sheet Datei verwenden (eingebunden durch eine entsprechende Anweisung im head Bereich) als auch eine lokale Definition im head Bereich angeben, als auch spezielle Angaben für einzelne Tags erstellen. 

Was passiert nun, wenn die verschiedenen Style-Deklarationen sich widersprechen? Die Angaben bei einem einzelnen Tag haben immer Vorrang. danach folgen die lokalen Angabe im head Bereich und erst zum Schluß die externe Datei. „Je näher beim Tag desto stärker wirkt es.“

Klassen, IDs, SPANs und DIVs
-----------------------------
Wenn Sie mit den Style-Angaben den p-Tag umformatieren, betrifft das alle p-Tags in der Webseite. Oft möchten Sie aber ein oder zwei Absätze anders formatieren als die anderen Absätze. Zu diesem Zweck können Sie sich im Stylesheet noch weitere Formatvorlagen - sogenannte "Klassen" - definieren:

    .wichtig { color: red; }

Diesen Klassen können Sie eigene Namen geben (hier „wichtig“), vor dem Klassennamen steht immer ein Punkt. Jedem normalen HTML-Tag können Sie nun diese Klasse zuweisen. Dies geschieht mit dem Attribut class. 

    <p>Eine <b class="wichtig">ganz wichtige</b> Meldung</p>
    <p class="wichtig">Ein ganz wichtiger Absatz</p>
    <p>Ein ganz normaler Absatz</p>

Zur „normalen“ Wirkung des HTML-Tags kommt nun die Formatierung durch die Klasse hinzu: der Text „ganz wichtige“ und „Ein ganz wichtiger Absatz“ ist in diesem Beispiel also rot. Eine Klasse kann also mehrmals in einem Dokument verwendet werden. Ein Tag kann mehrere Klassen erhalten, diese werden durch Leerzeichen getrennt im class-Attribut angeführt.

    <p class="wichtig eilmeldung">Ein wichtiger Absatz als Eilmeldung</p>

Zur eindeutigen Kennzeichnung von Tags wird das Attribut id verwendet:

    <p>Eine <b class="wichtig">ganz wichtige</b> Meldung</p>
    <p class="wichtig">Ein ganz wichtiger Absatz</p>
    <p id="impressum">Das einzige Impressum dieser Seite</p>

Auf diese eindeutigen IDs kann in CSS mit der Raute (englisch: „hash sign“) referenziert werden:

    #impressum { background-color: #DDD; }

Sowohl Klassen als auch IDs können mit Tags kombiniert werden um einen komplexen Selektor zu bilden, aber das macht nur bei Klassen wirklich Sinn:

    .wichtig { font-size: 20px; }     /* alle Tags mit der Klasse wichtig     */
    p.wichtig { color: red;    }     /* nur der Tag p mit der Klasse wichtig */

    b.wichtig { color: yellow; }    /* nur der Tag b mit der Klasse wichtig */

    #impressum { background-color:#ddd; }   /* nur der Tag mit der id #impressum */
    p#impressum { background-color:#ddd; } /* == nur der p-Tag mit der id #impressum */

    b#impressum { background-color:#ddd; }   /* nix! */

Die Firefox-Erweiterung Firebug zeigt Tags, Klassen und IDs in dieser Schreibweise an:

Es wird öfter vorkommen, dass Sie einem Bereich eine bestimmte Klasse zuweisen möchten, ohne dass ein passender Tag vorhanden ist. Hier können Sie die  beiden Tags &lt;span&gt; und &lt;div&gt; verwenden, die beide selber kaum Eigenschaft aufweisen. &lt;span&gt; eignet sich für die Verwendung in Fließtext, &lt;div&gt; ist ein blockbildender Tag.

    <p>Es gibt hier ganz <span class="wichtig">besonders interessante</span> Meldungen.</p>

Die Worte „besonders interessante“ erscheinen rot. 

Maßeinheiten in Stylesheets
-----------------------------

Für Längen- und Größen-Angaben gibt es mehrere Maßeinheiten: px (Pixel) , em (=Breite des Buchstaben M) , ex (Höhe des Buchstaben X),  % (Prozent), cm (Zentimeter), in (Inch).   Einige davon sind relativ (em = relativ zur Schriftgröße, px = relativ zur Pixel-Größe am aktuellen Ausgabemedium), andere absolut (Centimeter, Inch). Die absoluten Angaben kann man derzeit nur bei der Ausgabe auf Papier sinnvoll verwenden.

Farbangaben können auf mehrer Arten erfolgen: mit einigen Farbwörtern (red, green,…) oder mit der Angabe von rot-, grün- und blau-Anteil (jeweils werte von 0 bis 255) in verschiedenen Schreibweisen: Dezimal rgb(16,0,255), hexadezimal #10F oder zweistellig hexadezimal #1000FF. Mit CSS3 ist auch die Angabe eines Alpha-Wertes möglich: Hier ein Braun-Ton der nur zu 20% deckend ist, und zu 80% den darunter liegenden Content bzw. das Hintergrundbild durchscheinen lässt: rgba(153, 134, 117, 0.2);

Tool-Tipp: Mit dem Firefox AddOn Colorzilla kann man die Farben einer Webseite auslesen und in verschiedenen Schreibweisen kopieren:

![Abbildung 20: Colorzilla Pipette zum auslesen einer Farbe und Colorzilla Menü zum kopieren des Codes](/images/image073.png)

Wird in einem Stylesheet auf eine URL verwiesen (z.B. auf die URL eines Hintergrundbildes), dann kommt die Schreibweise url(http://absolute.com/bild.gif) oder url(relativ/bild.gif) zum Einsatz. Achtung: die relative URL bezieht sich auf das Stylesheet (nicht die HTML-Datei in der es verwendet wird).

 Klassisches Box Model

Jeder blockbildende Tag (z. B. h1, h2, p, blockquote, div, …) hat einen Rahmen, Innen- und Außenabstand. Diese werden mit den Deklarationen border, padding und margin festgelegt. Ein Hintergrundbild und/oder eine Hintergrundfarbe des Tags reicht immer bis zum Rahmen, aber nicht darüber hinaus. 

![Abbildung 21: Darstellung des Box Models von hicksdesign.co.uk](/images/image083.png)

Die Ausdehnung von margin, padding und border kann man besonders gut mit der Firefox-Erweiterung Firebug erforschen wie in Abbildung 22 gezeigt. 

![Abbildung 22: margin, border, padding in Firebug](/images/image085.png)

Dabei wird direkt in der Webseite der Außenabstand (margin) gelb und der Innenabstand (padding) dunkelviolett hinterlegt. 

Achtung: Im traditionelle Box model bezieht sich die Breite (width) bezieht auf den Inhalt, padding, border und margin muss man erst dazu zählen, um den Gesamt-Platzbedarf zu errechnen. Mit der Deklaration box-sizing: border-box kann man auf ein besseres Box-Model umschalten: dann gibt width die Gesamt-Breite an.  

Die Standard-Darstellung von Absätzen erklärt sich über den margin-top und margin-bottom des &lt;p&gt;-Tags:

![Abbildung 23: Standard-Darstellung von Absätzen (<p>) im Browser](/images/image086.png)

 Farben, Hintergrundfarben, Hintergrundbilder

Die Farbe des Textes wird mit color, die Hintergrundfarbe mit background-color gesetzt.  

Jeder Tag kann mittels CSS ein oder mehrere Hintergrundbilder erhalten (background-image). Als „Hintergrundbild“ in einer Webseite kann jedes Bild in einem Web-geeigneten Dateiformat (gif, jpg, png) dienen. Das Bild wird einfach dargestellt oder „gekachelt“ –horizontal und vertikal so oft wiederholt, bis es die ganze Fläche des Tags ausfüllt (background-repeat). Abbildung 24 wurde ein Bild mit drei Zahnrädern als Hintergrundbild verwendet, durch die Wiederholung werden sieben Zahnräder angezeigt. 

![Abbildung 24: Beispiel für ein Hintergrundbild in einer Webseite](/images/image088.png)

Bitte beachten Sie: Der Inhalt der Seite sollte trotz Hintergrundbild immer noch lesbar sein! Im Beispiel in Abbildung 24 ist eine Linkfarbe zu hell bzw. das Hintergrundbild zu auffällig: Der Text „wurde schon besucht“ in der letzten Zeile ist kaum noch lesbar. 

 Links formatieren

Der &lt;a&gt;-Tag wird in HTML für zwei sehr unterschiedliche Dinge verwendet: zum Setzen von Links und zum Setzen von Textmarken (auch ‚Anker’ genannt):

    <h1><a name="unis"></a>Universitäten</h1>   
    <a href="http://www.uni-salzburg.at/">Uni Salzburg</a>
    Textmarken sind normalerweise unsichtbar, Links sind normalerweise blau oder violett und unterstrichen. 

Um die Darstellung von Links zu verändern muss man in CSS :link oder :visited als Selektoren verwenden. Der Browser unterscheidet dabei zwischen Links die schon einmal besucht wurden (visited) und neuen Links. 

    a:link, a:visited { text-decoration: none; }

    a:link    {color:blue}

    a:visited {color:#FF00FF }

Im folgenden Beispiel werden die Links mit einem Icon markiert:

    a:link, a:visited { 
       background-image:    url(icon-link.gif);
       background-position: center right;
       background-repeat:   no-repeat;
       padding-right:       9px; 
    } 

