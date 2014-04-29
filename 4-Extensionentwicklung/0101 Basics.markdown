#[Extensionentwicklung](0100%20Index.markdown)#


##Basics##

###Grundüberlegungen###
Vor der Erstellung einer neuer Extension sollte man sich die Zeit nehmen, die erforderliche Datenstruktur zu skizzieren. Dabei werden schnell Abhängigkeiten klar und man spart später deutlich Zeit für nervige Änderungen. Meist nutze ich dafür ein Google Dokument "Zeichnung", letztendlich ist aber das Programm egal.

Als Beispiel nehme ich hier eine einfache Produktdatenbank:

image scetch

Anhand dieses Blueprints und des Extension Builders (1) können die Models ziemlich einfach "zusammengeklickt" werden:

image extension builder

Nach dem speichern finden wir im Extensionverzeichnis unsere neue Extension "Produktdatenbank" die in etwas folgende Struktur hat:

image Struktur EXT Verzeichnis
