#[Extensionentwicklung](0100%20Index.markdown)#


##Basics##

###Grundüberlegungen###
Vor der Erstellung einer neuer Extension sollte man sich die Zeit nehmen, die erforderliche Datenstruktur zu skizzieren. Dabei werden schnell Abhängigkeiten klar und man spart später deutlich Zeit für nervige Änderungen. Meist nutze ich dafür ein Google Dokument "Zeichnung", letztendlich ist aber das Programm egal.

Als Beispiel nehme ich hier eine einfache Produktdatenbank:

image scetch

Was hier simpel und trivial erscheint, kann in Extensions mit über 20 Tabellen und zig Abhängigkeiten einem das Leben retten ;) Investiert die Zeit und macht es euch zur Gewohnheit - wer im Kundengespräch ein solches Chart zum Datenmodelling aus der Tasche ziehen kann wirkt einfach professioneller als die Aussage "Ich muss mal sehen ob das geht ...".

Anhand dieses Blueprints und des Extension Builders können die Models und Abhängigkeiten ziemlich einfach "zusammengeklickt" werden:

###Extensions mit dem Extension Builder erstellen###

image extension builder

Nach dem Speichern finden wir im Extensionverzeichnis unsere neue Extension "Produktdatenbank" die in etwas folgende Struktur hat:

image Struktur EXT Verzeichnis
