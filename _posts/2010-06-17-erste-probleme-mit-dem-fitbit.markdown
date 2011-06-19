--- 
wordpress_id: 93
layout: post
title: Erste Probleme mit dem Fitbit
wordpress_url: http://blog.kopis.de/?p=93
---

    <p>Nachdem mein <a href="http://www.fitbit.com/">Fitbit</a> tags&uuml;ber schon flei&szlig;ig mitlief, wollte ich gestern abend die Synchronisation an meinem Macbook (ein <em>4,1</em>er) einrichten. Also hab ich <a href="http://www.fitbit.com/start">die Software installiert</a> und das <em>Account Setup</em> gestartet. Bei der Verbindung zur Basisstation traten dann allerdings die ersten Probleme auf: Keine Verbindung!</p>
<p>Nachdem ich eine Weile herumprobiert und 64bit- und 32bit-Modus ausprobiert habe, musste ich feststellen, dass ich etwas tiefer ran musste. Also habe ich den Fitbit-Daemon im Debugmodus gestartet:</p>
<p><span style="font-family: Times New Roman; font-size: medium;"> </span></p>
<div class="CodeRay">
  <div class="code"><pre>sudo launchctl unload -w /Library/LaunchDaemons/com.fitbit.fitbitd.plist
sudo /usr/local/bin/fitbitd -nmb</pre></div>
</div>

<p>&nbsp;</p>
<p>Diesen Schritt kann man sich ersparen, wenn man einfach das Zubeh&ouml;rprogramm <em>Konsole</em> &ouml;ffnet und die Konsolenmeldungen ansieht. Dort habe ich dann folgende Zeile gefunden:</p>
<p><span style="font-family: Times New Roman; font-size: medium;"> </span></p>
<div class="CodeRay">
  <div class="code"><pre>Failed to initialize communication [VID: 0x10c4, PID: 0x84c4]. Is the base station plugged in?</pre></div>
</div>

<p>&nbsp;</p>
<p>VID 0x10c4 ist die Vendor ID, PID 0x84c4 ist die Produkt ID zur Identifikation des Fitbit auf dem USB-Bus. Aber anscheinend wurde dort nichts gefunden. Allerdings wird das Fitbit geladen, wenn es in der Basisstation steckt - ein einfacher Kabelbruch kommt auch durch die Sichtpr&uuml;fung des Kabels eigentlich nicht in Frage.</p>
<p>Da ich mein Fitbit bei <a href="http://www.ebay.com">Ebay USA</a> gekauft habe, werd ich wohl keine Chance auf Umtausch haben. Fr&uuml;her oder sp&auml;ter muss ich die Basisstation wohl aufknacken und nach Hardware-Fehlern suchen. Sollte das keinen Erfolg bringen, muss ich mir irgendwie einen Ersatz organisieren - f&auml;hrt demn&auml;chst jemand in die USA? ;-)</p>
  
