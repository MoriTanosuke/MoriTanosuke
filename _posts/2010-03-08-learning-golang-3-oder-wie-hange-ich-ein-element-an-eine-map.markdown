--- 
wordpress_id: 127
layout: post
title: "Learning Golang #3, oder Wie h\xC3\xA4nge ich ein Element an eine Map?"
wordpress_url: http://blog.kopis.de/?p=127
---

    <p><span class="dropCap">E</span>s mag offensichtlich sein, aber ich will es hier doch noch festhalten: Um ein Element an eine <code>map</code> anzuh&auml;ngen, gen&uuml;gt eine Zuweisung.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package main

import (
    &quot;fmt&quot;
)

func main() {
    var m = map[string]string{&quot;1&quot;:&quot;eins&quot;}
    m[&quot;2&quot;] = &quot;zwei&quot;
    fmt.Println(m)
}</pre></div>
</div>

</span></p>
<p>Diese kleine Programm gibt folgende Ausgabe:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>map[1:eins 2:zwei]</pre></div>
</div>

</span></p>
<p>Daraufhin habe ich diese kleine Testanwendung geschrieben, die eine <code>map[string]string</code> nimmt, ein Argument hinzuf&uuml;gt und anschliessend einen String ausgibt, in dem alle Inhalte der <code>map</code> sortiert enthalten sind.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package main

import (
    &quot;fmt&quot;
    &quot;strings&quot;
    &quot;sort&quot;
)

func gq(m map[string]string) string {
    ma := make([]string, len(m))
    i := 0
    for key,value := range(m) {
        ma[i] = key + &quot;=&quot; + value
        i++
    }
    sort.SortStrings(ma)
    query := strings.Join(ma, &quot;&amp;&quot;)
    return query
}

func main() {
    var m = map[string]string{&quot;1&quot;:&quot;eins&quot;, &quot;acht&quot;:&quot;8&quot;}
    m[&quot;2&quot;] = &quot;zwei&quot;
    query := gq(m)
    fmt.Printf(&quot;result: ?%sn&quot;, query)
}</pre></div>
</div>

</span></p>
<p>Und ja, brauche ich so f&uuml;r meine erste kleine Anwendung von <a href="http://golang.org">golang</a>. :-)</p>
  
