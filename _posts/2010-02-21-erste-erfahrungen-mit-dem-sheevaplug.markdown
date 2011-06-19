--- 
wordpress_id: 132
layout: post
title: Erste Erfahrungen mit dem SheevaPlug
wordpress_url: http://blog.kopis.de/?p=132
---

    <p><span class="dropCap">S</span>eit <a href="http://blog.kopis.de/2010/02/19/angekommen-sheevaplug-computer-fur-die-steckdose/">Freitag abend</a> habe ich ein wenig mit dem <a href="http://www.newit.co.uk/">SheevaPlug</a> herumgespielt. Mittlerweile l&auml;uft Apache 2, <a href="http://libtorrent.rakshasa.no/">rtorrent</a> (und <a href="http://www.wtorrent-project.org/trac/">wtorrent</a>) und das ganze System ist bereits aktualisiert. Nachdem ich erst einmal die Boot-Parameter kaputtgespielt hatte und der SheevaPlug nicht mehr von der SD-Karte startete, hab ich mir Backup-Images sowohl von der NAND-Partition als auch von der gesamten SD-Karte angelegt, einmal per USB-Stick und einmal per <em>dd</em> und <em>ssh</em>.</p>
<p><strong>Backup der NAND-Partition</strong></p>
<p><strong></strong> Erst einmal solltet ihr ohne SD-Karte starten, damit der SheevaPlug das Ubuntu von der eingebauten NAND-Partition bootet. Anschliessend mountet ihr einen USB-Stick und kopiert anschliessend das Root-Dateisystem auf den Stick.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>mount /dev/sda /mnt/usbstick
cp -a / /mnt/usbstick
cp -a /dev /mnt/usbstick
umount /mnt/usbstick</pre></div>
</div>

</span></p>
<p>Anschliessend steckt ihr den USB-Stick an euren Rechner und zieht mit <em>dd</em> ein Image:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>dd if=/dev/sda of=sheevaplug-nand.img</pre></div>
</div>

</span></p>
<p><strong>Backup der SD-Karte</strong></p>
<p><strong></strong> Startet wieder von der NAND-Partition und bootet Ubuntu. Sobald ihr den SheevaPlug wieder erreichen k&ouml;nnt, wird per <em>ssh</em> und <em>dd</em> direkt ein Image der SD-Karte gezogen - auf dem Plug selbst ist nat&uuml;rlich zu wenig Platz f&uuml;r die 8GB der Karte, daher wird alles direkt &uuml;ber SSH auf den lokalen Rechner gezogen.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>ssh ZIELADRESSE dd if=/dev/mmcblk0 | dd of=sheevaplug-sdcard.img</pre></div>
</div>

</span></p>
<p><strong>Wie geht es jetzt weiter?</strong></p>
<p><strong></strong> Sobald das Image der SD-Karte fertig ist, werde ich <a href="http://www.twonkyvision.de/">Twonkymedia Server</a> installieren und mit der <a href="http://www.xbox.com">Xbox</a> ausprobieren. Danach wird eine USB-Platte mit <a href="http://truecrypt.org">Truecrypt</a> und einigen Medien angeschlossen und das Streaming per Twonkymedia auf die <a href="http://de.playstation.com/ps3/">PS3</a> und den <a href="http://www.sony.de/hub/bravia-lcd-fernseher">Sony Bravia</a> ausprobiert. :-)</p>
  
