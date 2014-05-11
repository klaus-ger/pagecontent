#Extensionentwicklung#

##Cheats Extbase Controller##

**Klasse instanzieren (anstelle von new)**

    Don't do this:
    $newObjekt = new Vedero/Ext/Domain/Model/Class
    //better:
    $newObject = $this->objectManager->get('Vendor\\Ext\\Domain\\Model\\Class');

**Frühzeitiges pesistieren**

    $this->objectManager->get('TYPO3\\CMS\\Extbase\\Persistence\\Generic\\PersistenceManager')->persistAll();
    
**Whitespace entfernen**

    $mail = preg_replace('/\s+/', '', $mail);
