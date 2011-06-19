--- 
wordpress_id: 550
layout: post
title: Wie man Pluspunkte in der Entwickler-Community sammelt
wordpress_url: http://blog.kopis.de/?p=550
---
Ich bastel ja seit ein paar Tagen an einem Clojure-Client für die neue Fitbit API, mit der man an die Daten auf www.fitbit.com herankommt. Dabei viel (nicht nur) mir auf, dass OAuth seit ein paar Tagen 404-Fehler wirft und ich mich nicht mehr mit meinem Applikation-Token und -Secret anmelden kann.

Erst war ein paar Tage Funkstille im Entwicklerforum, aber dann <a href="https://groups.google.com/d/topic/fitbit-api/n0yv3-dzAqY/discussion">meldete sich endlich ein Offizieller mit einer Erklärung</a>:

<blockquote>We've been working hard to improve the Fitbit developer APIs. Lately, we've noticed a number of wrinkles with the authorization system, and we have a few fixes that are scheduled to be rolled out tomorrow. Most of these issues have been noticed first by the Fitbit developer community.
[...]
If you're still having issues, it would help us immensely if you could submit a Minimal Reproducible Test Case.
[...]
We'll keep working to resolve any issue, no matter how it's reported, but sending a Minimal Reproducible Test Case with help us investigate your issue much more quickly! Plus, you get the assurance of knowing that we'll be adding your specific test case to our release testing process.
</blockquote>

Damit wurde die Funkstille zumindest bei mir wieder etwas gutgemacht. Ich finde es grundsätzlich positiv, wenn die Verantwortlichen auf die externen Entwickler hören, die mit einer neuen Funktion herumspielen und versuchen, damit etwas eigenes aufzubauen. Wenn man dann noch merkt, dass man der Firma hilft, Probleme aufzudecken und sogar in Zukunft zu vermeiden, dann ist das für mich auch ein Erfolgserlebnis.

Und wenn ich demnächst ohne 404s weitermachen kann, dann werd ich bald auch mit dem Clojure-Client fertig und kann mich wieder der ursprünglichen Idee, nämlich einem <a href="http://docs.google.com">Google Docs</a>/CSV-Export auf der Google Appengine widmen. :-)
