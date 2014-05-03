#Extensionentwicklung#

##TCA Felder##

###Type Select###

Mit leerer Optionsauswahl:
````
'my_field' => array(
            'exclude' => 1,
            'label' => 'My labeltext',
            'config' => array(
                'type' => 'select',
                'items' => array(
                    array('', 0),
                ),
                'foreign_table' => 'tx_myextension-table',
                'foreign_table_where' => 'ORDER BY my_order_field ASC',
                'size' => 1,
                'minitems' => 0,
                'maxitems' => 1,
            )
      ),
````

mit Wizards:
````
'my_select' => array(
            'exclude' => 1,
            'label' => 'my_field_label',
            'config' => array(
                'type' => 'select',
                'foreign_table' => 'tx_mytable',
                'foreign_table_where' => 'ORDER BY myorderfield ASC',
                
                'size' => 10,
                'autoSizeMax' => 30,
                'maxitems' => 9999,
                'multiple' => 0,
                'wizards' => array(
                    '_PADDING' => 1,
                    '_VERTICAL' => 1,
                    'edit' => array(
                        'type' => 'popup',
                        'title' => 'Edit',
                        'script' => 'wizard_edit.php',
                        'icon' => 'edit2.gif',
                        'popup_onlyOpenIfSelected' => 1,
                        'JSopenParams' => 'height=350,width=580,status=0,menubar=0,scrollbars=1',
                    ),
                    'add' => Array(
                        'type' => 'script',
                        'title' => 'Create new',
                        'icon' => 'add.gif',
                        'params' => array(
                            'table' => 'tx_mytable',
                            'pid' => '###CURRENT_PID###',
                            'setValue' => 'prepend'
                        ),
                        'script' => 'wizard_add.php',
                    ),
                ),
            ),
        ),
  ````

###FAL Image Feld###
````
'my_image' => array(
            'exclude' => 1,
            'label' => 'Image',
            'config' => \TYPO3\CMS\Core\Utility\ExtensionManagementUtility::getFileFieldTCAConfig('files', array(
                'appearance' => array(
                    'createNewRelationLinkTitle' => 'LLL:EXT:cms/locallang_ttc.xlf:images.addFileReference'
                ),
                'minitems' => 0,
                'maxitems' => 3,
                    ), $GLOBALS['TYPO3_CONF_VARS']['GFX']['imagefile_ext']),
        ),
````
