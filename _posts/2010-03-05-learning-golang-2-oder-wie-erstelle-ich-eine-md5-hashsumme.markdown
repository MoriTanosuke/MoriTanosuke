--- 
wordpress_id: 128
layout: post
title: "Learning Golang #2, oder Wie erstelle ich eine MD5-Hashsumme?"
wordpress_url: http://blog.kopis.de/?p=128
---

    <p><span class="dropCap">W</span>eiter geht's. Diesmal mit der Erstellung einer <a href="http://de.wikipedia.org/wiki/Message-Digest_Algorithm_5">MD5-Hashsumme</a>. Diese Funktion brauchte ich f&uuml;r die Validierung einer API-Anfrage. Dort sollte neben der Argumentliste auch eine Hashsumme der Argumente plus einem geheimen Schl&uuml;ssel &uuml;bermittelt werden. Nach ein paar erfolglosen Versuchen, aus der <a href="http://golang.org/pkg/crypto/md5/">Package Documentation</a> schlau zu werden, <a href="http://stackoverflow.com/questions/2377881/how-to-get-a-md5-hash-from-a-string-in-golang">half mir (wieder einmal) Stackoverflow weiter</a>.</p>
<p>Das ist &uuml;brigens auch der schwierigste Teil von Golang bis jetzt: Herausfinden, welche Funktion man aus einem Package gerade ben&ouml;tigt und vor allem wie man sie aufruft.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package main

import (
    &quot;fmt&quot;
    &quot;crypto/md5&quot;
    &quot;hash&quot;
)

func main() {
    original := &quot;my string comes here&quot;
    var h hash.Hash = md5.New()
    h.Write([]byte(original))
    fmt.Printf(&quot;%s: %xn&quot;, original, h.Sum())
}</pre></div>
</div>

</span></p>
  
