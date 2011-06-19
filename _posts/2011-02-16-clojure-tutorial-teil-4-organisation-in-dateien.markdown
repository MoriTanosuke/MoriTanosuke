--- 
wordpress_id: 443
layout: post
title: "Clojure Tutorial, Teil 4: Organisation in Dateien"
wordpress_url: http://blog.kopis.de/?p=443
---
<em>Dies ist der vierte Artikel in einer kleinen Serie, die meine ersten Schritte in der neuen funktionalen Programmiersprache <a href="http://clojure.org/">Clojure</a> dokumentieren soll. Die Artikel werden in unregelmäßigen Abständen hier publiziert.</em>

Bei der Arbeit mit Clojure ist das Standardvorgehen zur Organisation von Sourcecode das Aufteilen von logischen Einheiten von Funktionen in einzelne Dateien. Die Namespaces der Funktionen sollten diese logische Zusammengehörigkeit wiederspiegeln. Ich habe das ganze mal am Beispiel einer sehr einfachen HTML-Bibliothek ausprobiert.
<h2>Datei 1: Hauptprogramm im Namespace <em>FitbitClj.core</em></h2>
<pre class="brush: clojure">(ns FitbitClj.core
  (:use compojure.core
        compojure.handler
        ring.adapter.jetty
        ring.middleware.reload
        ring.middleware.stacktrace
        FitbitClj.html))

; define compojure routes
(site (defroutes test-routes
  (GET "/" {params :params}
    (str (h1 "Testing") (debug (h2 "params") params)))
  (ANY "*" []
    {:status 404, :body "Page not found."})
))

(def app
  (-&gt; (var test-routes)
      (wrap-reload '(FitbitClj.core))
      (wrap-reload '(FitbitClj.html))
      (wrap-stacktrace))
)

(defn dev []
  (run-jetty #'app {:port 8080})
)</pre>
Wie man sieht, verwende ich hier Funktionen wie <code>h1</code> oder <code>debug</code>, um mir ein einige Ausgaben auf einer Webseite anzusehen. Diese Funktionen sind kein Teil von <a href="http://clojure.org">Clojure</a> oder <a href="http://compojure.org">Compojure</a>, sondern selbstgeschrieben und in der Datei <code>FitbitClj/html.clj</code> gespeichert.
<h2>Datei 2: HTML-Bibliothek im Namespace <em>FitbitClj.html</em></h2>
<pre class="brush: clojure">(ns
  #^{:author "Carsten Ringe"
     :doc "Simple HTML formatting"}
  FitbitClj.html)

(defn h1
  ([heading] (str "&lt;h1&gt;" heading "&lt;/h1&gt;")))

(defn h2
  ([heading] (str "&lt;h2&gt;" heading "&lt;/h2&gt;")))

(defn debug
  ([heading elem] (str heading "&lt;pre&gt;" elem "&lt;/pre&gt;")))</pre>
Damit ist mein Hauptprogramm übersichtlich, während das langatmige Erzeugen des HTML-Markups aus dem Blickfeld versteckt ist.
