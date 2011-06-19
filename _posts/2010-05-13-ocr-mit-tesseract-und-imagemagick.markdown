--- 
wordpress_id: 111
layout: post
title: OCR mit Tesseract und ImageMagick
wordpress_url: http://blog.kopis.de/?p=111
---

    <p>Vor ein paar Tagen habe ich mir <a href="http://code.google.com/p/tesseract-ocr/">Googles Tesseract</a> <a href="http://www.macosxhints.com/article.php?story=2010021805585497">unter Mac OS X installiert</a> und will damit meinen gescannten Briefe und Rechnungen einen Volltextindex verpassen. Ich scanne allerdings gerne als PNG und Tesseract versteht nur TIFF. Daher m&uuml;ssen die Dateien mit <a href="http://www.imagemagick.org/script/binary-releases.php?ImageMagick=atphnn81to8g8ku2tqbvbgejf5#macosx">ImageMagick</a> konvertiert werden:</p>
<div class="CodeRay">
  <div class="code"><pre>convert -compress none -density 150x150 
    /PFAD/ZUM/BILD.png /PFAD/ZUM/TEMPBILD.tif</pre></div>
</div>

<p>Anschliessend kann man die Datei mit Tesseract durchleuchten lassen und erh&auml;lt eine Textdatei:</p>
<div class="CodeRay">
  <div class="code"><pre>tesseract /PFAD/ZUM/TEMPBILD.tif 
    /PFAD/ZUR/TEXTAUSGABE</pre></div>
</div>

<p>Tesseract h&auml;ngt die Endung <code>.txt</code> selbst an.</p>
  
