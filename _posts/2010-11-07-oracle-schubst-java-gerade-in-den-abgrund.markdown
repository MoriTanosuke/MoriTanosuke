--- 
wordpress_id: 30
layout: post
title: Oracle schubst Java gerade in den Abgrund
wordpress_url: http://blog.kopis.de/?p=30
---
Angefangen hat es mit <a href="http://www.mysql.de/">MySQL</a>: die kostenlose Variante unterstützt demnächst keine Transaktionen mehr. Ein ernsthaftes Manko für Anwendungen, wenn man seine Transaktionen nicht in der Anwendungslogik verwalten möchte. <a href="http://www.heise.de/newsticker/meldung/Oracle-erhoeht-Preise-fuer-MySQL-1130025.html">Und die anderen Varianten werden 3x so teuer wie bisher.</a> (<a href="http://www.oracle.com/us/corporate/pricing/price-lists/mysql-pricelist-183985.pdf">Offizielle Preisliste gibt es hier.</a>) <a href="http://www.skysql.com/en/letter-to-mysql-customers">Andere Firmen nutzen das als Anlass, die MySQL-Kunden abzuwerben.</a>

Ok, MySQL gehört sowieso auf den Müll. Aber der Hammer kommt danach:

<a href="http://www.theregister.co.uk/2010/11/06/oracle_dueling_jvms/">Oracle will Java in einer Free und einer Premium Version vertreiben</a>, die aus einer Verschmelzung von <a href="http://www.oracle.com/technetwork/middleware/jrockit/downloads/index.html">JRockit</a> und <a href="http://www.oracle.com/technetwork/java/javase/tech/index-jsp-136373.html">Hotspot</a> entstehen soll. Natürlich wird die Free-Version auch performant sein (ja klar), aber die Premium-Version wird besser in die Oracle-Middleware integriert sein. Gut, das ist erstmal nur eine Quelle bei <a href="http://www.theregister.co.uk/">The Register</a>, aber trotzdem: Oracle traue ich sowas zu. Und parallel dazu wird das Engagement im JCP zurückgefahren, <a href="http://www.itp.net/581440-oracle-kills-opensolaris-efforts">Neuerungen werden nur in die Premium-Version eingebaut</a>, und langsam, aber sicher stirbt die Free-Version aus.

Wird es langsam Zeit, sich eine andere Sprache und Plattform zu suchen? Sollte ich doch <a href="http://carstenringe.net/?sort=&amp;search=golang">meine Gehversuche in Golang</a> fortsetzen? Oder einen Lisp-Dialekt ohne JVM als mein bevorzugtes Entwicklungsinstrument auswählen?
