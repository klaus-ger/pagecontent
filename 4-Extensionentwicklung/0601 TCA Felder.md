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
