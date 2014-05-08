#Extensionentwicklung#

##TCA Felder##
Direktlinks
* [Input](#input) 
* [Textarea](#textarea)
* [select](#type-select)
* [FAL Image](#fal-image-feld)
* [Standard Image](#standard-image)

###Input###
````
'input_field' => array(
            'exclude' => 1,
            'label' => 'my Label',
            'config' => array(
                'type' => 'input',
                'size' => 30,
                'eval' => 'trim'
            ),
        ),
````

###Textarea###
````
        'textarea field' => array(
            'exclude' => 1,
            'label' => 'My textfield label',
            'config' => array(
                'type' => 'text',
                'cols' => 40,
                'rows' => 5
            ),
        ),
````


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
  
mit festen Auswahlwerten und Icons

````
'color' => array(
            'exclude' => 1,
            'label' => 'My Field Label',
            'config' => array(
                'type' => 'select',
                'items' => array(
                    array('grau', '474747'  , 'EXT:myextension/Resources/Public/Icons/color_474747.gif'),
                    array('gelb', 'efcc00'  , 'EXT:myextension/Resources/Public/Icons/color_efcc00.gif'),
                    
                    )               
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

###Standard Image###
````
        'image' => array(
            'exclude' => 1,
            'label' => 'My Image Label',
            'config' => array(
                'type' => 'group',
                'internal_type' => 'file',
                'uploadfolder' => 'uploads/tx_myext',
                'show_thumbs' => 0,
                'size' => 5,
                'maxitems' => 99,
                'allowed' => $GLOBALS['TYPO3_CONF_VARS']['GFX']['imagefile_ext'],
                'disallowed' => '',
            ),
        ),
````






