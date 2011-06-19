--- 
wordpress_id: 58
layout: post
title: Was macht Digg?
wordpress_url: http://blog.kopis.de/?p=58
---

    <p>Seit der Ver&ouml;ffentlichung des <a href="http://digg.com/">neuen Digg v4</a> gibt es einige Aufregung &uuml;ber die Instabilit&auml;t und die neuen Funktionen. <a href="http://techcrunch.com/2010/09/07/digg-struggles-vp-engineering-door/">Au&szlig;erdem ist anscheinend der VP Engineering gefeuert worden</a> oder gegangen. Ich war nie ein gro&szlig;e Digg-Nutzer, aber die aktuelle Diskussion interessiert mich nat&uuml;rlich.</p>
<p>F&uuml;r mich stellt sich jetzt eine Frage: Wieso geht man mit so einer Seite live, wenn sie anscheinend so kaputt ist, dass der verantwortliche Softwareingenieur gefeuert werden muss? Und wieso hat das vorher niemand gemerkt?</p>
<p>Bei einer Seite der Gr&ouml;&szlig;enordnung von Digg (oder <a href="http://www.reddit.com/">Reddit</a>, btw) kann es nat&uuml;rlich auf der echten Seite ganz andere Effekte geben wie in Testumgebungen. Millionen von User kann man eben nicht simulieren, man kann nur hochrechnen und sch&auml;tzen. <a href="http://blog.reddit.com/2010/08/everything-went-better-than-expected.html">Die Gr&ouml;&szlig;enordnungen kann man in einem Blogartikel von reddit nachlesen</a>, ca. 380k pro Stunde an normalen Tagen.</p>
<p>Digg wollte mit der neuen Seite eine bessere Skalierbarkeit erreichen, schafft aber im Moment wohl das Gegenteil. Schuld soll der Umstieg von <a href="http://www.mysql.de/">MySQL</a> auf <a href="http://cassandra.apache.org/">Cassandra</a> sein. Gut, die Technologie ist vielleicht noch nicht so alt wie MySQL, aber gro&szlig;e Firmen wie <a href="http://engineering.twitter.com/2010/07/cassandra-at-twitter-today.html">Twitter nutzen sie durchaus in Produktivsystemen</a>. Und ich glaube, die Aufregung bezieht sich eher um die neuen Funktionen und <a href="http://kevinrose.com/blogg/2010/8/27/digg-v4-release-iterate-repeat.html">Fehler in der Anwendung</a>. Die Fehler h&auml;tten w&auml;hrend des internen Tests, w&auml;hrend der Closed- und Open-Beta entdeckt werden m&uuml;ssen. Und das w&auml;re dann auch der einzige Punkt, der f&uuml;r mich eine Entlassung - oder besser: eine K&uuml;ndigung erkl&auml;ren w&uuml;rde.</p>
<p>Oder ist es mittlerweile so, da&szlig; IT-Projekte nicht fehlschlagen d&uuml;rfen? Das es keine Fehler in Software geben darf? Oder hei&szlig;t das eher, dass in Zukunft mehr Wert auf geplante (und planbare Testphasen) gelegt werden muss?</p>
  
