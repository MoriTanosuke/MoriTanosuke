--- 
wordpress_id: 612
layout: post
title: "Twitter Cleaner - kleine Anwendung, um Tweets bei Twitter zu l\xC3\xB6schen"
wordpress_url: http://blog.kopis.de/?p=612
---
Wenn ihr euch öfter mal fragt "<em><a href="http://twittercleaner.appspot.com/index.jsp">Wie lösche ich alle meine Tweets bei Twitter?</a></em>", dann haben wir das gleiche Problem. Hin und wieder schwanke ich zwischen einem öffentlichen und einem privaten Account, aber wenn ich von privat auf öffentlich wechsel, möchte ich nicht unbedingt, das meine Updates auf Twitter für alle Welt lesbar sind.

Aber es gibt <a href="http://twittercleaner.appspot.com/index.jsp">kein <em>Bulk Delete</em> für Twitter</a>! Kein <a href="http://twittercleaner.appspot.com/index.jsp">massenhaftes Löschen aller Status Updates im eigenen Twitter Account</a>.

Deshalb hab ich mich hingesetzt und eine kleine Anwendung für die <a href="http://code.google.com/intl/de-DE/appengine/">Google AppEngine</a> geschrieben, mit der Tweets gelöscht werden können:
<p style="text-align: center;"><a href="http://twittercleaner.appspot.com/">Twitter Cleaner</a></p>
Ihr könnt euch dort einloggen und anschliessend einzelne oder mehrere Status Updates löschen. Im Moment sieht das alles doof aus, aber daran arbeite ich als nächstes. Im Moment funktioniert das löschen erstmal und ihr könnt damit schnell eure letzten Updates entfernen.

Die nächsten Arbeiten sind:
<ol>
	<li>Suchfunktion für schnelles Finden der zu löschenden Tweets</li>
	<li>ALLE Tweets im Account löschen</li>
	<li>Auswahl von Tweets per Checkbox für gezieltes Löschen</li>
	<li>Aufhübschen der Oberfläche (wahrscheinlich mit <a href="http://code.google.com/intl/de-DE/webtoolkit/">GWT</a>)</li>
</ol>

Wenn ihr noch Wünsche habt oder einen Fehler findet, dann schreibt einfach was dazu im <a href="https://github.com/MoriTanosuke/TwitterCleaner/issues">Issue Tracker</a>. <a href="https://github.com/MoriTanosuke/TwitterCleaner">Ihr findet den (herrlich unaufgeräumten) Quelltext auch drüben bei Github</a>.
