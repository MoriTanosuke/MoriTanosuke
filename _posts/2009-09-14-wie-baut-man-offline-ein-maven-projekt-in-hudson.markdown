--- 
wordpress_id: 153
layout: post
title: Wie baut man offline ein Maven-Projekt in Hudson?
wordpress_url: http://blog.kopis.de/?p=153
---

    Diese Frage besch&auml;ftigt mich gerade. Auf der Maschine des Entwicklers l&auml;uft ein lokales Repository und der Zugriff erfolgt per HTTP. Jetzt soll das Projekt auf den <a href="https://hudson.dev.java.net/">Hudson</a>-Server umziehen, der aber keinerlei Internetverbindung verf&uuml;gt.<p />Wie bekommt man das <a href="http://maven.apache.org/">Maven</a>-Repository am besten auf den Hudson-Server?<p /><ul>
<li>Einfach bei der Konfiguration des Projektes draufkopieren?</li>
<li>Auf einer VM neben den Server stellen? (im Hinblick auf Nutzung des Repositories in zuk&uuml;nftigen Projekten sicher das beste.)</li>
<li>Das Maven-Repository im Subversion verwalten und vor dem Build abholen?</li>
</ul><p>Am einfachsten ist f&uuml;r das erste Projekt bestimmt das manuelle Kopieren des Repositories. F&uuml;r den weiteren Einsatz lohnt sich das Aufsetzen einer eigenen VM f&uuml;r das Repository.</p><p>Hat jemand eine sch&ouml;ne URL zu einem Erfahrungsbericht oder sogar eigene Erfahrungen mit der Einf&uuml;hrung von Maven in die <em>Continuous Integration</em>?</p>
  
