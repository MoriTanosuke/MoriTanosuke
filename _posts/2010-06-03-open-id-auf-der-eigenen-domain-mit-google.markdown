--- 
wordpress_id: 99
layout: post
title: Open ID auf der eigenen Domain mit Google
wordpress_url: http://blog.kopis.de/?p=99
---

    <p>Seit heute kann ich meine eigene Domain <a href="http://www.kopis.de">www.kopis.de</a> als <a href="http://de.wikipedia.org/wiki/OpenID">Open ID</a> verwenden. Das geht &uuml;berraschend einfach, wenn man schon bei einem Open ID-Provider wie <a href="http://www.google.com/profiles/carsten.ringe">Google</a> (oder <a href="http://me.yahoo.com/carstenringe">Yahoo</a> oder <a href="http://www.aol.de">AOL</a> oder <a href="https://www.myopenid.com/">My Open ID</a>) angemeldet ist. Dann gen&uuml;gen die folgenden Zeilen im Header der eigenen Homepage:</p>
<p><span style="font-family: Times New Roman; font-size: medium;"> </span></p>
<div class="CodeRay">
  <div class="code"><pre>&lt;link href=&quot;https://www.google.com/accounts/o8/ud&quot; rel=&quot;openid2.provider&quot; /&gt;
&lt;link href=&quot;https://www.google.com/profiles/PROFILENAME&quot; rel=&quot;openid2.local_id&quot; /&gt;
&lt;link href=&quot;https://www.google.com/accounts/o8/ud&quot; rel=&quot;openid.server&quot; /&gt;
&lt;link href=&quot;https://www.google.com/profiles/PROFILENAME&quot; rel=&quot;openid.delegate&quot; /&gt;</pre></div>
</div>

<p>&nbsp;</p>
<p>Nat&uuml;rlich muss <em>PROFILENAME</em> durch euer eigenes Profil ersetzt werden, in meinem Fall w&auml;re das <em>carsten.ringe</em>. Anschliessend kann man als Open ID-Login immer die eigene Domein angeben. :-)</p>
  
