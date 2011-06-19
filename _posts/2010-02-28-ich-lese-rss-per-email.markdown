--- 
wordpress_id: 131
layout: post
title: Ich lese RSS per eMail
wordpress_url: http://blog.kopis.de/?p=131
---

    <p><span class="dropCap">W</span>ieso? Weil ich immer noch gro&szlig;er Fan von eMail bin. Asynchrone Kommunikation, trotzdem Quasi-Echtzeit und kostenlos. Und weil ich auf meine eMail von &uuml;berall Zugriff habe, Iphone sei Dank.  Nachdem ich schon den Service <a href="http://www.feedmyinbox.com/">FeedMyInbox</a> ausprobiert habe und mit dem <a href="http://www.amazon.com/Kindle-Wireless-Reading-Display-Generation/dp/B0015T963C/kopisde-21">Amazon Kindle</a> einen sinnvollen Endpunkt f&uuml;r so einen Dienst in meiner Reisetasche habe, wollte ich mal sehen, ob ich das ganze nicht auch auf meinen eigenen Rechnern und damit unter meiner Kontrolle aufsetzen kann. Gesagt, getan: <a href="http://www.allthingsrss.com/rss2email/">rss2email</a> erledigt genau diese Aufgabe.  Unter Debian ist das Programm schnell installiert:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>apt-get install rss2email</pre></div>
</div>

</span></p>
<p>Voraussetzung ist <a href="http://python.org/">Python</a>, aber das ist mittlerweile ja schon fast Pflicht bei einer Linuxinstallation... :-} Danach kann man mit folgenden Befehlen die ersten Feeds hinzuf&uuml;gen:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>r2e new email@domain.org
r2e add http://url/fuer/den/feed
r2e run --no-send</pre></div>
</div>

</span></p>
<p>Damit ist der erste Feed hinzugef&uuml;gt und der erste Lauf hat den aktuellen Stand des Feeds geholt. Der Parameter <tt>--no-send</tt> verhindert das Versenden aller Feedartikel, erst bei einem Aufruf ohne diesen Parameter werden eMails verschickt. Das sollte man aber einem <a href="http://de.wikipedia.org/wiki/Cron">cronjob</a> &uuml;berlassen, der zyklisch l&auml;uft. Bei mir ist das alle 30 Minuten:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>crontab -l
*/30 * * * * r2e run</pre></div>
</div>

</span></p>
<p>Ab sofort fliessen also einige Feeds direkt in mein Postfach. Ob ich wirklich die <a href="http://www.amazon.com/gp/help/customer/display.html?nodeId=200375630&amp;#fees">Geb&uuml;hren f&uuml;r die Mobilfunk&uuml;bertragung</a> zum <a href="http://www.amazon.com/Kindle-Wireless-Reading-Display-Generation/dp/B0015T963C/kopisde-21">Amazon Kindle</a> bezahlen will, wei&szlig; ich noch nicht. M&ouml;glich w&auml;re das ganze aber mit rss2email, daf&uuml;r m&uuml;sste ich bloss eine neue Feeddatei mit meiner privaten Kindle-eMail anlegen und Feeds hinzuf&uuml;gen.</p>
  
