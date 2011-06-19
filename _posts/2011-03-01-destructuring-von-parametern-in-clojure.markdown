--- 
wordpress_id: 513
layout: post
title: Destructuring von Parametern in Clojure
wordpress_url: http://blog.kopis.de/?p=513
---
In Clojure gibt es ein nettes Sprachmittel, um Parameter -oder generell: Elemente aus Listen- herauszuholen. Am häufigsten wird das sicher bei Funktionsparametern eingesetzt. Hier ist ein einfaches Beispiel:

[clojure]
;; Anlegen einer Koordinate
(def coord [3 5])
;; Ausgeben der Koordinaten
(let [[x y] coord]
  (println &quot;x:&quot; x &quot;y:&quot; y))
[/clojure]

Zeile 2 legt eine Koordinate an, bestehend aus 2 Zahlen. Zeile 4+5 <em>destructures</em> die Koordinate und weist den Parametern <code>x</code> und <code>y</code> die Werte aus <code>coord</code> zu. In der Funktion werden die Parameter dann verwendet und als String ausgegeben.

Den gleichen Mechanismus nutzt man eigentlich bei jeder Funktion. Am deutlichsten wurde mir das, als ich das obige Beispiel für beliebig-dimensionale Koordinaten erweitert habe:

[clojure]
;; 3-dimensionale Koordinate anlegen
(def coord [1 2 3])
;; Koordinate ausgeben
(let [[x y &amp; more] coord]
  (println &quot;x:&quot; x &quot;y:&quot; y &quot;others:&quot; more))
;; =&gt; x: 1 y: 2 others: (3)
[/clojure]

Jetzt werden immer noch die ersten beiden Elemente aus der Koordinate geholt, aber der Rest wird durch <code>&amp; more</code> als Liste weitergegeben. Diesen Mechanismus nutzt man oft bei der definition von eigenen Funktionen in Clojure.
