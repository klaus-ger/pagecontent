#[Extensionentwicklung](0100%20Index.markdown)#


##Basics##

###Grundüberlegungen###
Vor der Erstellung einer neuer Extension sollte man sich die Zeit nehmen, die erforderliche Datenstruktur zu skizzieren. Dabei werden schnell Abhängigkeiten klar und man spart später deutlich Zeit für nervige Änderungen. Meist nutze ich dafür ein Google Dokument "Zeichnung", letztendlich ist aber das Programm egal.

Als Beispiel nehme ich hier eine einfache Produktdatenbank:

![Image](../blob/master/9-Images/Tables Produktdatenbank.png?raw=true)
 


Was hier simpel und trivial erscheint, kann in Extensions mit über 20 Tabellen und zig Abhängigkeiten einem das Leben retten ;) Investiert die Zeit und macht es euch zur Gewohnheit - wer im Kundengespräch ein solches Chart zum Datenmodelling aus der Tasche ziehen kann wirkt einfach professioneller als die Aussage "Ich muss mal sehen ob das geht ...".

Anhand dieses Blueprints und des Extension Builders können die Models und Abhängigkeiten ziemlich einfach "zusammengeklickt" werden:

###Extensions mit dem Extension Builder erstellen###

image extension builder

Nach dem Speichern finden wir im Extensionverzeichnis unsere neue Extension "Produktdatenbank" die in etwas folgende Struktur hat:

image Struktur EXT Verzeichnis

Extbase erwartet die Dateien in speziellen Verzeichnissen, nur so kann das Autoloading von Classen funktioneren. Demnach sind die Ordnerbezeichnungen fix und dürfen auch nicht geändert werden.

Verzeichnis **Classes**
Nur hier - und wirklich nur hier - steht ausführbarer php Code. Alles was später an php Libaries, ViewHelpers oder Utilitiy Classes gebraucht wird, kommt hier hinein. 

Verzeichnis **Configuration**
Extension Setup, Configurationsdatei und TCA der Tabellen. Später auch plugin Flexforms etc ...

Verzeichnis **Resources**
