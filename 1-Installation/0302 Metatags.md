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

###Metatag charset###

Typoscript: config.metaCharset = utf-8

###Base-Tag###

Typoscript: config.baseURL = myPage.de

###Title-Tag###

Der wichtigse Tag im Header. Der Feldinhalt wird aus dem Seitentitel gerendert und solte aus ca. 60 Zeichen bestehen.
Meist wird ja dieses Feld nur für den Naviagationspunkt benutzt - dieser sollte dann im Feld "Alternative Naviagtion Title" gepflegt werden.
Von einem Standardwert für alle Seiten kann ich nur abraten, da Google unter Umständen Seiten mit gleichem Header einfach ignoriert.

###Meta Generator###

Das Metag "Generator" kann über Typoscript nicht ausgeblendet oder verschoben werden. Eigentlich nicht schön an dieser Stelle ...

###Meta Description###

Das Feld kann über die Seiteneigengeschaften Meta Daten befüllt werden. Maximal 130 Zeichen, wird meist von den Suchmaschinen als Textfeld berücksichtigt.
Typoscript: page.meta.description.data = page:description

###Meta Keywords###

Die Keywords werden von Google nicht mehr berücksichtigt, sie schaden aber auch nicht - Einträge auf den Seiteneigenschaften: Keywords.
Typoscript: page.meta.keywords.data = page:keywords

###Meta Author###

Optional, kann fix über page.meta.author = Mein Name gesetzt werden.

###Meta Date###

Rendert das Datum der letzten Änderungen bzw. Seitenerstellung.
Typoscript: page.meta.date.data = page:SYS_LASTCHANGED // page:crdate;
Typoscript: page.meta.date.date = Y-m-d

###Meta viewport###

Legt den Zoomfaktor auf Mobilengeräten fest.
Typoscript: page.meta.viewport  = width=device-width, initial-scale=1.0

###Meta robots###

Anweisung für die Suchmaschinen Bots.
Typoscript: page.meta.robots = index,follow

###Link Stylesheet###

Wenn Ihr eure CSS Styleshhets über page.includeCSS einbindet erscheinen die an dieser Stelle. Es sollte immer mal überprüft werden, ob sich Stylesheets nicht sinvoll zusammenfassen lassen. 10 verschiedene CSS Dateiein hier einbinden macht wenig Sinn - siehe auch Abschnitt gzip Komprimierung.

###Link Script###

siehe Stylesheet, Einbindung über page.includeJS, aus Perfomancegründen möglichst viele js Dateien in den Footer verlegen.

###canonical###

Der canonical Link weist auf die eindeutige Contentseite zur Verhinderung von Double Content. Das Typoscript Snippet muss je nach eingesetzter Extension erweitert werden. Typoscript:

````
page.headerData {
700 = TEXT
700 {
    stdWrap.typolink.parameter.data = TSFE:id
    stdWrap.typolink.forceAbsoluteUrl = 1
    stdWrap.typolink.returnLast = url
    htmlSpecialChars = 1
    wrap = <link href="|" rel="canonical" />
  }
}
`´´´

###shortcut Icon###

Das Shortcut-Icon kann auch über page.shortcutIcon = myicon.ico eingebunden werden. Dann werden die Links jedoch im Header vor dem Title Tag ausgegeben. Um die shotcut Links am Ende einzufügen hilft folgendes Snippet:

````
page.headerData {
701 = TEXT
701.value (

<link rel="shortcut icon" href="http://mypage.de/icon.ico" type="image/x-icon; charset=binary" />
)

702 = TEXT
702.value (

<link rel="icon" href="http://mypage.de/icon.ico" type="image/x-icon; charset=binary" />
)

    }
````
    

Die Klammer-Schreibweise sorgt für den Zeilenumbruch im Header.
