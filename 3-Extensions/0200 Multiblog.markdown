#Multiblog#

Eine Blogextension für TYPO3. 
Multiblog ist eine einfach zu administrierende Blogextension mit Kommentarfunktion, social sharing und kompletter Frontend Editierung des Blogs. Es sind mehrere Blogs in einer TYPO3 Installation möglich.

| Aktuelle Version | 1.1 stable |
| :--------------- | :----------- |
| TER Name         | multiblog    |
| Kompatibel | TYPO3 6.2.1 und höher |

##Kurzbeschreibung##

###Blog###
Jedem Blog wird als Inhaber ein FE User zugeordnet. Mit diesen Zugangsdaten kann er sich im Frontend für die Blogeditierung anmelden. Auf Blogebene können folgende Einstellungen getroffen werden:
- Blogwidget Auswahl (Welche Widgets im Blogfrontend angezeigt werden)
- Blog Kurztext (erscheint im Blogwidget, social Sharing und in der Übersicht bei mehreren Blogs)
- Blog Bild (für social sharing und Übersicht mehrere Blogs)

###Post###
Ein Blogeintrag (Post) besteht aus mehreren *Contentelementen* (Absätzen). Jedem Contentelement kann ein Bild zugeordnet werden. Für jeden Blogeintrag können folgende Einstellungen getroffen werden:
- Datum des Eintrags
- Status (sichtbar / verborgen)
- Kategorien
- Kommentare erlauben
- SEO Text

###Kommentare###
Die eingebaute Kommentarfunktion basiert auf Ajax. Jeder Kommentar muss vom Bloginhaber einzeln freigeschaltet werden. Im Kommentar werden folgende Angaben gespeichert:
- Name
- email Adresse (wird nicht angezeigt)
- Kommentar
- Datum
- Status (Freigabe durch Bloginhaber)
- Post der kommentiert wurde

###Widgets###
