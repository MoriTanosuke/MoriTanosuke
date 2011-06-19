--- 
wordpress_id: 126
layout: post
title: "Learning Golang #4, oder FizzBuzz Kata"
wordpress_url: http://blog.kopis.de/?p=126
---

    <p><span class="dropCap">H</span>eute habe ich mir eine <a href="http://codingdojo.org/cgi-bin/wiki.pl?KataCatalogue">Kata</a> vorgenommen, und zwar FizzBuzz. Ich schreibe mein Golang immer noch extrem kurz und unleserlich. Solche Dinge wie <code>r[v] = list[v]</code> l&ouml;sen ein schlechtes Gewissen bei mir aus, aber trotzdem bekommt ihr hier den Sourcecode ohne irgendwelche Versch&ouml;nerungen. Wie bei einer Kata &uuml;blich kommt erst der Test, dann der Code:</p>
<p><strong>fizzbuzz_test.go</strong></p>
<p><strong></strong><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package fizzbuzz

import (
    &quot;testing&quot;
)

func TestAnswer(t *testing.T) {
    actual := Answer([]int{1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,60})
    expected := []interface{}{1,2,&quot;fizz&quot;,4,&quot;buzz&quot;,&quot;fizz&quot;,7,8,&quot;fizz&quot;, &quot;buzz&quot;,11,&quot;fizz&quot;,13,14,&quot;fizzbuzz&quot;,&quot;fizzbuzz&quot;}
    for a := range(actual) {
        if actual[a] != expected[a] {
            error(t, &quot;Wrong&quot;, expected[a], actual[a])
        }
    }
}
func error(t *testing.T, message string, expected interface{}, actual interface{}) {
    t.Errorf(&quot;%s: '%s' != '%s'&quot;, message, expected, actual)
}</pre></div>
</div>

</span></p>
<p><strong>fizzbuzz.go</strong></p>
<p><strong></strong><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package fizzbuzz

func Answer(list []int) []interface{} {
    r := make([]interface{}, len(list))
    for v := range(list) {
        switch {
            case list[v] % 3 == 0 &amp;&amp; list[v] % 5 == 0:
                r[v] = &quot;fizzbuzz&quot;
            case list[v] % 3 == 0:
                r[v] = &quot;fizz&quot;
            case list[v] % 5 == 0:
                r[v] = &quot;buzz&quot;
            default:
                r[v] = list[v]
        }
    }
    return r
}</pre></div>
</div>

</span></p>
  
