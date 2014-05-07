#Extensionentwicklung#

##backend ViewHelper##

###BE Container ViewHelper###

````
<f:be.container pageTitle="foo" 
        enableJumpToUrl="false" 
        enableClickMenu="false" 
        loadPrototype="false" 
        loadScriptaculous="false" 
        scriptaculousModule="someModule,someOtherModule" 
        loadExtJs="true" 
        loadExtJsTheme="false" 
        extJsAdapter="jQuery" 
        enableExtJsDebug="true" 
        loadJQuery="true"
        includeCssFiles="0: '{f:uri.resource(path:\'Styles/Styles.css\')}'" 
        includeJsFiles="0: '{f:uri.resource(path:\'JavaScript/Library1.js\')}', 1: '{f:uri.resource(path:\'JavaScript/Library2.js\')}'" 
        addJsInlineLabels="{0: 'label1', 1: 'label2'}">
        
        
        your module content
        
        </f:be.container>

 
 ````
