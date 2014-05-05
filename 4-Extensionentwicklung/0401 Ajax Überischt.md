#[Extensionentwicklung](0100%20Index.markdown)#

Mit dem eID Mechanismus und einem separetem PageType stehen zwei unterschiedliche Methoden für AjaxCalls zur Verfügung. 
Beide haben ein ähnliches Funktionsprinzip, unterscheiden sich aber deutlich in Details. Eine Gegenüberstellung.


##Ajax und Extbase: eID oder Page Type nutzen?##

Unabhäng von der Fragestellung eID oder PageType hier einmal das Grundschema eines Ajax Aufrufes. Einsteigern in die Thematik ist oftmals nicht klar, das der Serverresponse in jQuery ausgewertet werden muss. Ohne eine result Function, ändert sich auch nichts im Fronend ;)

Die Grundüberlegung von Ajax ist, - unabhängig vom Mechanismus - einen möglichst kleinen Datensatz vom Server zurück zu erhalten den wir dann per jQuery auswerten und den View manipulieren (Punkt 4 + 5).

Also keinen Pageheader etc., sondern exakt genau nur die Daten die wir brauchen.

Image

|      | eID | page Type |
|------|-----|-----------|
| Einbindung in Extension | • Dispatcher Class im Controller Verzeichnis<br />• eID include in ext-tables.php | Definition pageType in Extension setup |
| Ajax Aufruf             | Controller, Action, Parameter              | Controller, Action, Parameter |
|                         |                                            | + PageType                    |
| Rückgabe                | gewöhnlich json String                     | json String oder              |
|                         |                                            | html des gefülleten Teplates  |
| Controller Action Umgebung | kein TSFE geladen                          | TSFE geladen (settings,       |
|                         |                                            | mapped tables etc stehen zur Verfügung) |
| Beispielanwendung       | Nachladen von Werten für Select Felder     | Komplexe Seitenmanipulationen |
|                         | autocomplete Funktionen                    | ganze Bereiche ersetzten, da gefüllte|
|                         |                                            | Templates als html string geliefert|
