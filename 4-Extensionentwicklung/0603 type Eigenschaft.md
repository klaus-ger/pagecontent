#Extensionentwicklung#

##Typ Eigenschaft##

````
$TCA['tt_content'] = array (
  'ctrl' => array (
    'title' => 'Seiteninhalt',
    'label' => 'header',
    'type' => 'record_type',
  ),
  'types' => array(
    '0' => array('showitem' => 'hidden, record_type, title, some_date '),
    '1' => array('showitem' => 'record_type, title '),
    '2' => array('showitem' => 'title, some_date, hidden, record_type '),
  ),
);
````
