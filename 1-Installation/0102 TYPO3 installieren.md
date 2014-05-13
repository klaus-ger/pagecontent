#Installation#

##TYPO3 Installieren##

###Voraussetzungen für eine typische Installation###

**Server**
* Apache Server mod_expires and mod_rewrite enabled
* GraphicsMagick or ImageMagick v6
* standard PHP package
 * php Version 5.4 oder höher
  * memory_limit minimum 128M
  * max_execution_time 30s, empfohlen 240s
* MySQL Datenbank 5.1 bis 5.6, kein 'strict mode'
* 200 MB Speicherplatz
* ssh Serverzugriff empfohlen

Die Voraussetzungen werden eigentlich inzwischen von allen mittleren Paketen der großen Webhoster erfüllt.

**Lokale Software**
* Aktueller Webbrowser
* PC: Putty, Mac: Terminal
* FTP Programm
* Editor oder IDE (Z.B. Netbeans) empfohlen

* Download des aktuellen TYPO3 Paketes

###TYPO3 auf den Webserver installieren###
Siehe auch Artikle 'TYPO3 per SHH auf dem Server installieren'.

* Das komprimierte TYPO3 Paket per SHH auf den Server eine Ebene über euer Rootverzeichnis kopieren.
(Das Rootverzeichnis ist der Ordner auf dem eure Domain verweist.)
* Die TYPO3 Datei auf dem Server entpacken
* Im Rootverzeichnis einen Systemlink auf den entpackten Ordner setzten
* Im Rootverzeichnis einen Systemlink auf den Ordner typo3 setzen
* Im Rootverzeichnis einen Systemlink auf die index.php setzen
* Die _htaccess Datei aus dem entpacktem TYPO3 VErzeichnis in euer Rootverzeichnis kopieren und auf .htaccess umbenennen.
 

Ihr habt nachher folgende Verzeichnisstruktur auf dem Server:
  
    typo3_src-6.2.x/
    htdocs/typo3_src -> ../typo3_src-6.2.x/
    htdocs/typo3 -> typo3_src/typo3/
    htdocs/index.php -> typo3_src/index.php
    htdocs/.htaccess


###TYPO3 installieren###
