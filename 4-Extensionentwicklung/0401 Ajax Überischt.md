#[Extensionentwicklung](0100%20Index.markdown)#

Mit dem eID Mechanismus und einem separetem PageType stehen zwei unterschiedliche Methoden für AjaxCalls zur Verfügung. 
Beide haben ein ähnliches Funktionsprinzip, unterscheiden sich aber deutlich in Details. Eine Gegenüberstellung.


##Ajax und Extbase: eID oder Page Type nutzen?##

Unabhäng von der Fragestellung eID oder PageType hier einmal das Grundschema eines Ajax Aufrufes. Einsteigern in die Thematik ist oftmals nicht klar, das der Serverresponse in jQuery ausgewertet werden muss. Ohne eine result Function, ändert sich auch nichts im Fronend ;)

Die Grundüberlegung von Ajax ist, - unabhängig vom Mechanismus - einen möglichst kleinen Datensatz vom Server zurück zu erhalten den wir dann per jQuery auswerten und den View manipulieren (Punkt 4 + 5).

Also keinen Pageheader etc., sondern exakt genau nur die Daten die wir brauchen.
