--- 
wordpress_id: 168
layout: post
title: Nicht-druckbare Zeichen aus einem String entfernen
wordpress_url: http://blog.kopis.de/?p=168
---

    <p>Ja, ich wei&szlig;. Ich poste zu viel <a href="http://kopis.wordpress.com/category/allgemeines/musik/">Musik</a>. Aber das muss sein!  Jetzt kommt aber noch etwas anderes, n&auml;mlich das Entfernen von nicht-druckbaren Zeichen aus einem String - in <a href="http://java.sun.com/">Java</a>:</p>
<div class="CodeRay">
  <div class="code"><pre>String s = new String(new char[] {0x05, 0x03, 'H', 'E', 'L', 0x10, 'L', 'O'});
String clean = s.replaceAll(&quot;[^\p{Print}]&quot;, &quot;&quot;);
System.out.println(&quot;'&quot; + s + &quot;'&quot;);
System.out.println(&quot;'&quot; + clean + &quot;'&quot;);</pre></div>
</div>

<p>Diesmal ist es ein kleines Beispiel. <a href="http://java.sun.com/j2se/1.4.2/docs/api/java/lang/String.html#replaceAll(java.lang.String,%20java.lang.String)">String#replaceAll</a> verlangt nach einer <a href="http://java.sun.com/docs/books/tutorial/essential/regex/">Regex</a> und <code>\p{Print}</code> trifft alle druckbaren Zeichen. Dementsprechend trifft <code>[^\p{Print}]</code> alle nicht-druckbaren Zeichen. Und schon ist man frei von &uuml;berfl&uuml;ssigem Ballast.  Und wer jetzt bei Regex nur komischen Zeichensalat sieht, der lernt gef&auml;lligst <a href="http://de.wikipedia.org/wiki/Regul%C3%83%C2%A4rer_Ausdruck">die Grundlagen</a> und besorgt sich einen <a href="http://www.vim.org">anst&auml;ndigen Editor</a>, der damit um kann.</p>
  
