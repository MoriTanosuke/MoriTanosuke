--- 
wordpress_id: 129
layout: post
title: "Learning Golang #1, oder Wie sortiere ich eine map?"
wordpress_url: http://blog.kopis.de/?p=129
---

    <p><span class="dropCap">G</span>estern habe ich weiter an meiner ersten Applikation in <a href="http://golang.org/">golang</a> gearbeitet und dabei stellte sich mir die Frage, wie man eine <code>map[string]string</code> sortiert. <a href="http://stackoverflow.com/questions/2377881/how-to-get-a-md5-hash-from-a-string-in-golang">Stackoverflow hat (wie immer) weiter geholfen</a>, nachdem ich ein paar Versuche selbst unternommen hatte.</p>
<p>Ich denke, die folgende L&ouml;sung ist nicht das schickste. Sicherlich gibt es eine nette M&ouml;glichkeit, eine <code>map</code> auch mit <code>Channels</code> zu sortieren. Ein <a href="http://de.wikipedia.org/wiki/Bubblesort">BubbleSort</a> sollte damit schnell erstellt sein. Das werde ich beim n&auml;chsten Mal ausprobieren.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package main

import (
    &quot;fmt&quot;
    &quot;sort&quot;
)

func main() {
    m := map[string]string{&quot;b&quot;:&quot;15&quot;, &quot;z&quot;:&quot;123123&quot;, &quot;x&quot;:&quot;sdf&quot;, &quot;a&quot;:&quot;12&quot;}
    mk := make([]string, len(m))
    i := 0
    for k, _ := range m {
        mk[i] = k
        i++
    }
    sort.SortStrings(mk)
    fmt.Println(mk)
}</pre></div>
</div>

</span></p>
  
