#TYPO3 Installation#


Wer nur selten eine TYPO3 Seite neu aufsetzt und Linux nur am Rende kennt, sucht immer wieder die passenden Terminalbefehle für eine schnelle Installation of dem Apache Server. Eine Kurzanleitung:

##TYPO3 per Terminal und SHH vom Mac auf dem server installieren##

Voraussetzungen:
* Ihr habt euren ssh Key auf dem Server hinterlegt und kennt den Usernamen
* 

ins download Verzeichnis navigieren 
    
    cd downloads

Daten auf Server kopieren:

        scp typo3_src-6.2.2.tar.gz user@domain:folder/
        
        
SSH password eingeben: 


ins Serververzeichnis wechseln und TYPO3 entpacken

      tar xzf typo3_src-6.2.x.tar.gz
      
Neuen Ordner anlegen, hier cms

    mkdir cms

ins neue VErzeichnis wechseln

    cd cms
    
* Create the symlinks in your Document Root:

```
  cd htdocs
  ln -s ../typo3_src-6.2.x typo3_src
  ln -s typo3_src/index.php index.php
  ln -s typo3_src/typo3 typo3
```

* In case you use Apache, copy the .htaccess to your Document Root:

```
  cp typo3_src/_.htaccess .htaccess
```
