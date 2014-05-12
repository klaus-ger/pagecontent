#Extensionentwicklung#

##Cheats Extbase Controller##

**Klasse instanzieren (anstelle von new)**

    Don't do this:
    $newObjekt = new Vedero/Ext/Domain/Model/Class
    //better:
    $newObject = $this->objectManager->get('Vendor\\Ext\\Domain\\Model\\Class');

**Frühzeitiges persistieren (speichern in die DB)**

Wird z.B. ein Datensatz mit $this->myRepository->add($newData) hinzugefügt, so steht nach dem persistieren die UID des Datensatzes zur Verfügung ($newData->getUid() ).

    $this->objectManager->get('TYPO3\\CMS\\Extbase\\Persistence\\Generic\\PersistenceManager')->persistAll();
    
**Mailfunktion im Controller**
    
        $email = \TYPO3\CMS\Core\Utility\GeneralUtility::makeInstance('TYPO3\\CMS\\Core\\Mail\\MailMessage');
        $email->setFrom($message['sender']);
        $email->setTo($message['receiver']);
        $email->setSubject($message['subject']);
        $email->setBody($message['content'], 'text/html');
        $email->send();
        
        
**Whitespace entfernen**

    $mail = preg_replace('/\s+/', '', $mail);
