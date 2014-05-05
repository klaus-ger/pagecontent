#[Extensionentwicklung](0100%20Index.markdown)#

Mit dem eID Mechanismus und einem separatem PageType stehen zwei unterschiedliche Methoden für AjaxCalls zur Verfügung. 
Beide haben ein ähnliches Funktionsprinzip, unterscheiden sich aber deutlich in Details. Eine Gegenüberstellung.


##AjaxCalls über pageType##

Die Verwendung eines eigenen page Types für Ajax Calls ist relativ simpel. Ihr müsst zunächst euer Extensionsetup um einen neuen PageType erweitern. Die PageType Nummer muss einmalig in der Installation sein, also ggf. bereits vergebene PageTypes für RSS, Sitemaps, Print & Co beachten. 

Extensionsetup

````
ajaxCall = PAGE
ajaxCall {
    typeNum = 999
    config.disableAllHeaderCode = 1
    config.metaCharset = UTF-8
    10 = COA
    10 < tt_content.list.20.myextension_myplugin
    }
````
    

Der AjaxCall in jQuery sieht dann ungefähr so aus: 

````
$('#jq-send').click(function(e) {
    $.ajax({
        var controller = tx_myExt_pi1[controller]= blabla;
        var action = tx_myExt_pi1[action]= meine Function; // ohne Action am Ende
        var pagetype = 999;
        url: '/?' + controller + '&' + action + '&type=' + pagetype
        //optionale Parameter
        data: 'useruid=' + useruid,
        success: function(result) {
            console.log(result);
        },
        error: function(error) {
         console.log(error);
        }
    });
});
````
 Ein Beispiel findet ihr auch in meiner Blogextension "multiblog" auf Github: 
 
###Controller###
 
 Eure Controllerfunction muss natürlich wie jede Action in der ext_localconf.php registriert sein. Innerhalb dieser Action stehet euch die ganz normale Extbase Umgebung zur Verfügun, also alles das was ihr in 'normalen' Funktion auch habt (injected Repositories, mapped Tables, setting, persistance Angaben etc.) 
 
Am Ende der Funktion müsst Ihr euch nur entscheiden, was Ihr zurückgeben wollt:

Rückgabe eine json strings (z.B. Ergebnisarray):

    return json_decode(4myArray)


Rückgabe eines kompletten Views als html string.
Am Ende der Ajax Funktion im Controller setzt Ihr ganz normal euren view (template muss vorhanden sein)

    $this->view->assign('myAjaxAction, $values);
    
Keinerlei Rückgabe
z.B wenn Ihr nur Daten speichert z.B. für einen counter:
    
    exit;
    
    
Innerhalb von success:function(result) { } wird dann das Ergebnis ausgewertet und der View manipuliert.
