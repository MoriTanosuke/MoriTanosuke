--- 
wordpress_id: 71
layout: post
title: Anwendungen auf Android-Telefonen spionieren die Anwender aus
wordpress_url: http://blog.kopis.de/?p=71
---

    <p>Mittlerweile ist es sogar schon <a href="http://www.heise.de/newsticker/meldung/Apps-telefonieren-nach-Hause-Update-1047796.html">bei heise aufgeschlagen: Android Apps haben arglose Nutzer ausgesp&auml;ht.</a> Und mir ist ein etwas zu sorgloser Umgang mit Berechtigungen auch schon aufgefallen. Ich wollte mir z.B. einen FLAC-Player installieren, und musste erstaunt feststellen, dass der Player meinen Telefonstatus und die Logs auslesen will. Wieso das?</p>
<p>Wahrscheinlich, weil damit Ger&auml;teinformationen ausgelesen werden. Evtl f&uuml;r Hacks und Workarounds f&uuml;r spezielle Ger&auml;te, evtl um die Ger&auml;te noch detaillierter zu identifizieren - oder evtl um die IMEI auszulesen und an chinesische Server zu &uuml;bertragen... wei&szlig; man halt erstmal nicht. Und als Normalnutzer klickt man sich &uuml;ber den Installationsbildschirm sowieso schnell weg, der einen mit detaillierten Berechtigungsinformationen &uuml;bersch&uuml;ttet.</p>
<p>Wie sch&uuml;tzt man sich jetzt vor so einem Diebstahl?</p>
<ol>
<li>Man installiert keine Anwendungen.</li>
<li>Man nutzt Webanwendungen, die nur beschr&auml;nkten Zugang zu der Telefonhardware haben.</li>
<li>Man nutzt nur <a href="http://code.google.com/p/andless/source/browse/trunk/src/net/avs234/AndLess.java#945">Open Source-Anwendungen, deren Quelltext man &ouml;ffentlich einsehen kann</a>.</li>
</ol>
<p>Ich verstehe sowieso nicht, wieso man f&uuml;r jeden Kleinkram eine Anwendung auf dem Telefon braucht. Haben wir nicht die <em>always connected smartphones</em>, damit wir sowas nicht brauchen und immer und &uuml;berall auf das gro&szlig;e weite Internet zugreifen k&ouml;nnen? Und nur wenn ich z.B. eine Navigationssoftware oder einen Schlafmonitor nutzen will, braucht so eine Anwendung wirklich Zugriff auf meine Hardware. Sogar <a href="http://de.wikipedia.org/wiki/Standortbezogene_Dienste">Location Based Services</a> wie Google Maps k&ouml;nnen mittlerweile vom Browser aus den aktuellen Ort bestimmen. Ausserdem ist das Webdesign mittlerweile durch AJAX und generell durch Javascript so weit, dass Webanwendungen wie Desktop bzw Smartphone anwendungen aussehen und funktionieren.</p>
<p>Die besten Beispiele, die ich t&auml;glich nutze:</p>
<ul>
<li>Google Reader</li>
<li>Instapaper</li>
<li>Wordpress</li>
</ul>
<p>Wenn ihr noch Beispiele f&uuml;r Schadanwendungen oder zu weit gesetzte Berechtigungen auf Smartphones habt, schreibt doch mal einen Kommentar. Und schreibt auch gleich eure Lieblings-Webanwendung dazu. ;-)</p>
  
