#[Extensionentwicklung](0100%20Index.markdown)#

Mit dem eID Mechanismus und einem separatem PageType stehen zwei unterschiedliche Methoden für AjaxCalls zur Verfügung. 
Beide haben ein ähnliches Funktionsprinzip, unterscheiden sich aber deutlich in Details. Eine Gegenüberstellung.


##AjaxCalls über pageType##

Die Verwendung eines einen page Types für Ajax Calls ist relativ simpel. Ihr müsst zunächst euer Extensionsetup um einen neuen PageType erweitern. Die PageType Nummer muss einmalig in der Installation sein, also ggf. bereits vergebene PageTypes für RSS, Sitemaps, Print & Co beachten. 

````
ajaxCall = PAGE
ajaxCall {
    typeNum = 999
    config.disableAllHeaderCode = 1
    config.metaCharset = UTF-8
    10 = COA
    10 <  styles.content.get
    }
````
    
Mit dieser Einstellung könnt Ihr ganz normale euer Actionergebnis an einen View übergeben den Ihr dann komplett in Ajax zur Verfügung habt.

Der AjaxCall in jQuery sieht dann ungefähr so aus: 

````
$.ajax({
    var controller = tx_myExt_pi1[controller]= blabla;
    var action = tx_myExt_pi1[action]= bub; // ohne Action am Ende
    var pagetype = 999;
    url: './?' + controller + '&' + action + '&type=' + pagetype
    //optionale Parameter
    data: 'useruid=' + useruid,
    success: function(result) {
        console.log(result);
    },
    error: function(error) {
       console.log(error);
    }
});
````
 
 
Innerhalb von success:function(result) { } wird dann das Ergebnis ausgewertet und der View manipuliert.
