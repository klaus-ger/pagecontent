#Installation & Einrichtung#

Suchmaschinenoptimierung (SEO) ist ein weites Feld das sich ständig neu erfindet. Ich bin weder ausgewiesener SEO Spezialist, auch würde es den Umfang dieser Seite sprengen auf alle Einzelheiten einzugehen. Hier also nur ein paar Basisc mit TYPO3 typischen Workaround.

##Metatags in TYPO3##

Unter SEO Aspekten haben die Metatags in den letzten Jahren an Gewicht verloren, dennoch sollte man den head Bereich seiner Seite nicht ganz vernachlässigen.
Der title-Tag und die meta Descriptions sind immer noch eine wichtige Angabe für die Ergebnisanzeige in Suchmaschinen, auch wenn es für die Positionierung in den Ergebnissen eine untergeordnete Rolle spielt.
Und persönliche finde ich, ein wildes gemixe von Metatags, CSS Links und Scriptaufrufe im Header zeugen nicht wirklich von einer durchdachten Installation und dem Wunsch nach einem schlankem Quellcode.
Für eine Standardseite reichen folgende Angaben:

````
<!DOCTYPE html>
<html lang="de">
<head>
 
<meta charset="utf-8">
<!--
This website is powered by TYPO3 - inspiring people to share!
...
-->
 
<base href="http://www.myPage.de/">
 
<title>My Title - max. 65 charakters</title>
<meta name="generator" content="TYPO3 6.2 CMS">
<meta name="description" content="Page Content - max 130 charakters">
<meta name="keywords" content="keyword 1, keyword 2">
<meta name="author" content="Klaus Heuer">
<meta name="date" content="2014-03-19">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="robots" content="index,follow">
 
<link rel="stylesheet" type="text/css" href="link zur css" media="screen">
 
<script src="link zum scipt" type="text/javascript"></script>
 
<link href="http://myPage.de/" rel="canonical" />
<link rel="shortcut icon" href="http://mypage.de/icon.ico" type="image/x-icon; charset=binary" />
<link rel="icon" href="http://mypage.de/icon.ico" type="image/x-icon; charset=binary" />
</head>
````

Dies ist wirklich eine anonymisierte Header Kopie einer Live Seite, ohne irgedwelche Plugins oder Core Hacks um die Reihenfolge zu manipulieren.

Die Setupeinstellungen im Einzelnen:

###doctype###

Seit der TYPO3 Version 6.0 wird der doctype automatisch auf html5 gesetzt.
Die Typoscriptzeile config.doctype = html5 ist nicht mehr erforderlich.

###html-Tag###

Typoscript: config.htmlTag_langKey = de
Bei mehrsprachigen Seiten muss der Key über Conditions angepasst werden.
