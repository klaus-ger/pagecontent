#Extensionentwicklung#

##Eigenes Backendmodul anlegen#

Datei: ext_tables.php

````
    /**
     * My Bakcendmodul
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
