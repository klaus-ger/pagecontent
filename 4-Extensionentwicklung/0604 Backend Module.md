#Extensionentwicklung#

##Eigenes Backendmodul anlegen#

Datei: ext_tables.php

````
    /**
     * My Backendmodul
     */
    \TYPO3\CMS\Extbase\Utility\ExtensionUtility::registerModule(
            'Vendor.' . $_EXTKEY, 'web', 'mymodulname', // Submodule key
            '', // Position
            array(
        'MyBackendController' => 'list',
            ), array(
        'access' => 'user,group',
        'icon' => 'EXT:' . $_EXTKEY . '/ext_icon.gif',
        'labels' => 'LLL:EXT:' . $_EXTKEY . '/Resources/Private/Language/locallang_myName.xlf',
            )
    );
````

Um die Templates sauber von den Frontendtemplates zu trennen, können wir folgende Ordnerstrutur im Verzeichnis MyExtension/Resources/Private anlegen:

 - Backend/Layouts
 - Backend/Partials
 - Backend/Templates
 
Das Mapping erfolgt durch folgenden Eintrag in der Extensionsetup:

````
module.tx_myextension {
	view {
		templateRootPath = EXT:myextension/Resources/Private/Backend/Templates/
		partialRootPath  = EXT:myextension/Resources/Private/Backend/Partials/
		layoutRootPath   = EXT:myextension/Resources/Private/Backend/Layouts/
	}
}
````
