--- 
wordpress_id: 97
layout: post
title: "Bash: Kommando f\xC3\xBCr alle Zeilen einer Datei ausf\xC3\xBChren"
wordpress_url: http://blog.kopis.de/?p=97
---

    <p>Dieser Einzeiler liest eine Datei und f&uuml;hrt ein Kommando f&uuml;r jede Zeile aus:</p>
<div class="CodeRay">
  <div class="code"><pre>while read file; do git add $file; done</pre></div>
</div>

<p><strong>Achtung </strong>Leider verschmiert der Syntax-Highlighter das '&lt;' zu einem <strong>&amp; lt ;</strong> - Schaut euch bitte den Quelltext des Schnippsels an.</p>
  
