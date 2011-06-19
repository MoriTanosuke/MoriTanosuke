--- 
wordpress_id: 165
layout: post
title: "Gr\xC3\xB6\xC3\x9F\xC5\xB8e des Browsers automatisch anpassen"
wordpress_url: http://blog.kopis.de/?p=165
---

    <p>Nachdem mich <a href="http://www.mozilla-europe.org/de/firefox/">Firefox</a> auf meinem <a href="http://www.apple.com/de/macbook/">Macbook</a> mal wieder mit dem elenden Verhalten des <em>Maximieren auf Vollbild</em> genervt hat, habe ich ein paar Anregungen aus dem Netz zusammengeklaubt und folgendes Bookmarklet erstellt:</p>
<div class="CodeRay">
  <div class="code"><pre>javascript:var%20width%20=%20window.document.documentElement.offsetWidth;%20var%20height%20=%20window.document.documentElement.offsetHeight;%20var%20availWidth%20=%20screen.availWidth;%20var%20availHeight%20=%20screen.availHeight;%20var%20x%20=%20window.screenX;%20var%20y%20=%20window.screenY;%20%20if(height%20&gt;%20availHeight-y)%20{%20%20%20%20%20height%20=%20availHeight-y;%20}%20if(width%20&gt;%20availWidth-x)%20{%20%20%20%20%20width%20=%20availWidth-y;%20}%20%20window.resizeTo(width,height);</pre></div>
</div>
  
