#Extensionentwicklung#

##Tabellenmappig am Beispiel der tt-content##

Im Gegensatz zu den Tabellen fe_user und usergroups bietet Extbase kein fertiges Model für Inhalte der tt_content Tabelle.
Das Snippet hier bietet ein fertiges Mapping und Model, um die wichtigsten Inhalte der tt_content in der eigenen Extension nutzen zu können.

Um auf die Inhalte der tt_content Tabelle zugreifen zu können, werden folgende Dateien benötigt:

myExtension/Configuration/TypoScript/Setup.txt
Mapping der Tabelle auf ein Extension Model. Die Setup Datei muss in der ext_tables.php eingebunden werden:
t3lib_extMgm::addStaticFile($_EXTKEY, 'Configuration/TypoScript', 'Setup');

myExtension/Classes/Domain/Model/Content.php
Im Snippet sind nur die Getters für die wichtigsten tt_content Inhalte angelegt. Wer tt_content Daten in seiner Extension ändern will, muss die entsprechenden Setters nachtragen.

myExtension/Classes/Domain/Repositoryl/ContentRepository.php
Normale Repository Class für individuelle Abfragen.

````
config.tx_extbase {
persistence{
enableAutomaticCacheClearing = 1
updateReferenceIndex = 0
classes {
Tx_MyExtension_Domain_Model_Content {
mapping {
tableName = tt_content
columns {
uid.mapOnProperty = uid
pid.mapOnProperty = pid
sorting.mapOnProperty = sorting
CType.mapOnProperty = contentType
header.mapOnProperty = header
header_link.mapOnProperty = headerLink
bodytext.mapOnProperty = bodytext
image.mapOnProperty = image
image_link.mapOnProperty = imageLink
colPos.mapOnProperty = colPos
}
}
}
}
}
}
````
