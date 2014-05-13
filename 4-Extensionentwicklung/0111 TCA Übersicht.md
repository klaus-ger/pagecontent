#Extensionentwicklung#

##Das TCA (Tabellen-Konfigurations-Array)##


Ohne ein TCA Array für eine Tabelle geht in TYPO3 nichts da es die zentrale Schnittstelle zwischen Datenbank und TYPO3 darstellt. Wir brauchen also für jede Tabelle unserer Extension ein $TCA Array um die Tabelle im Backend anzuzeigen und den Tabelleninhalt in Extbase Models verfügbar zu machen.

Zusätzlich werden Tabellenrelation im TCA definiert, welche Felder in welcher Form im Backend angezeigt und wie validiert werden.

Seit TYPO3 6.1 reicht es aus, für jede Tabelle eine Datei mit dem entsprechendem TCA Array (Dateiname = Tabellenname) im Extension-Ordner Configruration/TCA zu speichern. Die Datei wird von dort automatisch geladen.

Es ist also nicht mehr erforderlich (wie bis 6.1 üblich), einen Teil der TCA Definition (das ctrl Array) in die ext_tables.php zu schreiben und dann auf eine dynamische Konfiguration im TCA Ordner zu verweisen.

*Vorsicht: Damit wird nur das TCA automatisch geladen. Weiterhin ist die Variable $_EXTKEY nach meiner Erfahrung dort nicht erreichbar. Diese wird desöftern in der Zeile iconfile => ... verwendet.*

*Die Zeilen*

*...\ExtensionManagementUtility::addLLrefForTCAdescr(... und*

*....\ExtensionManagementUtility::allowTableOnStandardPages(...*

*müssen nach wie vor in der ext_tables.php eingefügt werden.*




###Das TCA Array im Überblick:###

Pfad zur Datei: myExtension/Configuration/TCA/tx_meineextension_domain_model_tabelle.php

````
$TCA['tx_myextension_domain_model_table'] = array(
    'ctrl' => array(
        ... genrelle Anzeigeoptionen im Backend (Icon, Titel etc ...)
        ... generelles Verhalten der Tabelle 
        ... Pflichtangabe für jede Tabelle
    ),
    'interface' => array(
        ... Angaben wir die Tabelle im Backend angezeigt werden soll
    ),
    'types' => array(
        ... Anordnung der Felder innerhalb der Backendformulare (Datensatz bearbeiten)
    ),
    'palettes' => array(
        ... Hier können mehrere Felder für eine horizontale Anordnung im Formular zusammengafasst werden
    ),
    'columns' => array(
        ... Für jedes Datanbankfeld werden hier die Eigenschaften festgelegt:
        ... Feldtyp, Relationen, Validierung
    ),
);
````

