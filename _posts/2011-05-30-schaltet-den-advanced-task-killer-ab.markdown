--- 
wordpress_id: 695
layout: post
title: Schaltet den Advanced Task Killer ab!
wordpress_url: http://blog.kopis.de/?p=695
---
Wenn ihr - wie eigentlich jeder - das Programm Advanced Task Killer auf eurem Android Smartphone installiert habt, dann solltet ihr mal drüber nachdenken, wieso ihr euer Telefon so oft an die Steckdose bringen müsst:
<blockquote>By default, every application runs in its own Linux process. Android starts the process when any of the application's components need to be executed, then shuts down the process when it's no longer needed or when the system must recover memory for other applications.</blockquote>
Weiterlesen unter <a href="http://developer.android.com/guide/topics/fundamentals.html">Application Fundamentals im Android SDK</a>. <a href="http://geekfor.me/faq/you-shouldnt-be-using-a-task-killer-with-android/">Eine gute Zusammenfassung gibt es hier: <em>Why You Shouldn’t Be Using a Task Killer with Android</em></a>.

Und hier ist meine Zusammenfassung: Android selbst sorgt dafür, dass Prozesse abgeräumt werden, die nicht mehr benötigt werden. Wenn also ein Programm für eine Zeit lang keine Eingaben mehr annimmt oder keine anderen Aktivitäten startet, dann wird es vom Betriebssystem komplett aus dem Speicher und von der CPU entfernt. Alle Ressourcen werden freigemacht und euer Telefon wird sich nicht mehr mit dieser Anwendung beschäftigen.

Wenn ihr diese Task jetzt killt, bevor Android sie abräumt, wird sie evtl noch einmal gestartet und zwar mit den Standardeinstellungen - und nicht mit den vorher abgelegten Einstellungen. Das kann bedeuten, dass Programme tatsächlich ihre Arbeit von vorn beginnen und damit mehr Speicher und CPU verbrauchen als notwendig.

Also, schaltet das Teil mal aus. Und dann sagt mir bescheid, ob euer Telefon nach 1 oder 2 Tagen nicht doch besser läuft und der Akku vielleicht länger hält. ;-)
