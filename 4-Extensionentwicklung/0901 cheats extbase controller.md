#Extensionentwicklung#

##Cheats Extbase Controller##

Klasse instanzieren (anstelle von new)

    Don't do this:
    $newObjekt = new Vedero/Ext/Domain/Model/Class
    //better:
    $newObject = $this->objectManager->get('Vendor\\Ext\\Domain\\Model\\Class');
