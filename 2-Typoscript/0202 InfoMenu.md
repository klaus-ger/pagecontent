# Info Menü
# Datei: Pagesetup oder Menulibrary
# Aufruf per cObject in Fluid- oder Markern in Html Templates
# In Zeile 8 muss die uid des Rootline Ordners angegeben werden
lib.infoNavi = HMENU
lib.infoNavi.special = directory
lib.infoNavi.special.value = 99
lib.infoNavi.1 = TMENU
lib.infoNavi.1 {
wrap = <ul> | </ul>
expAll = 0
noBlur = 1
NO.allWrap = <li> | </li>
#Für eine separate Klasse des ersten und letzten MenuItems folgende Zeile benutzen:
#NO.allWrap = <li class="first>|</li>|*|<li>|</li>|*|<li class="last">|</li>
RO < .NO
RO = 1
CUR < .NO
CUR = 1
CUR.allWrap = <li class="active"> | </li>
ACT < .CUR
}
