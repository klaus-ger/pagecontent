#Extensionentwicklung#

##Das TCA (Tabellen Konfiguratins Array)##


Ohne einem $TCA Array für eine Tabelle geht in TYPO3 nichts, da es die zentrale Schnittstelle zwischen Datenbank und TYPO3 darstellt. Wir brauchen also für jede Tabelle unserer Extension ein $TCA Array um die Tabelle im Backend anzuzeigen und den TAbelleninhalt in Extbase Models verfügbar zu machen.

Seit TYPO3 6.1 reicht es aus, für jede Tabelle eine Datei mit dem entsprechendem TCA Array (Dateiname = Tabellenname) im Extension-Ordner Configruration/TCA zu speichern. Die Datei wird von dort automatisch geladen.

Es ist also nicht mehr erforderlich (wie bis 6.1 üblich), einen Teil der TCA Definition in die ext_tables.php zu schreiben und dann auf eine dynamische Konfiguration im TCA Ordner zu verweisen.


###Das $TCA Array im Überblick:###

````
$TCA['tx_examples_haiku'] = array(
    'ctrl' => array(
        ....
    ),
    'interface' => array(
        ....
    ),
    'columns' => array(
        ....
    ),
    'types' => array(
        ....
    ),
    'palettes' => array(
        ....
    ),
);
````

