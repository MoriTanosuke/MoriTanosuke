--- 
wordpress_id: 17
layout: post
title: "Clojure Tutorial, Teil 2: Namespaces"
wordpress_url: http://blog.kopis.de/?p=17
---
<em>Dies ist der zweite Artikel in einer kleinen Serie, die meine ersten Schritte in der neuen funktionalen Programmiersprache <a href="http://clojure.org/">Clojure</a> dokumentieren soll. Die Artikel werden in unregelmäßigen Abständen hier publiziert.</em>

<a href="http://carstenringe.net/clojure-tutorial-teil-1">Im letzten Artikel</a> habe ich in dem erweiterten <a href="http://de.wikipedia.org/wiki/Hallo-Welt-Programm">Hallo Welt</a> eine Var definiert, in der ich die auszugebende Nachricht Hallo Welt abgelegt hatte. Man könnte jetzt glauben, eine Var ist gleichbedeutend mit einer globalen Variable, aber das ist nicht so.
<h2>Namespaces</h2>
In <a href="http://clojure.org/">Clojure</a> sind alle Variablen und Funktionen "gescoped", d.h. mit einem Gültigkeitsbereich belegt. Startet man die REPL, wird automatisch der Namespace "user" angelegt. Man kann den Namespace einfach mit der special form ns wechseln:
<div class="CodeRay">
<div class="code">
<pre>$ java -cp clojure.jar clojure.main
Clojure 1.3.0-alpha3-SNAPSHOT
user=&gt; (ns mynamespace)
nil
mynamespace=&gt;</pre>
</div>
</div>
Mit der Funktion <em>(ns mynamespace)</em> erstelle ich einen neuen Namespace und wechsel direkt dort hinein. Anschliessend kann ich dort Vars und Funktionen erstellen, und zwar ohne explizit den Namespace angeben zu müssen. Allerdings kann ich sie ausserhalb meines Namespaces nur voll qualifiziert referenzieren, d.h. ich muss immer den Namespace mit angeben:
<div class="CodeRay">
<div class="code">
<pre>mynamespace=&gt; (def msg "Hallo Welt")
#'mynamespace/msg
mynamespace=&gt; (println msg)
Hallo Welt
nil
mynamespace=&gt; (ns user)
nil
user=&gt; (println msg)
CompilerException java.lang.Exception: Unable to resolve symbol: msg in this context, compiling:(NO_SOURCE_PATH:5)
user=&gt; (println mynamespace/msg)
Hallo Welt
nil
user=&gt;</pre>
</div>
</div>
Ich habe die Var <em>mynamespace/msg</em> angelegt und anschliessend in einen anderen Namespace gewechselt. Dort habe ich versucht, die Var <em>msg</em> auszugeben, die im Namespace <em>user</em> gar nicht existiert und der Compiler hat das mit einer Fehlermeldung quittiert. Anschliessend habe ich den vollständigen Namen <em>mynamespace/msg</em> verwendet und konnte die Var erfolgreich ausgeben.
<h2>Organisation in Dateien</h2>
Um die Organisation der Quelltexte in Dateien zu vereinfachen, gibt es eine kleine Regel:
<blockquote class="posterous_short_quote">Jede Datei hat ihren eigenen Namespace, die erste Form in einer Datei ist die <em>special form ns</em>.</blockquote>
Wenn man allerdings in einer Datei sehr oft Funktionen eines anderen Namespace verwendet, kann man den Schreibaufwand etwas reduzieren, in dem man alle Funktionen des anderen Namespace in den eigenen importiert. Dazu verwendet man die <em>:use</em> Direktive der <em>special form ns</em>:
<div class="CodeRay">
<div class="code">
<pre>user=&gt; (ns mynamespace (:use clojure.xml))
nil
mynamespace=&gt; parse
#&lt;xml$parse clojure.xml$parse@55a7b0bf&gt;
mynamespace=&gt;</pre>
</div>
</div>
Die seltsame Ausgabe ist Clojures Repräsentation der Funktion <em>parse</em>, das kann jetzt erstmal ignoriert werden. Der springende Punkt ist die Tatsache, dass ich die Funktion <em>clojure/xml/parse</em> ohne Angabe des voll qualifizierten Namen aufrufen kann. Damit werden die eigenen Quelltexte wieder etwas kürzer und hoffentlich lesbarer.
