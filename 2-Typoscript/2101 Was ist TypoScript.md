#TypoScript -Basics#

##Was ist TypoScript?##

Auch wenn der Name darauf hindeutet, TypoScript ist **keine** Programmier- oder Scriptsprache. 
 
Typoscript kann man vereinfacht mit XML vergleichen - es können Konstanten definiert und Werte zugewiesen werden.
Letztendlich ist es ein großes Array das TYPO3 intern in php geparst wird. 

**TypoScript begegnet uns vor allem in 3 Bereichen:**

* Dem Seitentemplate
* Auf Seiten-Ebene (um z.B. die Eigenschaften einzelner Seiten oder Baumabschnitte zu beinflussen) 
* Auf User-Ebene (User & Usergroups, z.B. um Rechte einzustellen)

**Die Syntax:**

Die TypoScript Syntax ist proprietär und für den Einsteiger zunächst verwirrend, nach kurzer Einarbeitung wird man sich aber schnell daran gewöhnt haben. Grundsätzlich sollte man beim Schreiben von TypoScript die gleichen Regeln beachten wie sonst auch: den Code gruppieren, sinnvolle Zeileneinzüge und Aufsplittung in verschiedene Dateien um die Übersichtlichkeit zu gewährleisten.

Wenn ich Installationnen sehe die über 500 Zeilen TypoScript bunt gemixt im Setup stehen haben, verwundert es micht nicht, wenn es im Frontend *unerklärliche* Darstellungsfehler gibt ;)

**TypoScript lebt:**

Die Syntax von TypoScript ist nicht auf ewige Zeiten festgeschrieben. Zumindest bei den TYPO3 Major Updates gibt es auch immer wieder ein paar Änderungen in der TypoScript Syntax. 
