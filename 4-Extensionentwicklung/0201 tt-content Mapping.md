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


Model
````
?php
/***************************************************************
* Copyright notice
*
* (c) 2012 Klaus Heuer <klaus.heuer@t3-developer.com>
* All rights reserved
*
* This script is part of the TYPO3 project. The TYPO3 project is
* free software; you can redistribute it and/or modify
* it under the terms of the GNU General Public License as published by
* the Free Software Foundation; either version 3 of the License, or
* (at your option) any later version.
*
* The GNU General Public License can be found at
* http://www.gnu.org/copyleft/gpl.html.
*
* This script is distributed in the hope that it will be useful,
* but WITHOUT ANY WARRANTY; without even the implied warranty of
* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
* GNU General Public License for more details.
*
* This copyright notice MUST APPEAR in all copies of the script!
***************************************************************/
/**
* Class for the tt_content
*
* represents the Content Model
*
*
*/
/**
* @scope prototype
* @entity
*/
class Tx_MyExtension_Domain_Model_Content extends Tx_Extbase_DomainObject_AbstractEntity {
/**
* uid
* @var int
* @validate NotEmpty
*/
protected $uid;
/**
* pid
* @var int
* @validate NotEmpty
*/
protected $pid;
/**
* sorting
* @var int
* @validate NotEmpty
*/
protected $sorting;
/**
* header
* @var string
*
*/
protected $header;
/**
* headerLink
* @var string
*
*/
protected $headerLink;
/**
* bodytext
* @var string
*
*/
protected $bodytext;
/**
* image
* @var string
*
*/
protected $image;
/**
* imageLink
* @var string
*
*/
protected $imageLink;
/**
* colPos
* @var int
*
*/
protected $colPos;
/**
* Returns the pid
*
* @return int $pid
*/
public function getPid() {
return $this->pid;
}
/**
* Returns the sorting
*
* @return int $sorting
*/
public function getSorting() {
return $this->sorting;
}
/**
* Returns the header
*
* @return string $header
*/
public function getHeader() {
return $this->header;
}
/**
* Returns the headerLink
*
* @return string $headerLink
*/
public function getHeaderLink() {
return $this->headerLink;
}
/**
* Returns the bodytext
*
* @return string $bodytext
*/
public function getBodytext() {
return $this->bodytext;
}
/**
* Returns the image
*
* @return string $image
*/
public function getImage() {
return $this->image;
}
/**
* Returns the imageLink
*
* @return string $imageLink
*/
public function getImageLink() {
return $this->imageLink;
}
/**
* Returns the colPos
*
* @return int $colPos
*/
public function getColPos() {
return $this->colPos;
}
}
?>
````


### Repository###

````
<?php
class Tx_MyExtension_Domain_Repository_ContentRepository extends Tx_Extbase_Persistence_Repository {
       protected $defaultOrderings = array('sorting' => Tx_Extbase_Persistence_QueryInterface::ORDER_ASCENDING);
}
?>
````


