--- 
wordpress_id: 23
layout: post
title: "Installation der USB-Treiber f\xC3\xBCr die serielle Konsole des SheevaPlug unter Windows 7"
wordpress_url: http://blog.kopis.de/?p=23
---

    <p>Heute nachmittag wollte ich meinem <a href="http://de.wikipedia.org/wiki/SheevaPlug">SheevaPlug</a> noch einmal auf den Zahn f&uuml;hlen. Seit ein paar Tagen kann ich mich nicht mehr per SSH einloggen, obwohl er ansonsten wie erwartet funktioniert. Ich wollte mich also &uuml;ber die serielle Konsole per USB-Port einloggen - aber leider werden die Treiber nicht korrekt unter Windows 7 installiert.</p>
<p>Man muss nach dem Download die Dateien entpacken und anschliessend die ftdibus.inf und ftdiport.inf editieren und mehrere Zeilen einf&uuml;gen. <a href="http://www.georg-stich.de/index.php?option=com_content&amp;view=article&amp;id=54:ftdi-change&amp;catid=34:soft&amp;Itemid=61">Bei Georg Stich hab ich schliesslich einen Artikel gefunden, in dem der Vorgang erkl&auml;rt ist</a>. Ich poste hier nochmal die &Auml;nderungen, damit sie nicht verloren gehen:</p>
<h2>FTDIBUS.INF</h2>
<blockquote>[FtdiHw]<br /> %USBVID_9E88&amp;PID_9E8F&amp;MI_00.DeviceDesc%=FtdiBus.NT,<strong>USBVID_9E88&amp;PID_9E8F&amp;MI_00</strong><br /> %USBVID_9E88&amp;PID_9E8F&amp;MI_01.DeviceDesc%=FtdiBus.NT,<strong>USBVID_9E88&amp;PID_9E8F&amp;MI_01</strong><p />  [FtdiHw.NTamd64]<br /> %USBVID_9E88&amp;PID_9E8F&amp;MI_00.DeviceDesc%=FtdiBus.NTamd64,<strong>USBVID_9E88&amp;PID_9E8F&amp;MI_00</strong><br /> %USBVID_9E88&amp;PID_9E8F&amp;MI_01.DeviceDesc%=FtdiBus.NTamd64,<strong>USBVID_9E88&amp;PID_9E8F&amp;MI_01</strong><p />  [Strings]<br /> USBVID_9E88&amp;PID_9E8F.DeviceDesc="SheevaPlug JTAGKey FT2232D B"<br /> USBVID_9E88&amp;PID_9E8F&amp;MI_00.DeviceDesc="SheevaPlug JTAGKey FT2232D B Port A"<br /> USBVID_9E88&amp;PID_9E8F&amp;MI_01.DeviceDesc="SheevaPlug JTAGKey FT2232D B Port B"</blockquote>
<h2>FTDIPORT.INF</h2>
<blockquote class="posterous_medium_quote">[FtdiHw]<br /> %VID_9E88&amp;PID_9E8F.DeviceDesc%=FtdiPort2232.NT,<strong>FTDIBUSCOMPORT&amp;VID_9E88&amp;PID_9E8F</strong><p />  [FtdiHw.NTamd64]<br /> %VID_9E88&amp;PID_9E8F.DeviceDesc%=FtdiPort2232.NTamd64,<strong>FTDIBUSCOMPORT&amp;VID_9E88&amp;PID_9E8F</strong><p />  [Strings]<br /> VID_9E88&amp;PID_9E8F.DeviceDesc="SheevaPlug JTAGKey FT2232D B Serial Port"</blockquote>
<p>Die fett gedruckten Stellen kann man auch in den Ger&auml;tedetails im Ger&auml;temanager nachsehen.&nbsp;Und so soll das ganze anschliessend im Ger&auml;temanager aussehen:</p>
<p><a href="http://www.flickr.com/photos/cringe/5199003440/" title="SS-2010-11-22_18.24.53 by cringe, on Flickr"><img src="http://farm5.static.flickr.com/4154/5199003440_da8e036ec6.jpg" height="475" alt="SS-2010-11-22_18.24.53" width="412" /></a></p>
<p>Ist das erledigt, kann man sich z.B. mit Putty auf dem neu erstellten COM-Port (bei mir ist das jetzt COM8) mit folgenden Einstellungen verbinden:</p>
<p><a href="http://www.flickr.com/photos/cringe/5198410029/" title="SS-2010-11-22_18.25.14 by cringe, on Flickr"><img src="http://farm5.static.flickr.com/4144/5198410029_06b4b4b988.jpg" height="448" alt="SS-2010-11-22_18.25.14" width="466" /></a></p>
<p>Jetzt ist man auf dem SheevaPlug und kann sich ganz normal einloggen.</p>
  
