Class: Classes/Utility/userLabel.php

````
<?php

require_once(PATH_t3lib . 'class.t3lib_befunc.php');

class userLabel {

    function getUserLabel(&$params, &$pObj) {
                
        $id = $params['row']['uid']; //aktuelle uid 
        
        //kompletten Datensatz holen
        $rec = t3lib_BEfunc::getRecord($params['table'],$params['row']['uid']);
        
        //Startdatum aus Event Tabelle
        $mylabel = date('d.m.Y',$rec['start_timestamp']); //wie oben holen wir uns den
        
        
        //Play Datensatz laden
        if ($rec['play']) {
			$item = t3lib_BEfunc::getRecord('tx_theatre_domain_model_play', $rec['play']);
			$mylabel.= ' | '.$item['title'];
		}
            
            
        //subtitel vom Event anhängen
        $mylabel.= ' | '.$rec['title'];
        
        
        //Rückgabe 
        $params['title'] = $mylabel ;
        
       
    }

   
}

?>
````

ext_tables.php TCA

````
$TCA['tx_theatre_domain_model_event'] = array(
    'ctrl' => array(
        'title' => 'LLL:EXT:theatre/Resources/Private/Language/locallang_event.xlf:list_title',
        'label' => 'start_timestamp',
        'label_alt' => 'play',
        'label_alt_force' => TRUE,
        'label_userFunc' => "userLabel->getUserLabel",
        ....
````

ext_tables.php

````
//custom table label for events
require_once(\TYPO3\CMS\Core\Utility\ExtensionManagementUtility::extPath($_EXTKEY).'Classes/Utility/userLabel.php');
````
