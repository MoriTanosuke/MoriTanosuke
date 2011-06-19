--- 
wordpress_id: 591
layout: post
title: Programm als Administrator mit Sandboxie installieren
wordpress_url: http://blog.kopis.de/?p=591
---
Wer von euch öfter Programme installiert und seine Windows-Installation nicht versauen will, der ist bestimmt schon auf <a href="http://www.sandboxie.com">Sandboxie</a> gestossen. Damit werden Programme in einem <a href="http://de.wikipedia.org/wiki/Sandbox">Sandkasten</a> eingeschlossen und können nur dort Dateien verändern. Ist man mit dem Programm bzw. mit den Funktionen unzufrieden, wird einfach der gesamte Sandkasten geleert und alle Änderungen des Programms sind wieder von eurem Rechner verschwunden. Sehr praktisch.

Ein <strong>Problem unter Windows 7 64-bit</strong> ist aber die Installation von Software. Die Installation fragt nämlich bei Windows nach erweiterten Rechten, die aber in den Standardeinstellungen von Sandboxie immer verworfen werden. <a href="http://www.sandboxie.com/index.php?SBIE2217">Heraus kommt die Fehlermeldung SBIE2217</a> und die Installation schlägt fehl.

Wenn ihr also Software in der Sandbox installieren wollt, richtet ihr euch am besten eine neue Sandbox ein und <a href="http://www.sandboxie.com/index.php?RestrictionsSettings#drop">deaktiviert dort das <em>Drop Rights</em></a>. Dazu macht ihr folgendes:
<ol>
	<li>Doppelklick auf das Sandboxie-Tray Icon</li>
	<li>Menü <em>Sandbox </em>öffnen</li>
	<li>Als Name <em>AdminBox</em> eingeben</li>
	<li>Rechtsklick auf die neue <em>AdminBox</em>, dann <em>Sandbox Settings</em> anklicken</li>
	<li>Punkt <em>Restrictions</em> auswählen</li>
	<li>Punkt <em>Drop Rights</em> auswählen</li>
	<li>Haken bei <em>Drop rights from Administrators and Power Users groups</em> wegnehmen</li>
</ol>
Die Sandbox heißt bei mir z.B. "<em>AdminBox</em>" und ist damit sehr deutlich von der Standardbox unterscheidbar.

Wenn das installierte Programm euch gefällt, könnt ihr natürlich nach ein paar Probeläufen auch die Dateien aus der Sandbox in das echte System verschieben. Das werde ich mir nach einem <em>Dell-Download-Ruhezustand-kaputt</em>-Desaster in Zukunft deutlich länger überlegen... :-(
