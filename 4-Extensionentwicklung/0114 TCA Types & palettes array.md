#Extensionentwicklung#

##Die TCA Type & Palletes Sub-Arrays##

Im Type Array wird die Feldanordnung in TCA Formulare festgelegt. Dabei kann es durchaus verschiedene Types (Ansichten) für ein Formular (nit verschiedenen Feldern) geben. Ein klassisches Beispiel ist das normale tt-content TCA Form - hier erfolgt die unterschiedliche Feldanzeige bei der Änderungen von z.B. 'Text' auf 'Text mit Bild' über Type Angaben.

In disem Abschnitt erkläre ich nur die generellen Möglichkeiten der Type und Palletes Arrays - die Funktion zur Einblendung von unterschiedlichen Felder wird hier beschrieben.

**Die Reihenfolge im Formular festlegen**

Um Felder im TCA Formular anzuzeigen müssen sie - nachdem sie im Columns Array definiert sind - im Typ Subarray des TCA aufgezählt werden:

````
$TCA['tx_myextension_domain_model_table'] = array(
    'ctrl' => array(
        ....
    'interface' => array(
        ...
    ),
    'types' => array(
        '1' => array('showitem' => ' feld_1, feld_2, feld_3....)
    ),
    'palettes' => array(
        '1' => array( .... ),
    ),
    'columns' => array(
        ....
    )
)
````

Die Reihenfolge im Array bestimmt die Reihenfolge in der Ausgabe wobei jedes Feld in einer neuen Zeile erscheint.

##Tabs in TCA Formularen anzeigen##

Um Tabs - analog aus den in tt_content TCA Forms belannten Reitern 'Text', 'Bilder' etc zu erzeugen, muss das ctrl- und types Subarray ergänzt werden:

**ctrl-Array**

````
$TCA['tx_myextension_domain_model_table'] = array(
    'ctrl' => array(
        ....
        'dividers2tabs' => TRUE,
        ....
        ),
    ....
)
````

Im types-Subarray können wir nun unsere Tabs - gekennzeichnet durch 'div; my_Label' einfügen:

````
$TCA['tx_myextension_domain_model_table'] = array(
    'ctrl' => array(
        ....
        'dividers2tabs' => TRUE,
        ....
        ),
    ....
    'types' => array(
        '1' => array('showitem' => ' div; my_first_tab_label
                                   , feld_1
                                   , fled_2
                                   , div; my_second_tab_label
                                   , field_3
                                   ....
                )
       )
)
````
