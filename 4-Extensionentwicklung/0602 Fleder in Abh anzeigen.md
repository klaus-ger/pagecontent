#Extensionentwicklung#

##TCA Felder in Abhängigkeit von anderen Felder anzeigen##

Scenario: Wir wollen Felder im TCA Formular in Abhängigkeit von Werten in Auswahlboxen ein- oder ausblenden.

Zunächt brauchen wir ein Feld das unsere Auswahl beinhalten. Sinnvoll kann hier eine Selectfeld oder eine einfache Checkbox sein. Das Feld in unserem Beispiel nennen wir form_type und haben es in über die ext_table.sql in der Datenbank ergänzt.

Um die Felder ein- oder auszublenden, brauchen wir ein reload das wir mit folgender Zeile in der ctrl Section ergänzen:

````
$TCA['tx_myextension_domain_model_table'] = array(
    'ctrl' => array(
    ....
    'requestUpdate' =>'form_typ',
    ...
    ),
    ...
)
````   
  
Bei jeder Änderung des Feldes 'form_typ' wird nun unser tcA Formular neu geladen.

##Felder ein- und ausblenden##

Unser Feld as nun die Anzeige bestimmt am Beispeil eines Select Feldes:

````
        'form_typ' => array(
            'exclude' => 1,
            'label' => 'Form Typ',
            'config' => array(
                'type' => 'select',
                'items' => array(
                    array('Standard', 0),
                    array('Variante A', 1),
                    array('Variante B', 2),
                    
                )
            ),
        ),
````

Die Felder die nun in Abhängigkeit des Wertes im Feld 'form_typ' angezeigt werden sollen, erhalten jetzt in der Column Section den zusätzlichen Eintrag 'displayCond'.

````
    'my_field' => array(
            'exclude' => 1,
            'displayCond' => 'FIELD:form_typ:=:1',
            'label' => 'my Label',
            'config' => array(
                'type' => 'input'
            ),
        ),
````

Damit wird das Feld 'my_field' nur angezeigt, wenn im Feld 'from_typ' Variante A (= Wert 1) ausgwählt wurde. 
