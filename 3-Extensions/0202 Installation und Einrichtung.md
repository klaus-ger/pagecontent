#Multiblog - Installation und Einrichtung#

##Installation##

* Extension (Key: multiblog) aus dem TER laden und installieren
* Im Seitensetup multiblog inkludieren.
* Eine neue Seite vom Typ 'Ordner' für die Blogdaten anlegen
* Im Seitensetup -> Konstanten -> multiblog die storagePid angeben

* Das Blog plugin auf einer Seite einfügen. Die Seite sollte eine 100% Breite haben und benötig keinen content wrapper.
* Das Seitensetup so modifizieren (conditions) das keine title oder Meta Tags auf der Blog plugin Seite ausgegeben werden. (werden von der Extension gerendert).

* Auf einer weiteren Seite das Plugin Blog -> frontend editing einfügen und Konstante im Setup setzten

* Im Seitentyposcript des Speicherordners: TCEMAIN.clearCacheCmd = PID of the Blogplugin eintragen. Damit wird der Cache bei neuen Einträgen automatisch gelöscht.

Empfehlenswert ist der Einsatz von realUrl. Eine Beispielkonfiguration ist im EXT Ordner multiblog/realURL_config enthalten. Mit dieser Konfiguration werden links wie 'www.meineseite.de/die-ist-mein-blogeintrag' erzeugt werden.


 
