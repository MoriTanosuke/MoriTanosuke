--- 
wordpress_id: 502
layout: post
title: Funktion auf alle Elemente einer Hashmap anwenden
wordpress_url: http://blog.kopis.de/?p=502
---
Ich habe einige Zeit gebraucht, bis ich das folgende Problem in Clojure lösen konnte:

<blockquote>Ich habe eine <code>map</code> mit einigen key-value-Paaren und möchte eine Funktion auf die <code>keys</code> dieser Elemente anwenden. Die Keys sind ausserdem Clojure <code>keywords</code>.
</blockquote>

Heute bin ich dann auf die Lösung gekommen, <a href="http://stackoverflow.com/questions/1676891/mapping-a-function-on-the-values-of-a-map-in-clojure">mein Dank gilt wie so oft Stackoverflow.com</a>.

[clojure]
;; map anlegen
(def m {:foo 'foo, :bar 'bar, :baz 'baz})
;; zipmap erstellt eine neue map aus einer 2 Listen mit Keys und Values
(zipmap (map #(str &quot;key=&quot; %) (keys m)) (vals m))
;; =&gt; {&quot;key=:baz&quot; baz, &quot;key=:bar&quot; bar, &quot;key=:foo&quot; foo}
[/clojure]

Nochmal auf Deutsch: Zeile 4 erstellt mit der Funktion <code>zipmap</code> eine neue <code>map</code> aus der Liste der Keys und Values aus meiner <code>map m</code>.

Wer das jetzt nochmal Schritt für Schritt nachvollziehen will, der kann diese Befehle in die REPL kopieren:

[clojure]
;; Funktion zipmap mit 2 Listen aufrufen
(zipmap [:foo :bar :baz] ['foo 'bar 'baz])
;; =&gt; {:baz baz, :bar bar, :foo foo}
[/clojure]

Das ist im Prinzip identisch zu meinem Aufruf, nur dass ich mit <code>(keys m)</code> und <code>(vals m)</code> die Listen aus meiner bereits existierenden <code>map</code> erstelle.

Meine Beispiele könnt ihr meistens kopieren und in eine REPL einfügen. Ich hab alles, was Fehler verursachen kann, mit Kommentaren versehen.
