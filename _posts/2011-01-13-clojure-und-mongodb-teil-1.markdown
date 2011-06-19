--- 
wordpress_id: 343
layout: post
title: "Clojure Tutorial, Teil 3: MongoDB"
wordpress_url: http://blog.kopis.de/?p=343
---
<!--OffDef-->

<em>Dies ist der dritte Artikel in einer kleinen Serie, die meine ersten Schritte in der neuen funktionalen Programmiersprache <a href="http://clojure.org/">Clojure</a> dokumentieren soll. Die Artikel werden in unregelmäßigen Abständen hier publiziert.</em>

Heute hab ich mit <a href="http://blog.kopis.de/2010/11/30/clojure-tutorial-teil-1/">meinen</a> <a href="http://blog.kopis.de/2010/12/03/clojure-tutorial-teil-2-namespaces/">Gehversuchen</a> in <a href="http://clojure.org/">Clojure</a> weiter gemacht. Diesmal ging's darum, die <a href="http://de.wikipedia.org/wiki/NoSQL">NoSQL</a>-DB <a href="http://www.mongodb.org/">MongoDB</a> anzusprechen. Ich will mir nicht dauernd SQL-Datenbanken wie PostgreSQL oder MySQL ans Bein binden, nur um mich anschliessend mit den elenden <code>JOIN</code>-Statements rumzuschlagen. Meine SQL-Kenntnisse hören so ungefähr bei <code>SELECT * FROM X</code> auf - und so soll das auch bleiben.

Deshalb stand heute ein simples Anwendungsgerüst auf meinem Stundenplan, das eine Webseite zur Verfügung stellt, die Daten aus einer MongoDB liefert. Also, ran ans Werk.

Wer möchte, kann sich <a href="https://github.com/MoriTanosuke/TweetIt">das fertige Projekt von Github holen</a>.

<!--more-->

<strong>Abhängigkeiten von Leiningen verwalten lassen</strong>

Damit ich mich nicht ewig in der Dependency Hell herumirre, hab ich mein Projekt mit <a href="https://github.com/technomancy/leiningen">leiningen</a> aufgesetzt. Das ist ein kleines Tool zur Paketverwaltung, wie man's von Perl &amp; Co kennt. Als erstes braucht man <em>leiningen</em> selbst. <a href="https://github.com/technomancy/leiningen/blob/master/README.md">Dazu lädt man dort das Skript herunter</a>, macht es ausführbar und schon installiert sich die Anwendung. Den Pfad zu <em>leiningen</em> legt man am besten im <strong>PATH</strong> ab.

Anschliessend kann man mit folgender Kommandozeile das neue Projekt anlegen lassen:
<pre>lein new PROJEKTNAME</pre>
Jetzt werden einige Dateien und Verzeichnisse angelegt:
<ul>
	<li>lib - Ordner für Abhängigkeiten</li>
	<li>src - Ordner für Sourcecode</li>
	<li>classes - Ordner für die Kompilate</li>
	<li>project.clj - Projekteinstellungen, enthält auch die Abhängigkeiten</li>
</ul>
Daneben wird auch gleich eine <code>.gitignore</code> angelegt. Sehr praktisch, damit man nicht plötzlich die ganzen Klassen und Bibliotheken eincheckt.

Jetzt müssen noch die Abhängigkeiten in der Datei <code>project.clj</code> eingetragen werden. Da ich eine Webanwendung bauen will, gehören dazu u.A. <a href="https://github.com/weavejester/compojure">compojure</a>, <a href="https://github.com/mmcgrana/ring">ring</a> und der MongoDB-Adapter <a href="https://github.com/somnium/congomongo">congomongo</a>. Hier ist der relevante Teil meiner Projektdatei:
<pre>(defproject tweetit "0.0.1-SNAPSHOT"
  :description "FIXME: no description"
  :dependencies [[org.clojure/clojure "1.2.0"]
                 [org.clojure/clojure-contrib "1.2.0"]
		 [compojure "0.5.2"]
		 [ring/ring-core "0.3.5"]
		 [ring/ring-devel "0.3.5"]
		 [ring/ring-jetty-adapter "0.3.5"]
		 [ring/ring-servlet "0.3.5"]
		 [congomongo "0.1.3-SNAPSHOT"]]
  :main tweetit.clj)</pre>
Jetzt kann <em>leiningen</em> die Abhängigkeiten installieren:
<pre>lein deps</pre>
<strong>Webapplikationen mit Compojure</strong>

Als erstes lege ich die Datei <code>mongo.clj</code> an, die später mit dem Befehl <code>(:use mongo)</code> eingebunden wird. Dort will ich alles sammeln, was mit dem Zugriff auf die <em>MongoDB</em> zu tun hat. Hier ist der Inhalt:
<pre>(ns mongo
  (:use somnium.congomongo))

(defn get-all-notes []
  (let [notes (fetch :notes :only [:title :content])]
    (apply
      str
      (for [note notes]
        (str "<strong>" (:title note) "</strong>" (:content note) "
")
      )
    )
  )
)

(defn add-note []
  (insert! :notes
    {:title "title #1", :content "this is a first note"})
)</pre>
Hier sind zwei Funktionen definiert. Die Funktion <code>get-all-notes</code> liest Dokumente aus der Datenbank <code>notes</code>, die Funktion <code>add-note</code> fügt ein Dokument hinzu. Das ist immer das gleiche Dokument, da ich diese Funktion nur für den ersten Test brauche.

Jetzt muss noch die eigentliche Webanwendung angelegt werden. Dazu lege ich die Datei <code>src/tweetit.clj</code> mit folgendem Inhalt an:
<pre>(ns tweetit
  (:use compojure.core
	ring.adapter.jetty)
  (:use ring.middleware.reload)
  (:use ring.middleware.stacktrace)
  (:use somnium.congomongo)
  (:use mongo)) ; my own file

;; set up congomongo + mongodb
(mongo!
  :db "notes", :host "127.0.0.1")

(defroutes test-routes
  (GET "/" []
    (str "&lt;h1&gt;Testing&lt;/h1&gt;" (add-note) "&lt;br /&gt;" (get-all-notes) "&lt;br /&gt;"))
  (ANY "*" []
    {:status 404, :body "Page not found."})
)

(def app
  (-&gt; (var test-routes)
      (wrap-reload '(tweetit))
      (wrap-reload '(nlp))
      (wrap-reload '(mongo))
      (wrap-stacktrace))
)

(defn dev []
  (run-jetty #'app {:port 8080})
)</pre>
Jetzt nochmal aufgepasst: In der Routendefinition <code>test-routes</code> wird bei einem <code>GET</code>-Request auf <code>/</code> ein String zusammengebaut, der meine Testfunktion <code>add-note</code> aufruft, und anschliessend noch <code>get-all-notes</code> aufruft.
<pre>(str "&lt;h1&gt;Testing&lt;/h1&gt;" (add-note) "&lt;br /&gt;" (get-all-notes) "&lt;br /&gt;"))</pre>
Es wird also bei jedem Aufruf der Seite das gleiche Dokument in die Datenbank geschrieben. Das muss natürlich noch geändert werden, so dass man per Formular das Dokument verändern kann. Aber für heute reicht das erstmal.

<strong>Start der MongoDB</strong>

Bevor die Anwendung gestartet wird, muss natürlich die MongoDB hochgefahren werden. Weil die zwar den Pfad <code>data/db</code> erwartet, ihn aber nicht selbst anlegt, mache ich das schnell selbst. Anschliessend starte ich die MongoDB und gebe den Pfad zum Datenverzeichnis an:
<pre>MONGO_HOME/bin/mongod --dbpath /pfad/zum/parent/verzeichnis # hier muss data/db nicht angegeben werden
Thu Jan 13 20:50:17 MongoDB starting : pid=2661 port=27017 dbpath=. 64-bit
Thu Jan 13 20:50:17 db version v1.6.5, pdfile version 4.5
Thu Jan 13 20:50:17 git version: 0eb017e9b2828155a67c5612183337b89e12e291
Thu Jan 13 20:50:17 sys info: Linux domU-12-31-39-06-79-A1 2.6.21.7-2.ec2.v1.2.fc8xen #1 SMP Fri Nov 20 17:48:28 EST 2009 x86_64 BOOST_LIB_VERSION=1_41
Thu Jan 13 20:50:17 [initandlisten] waiting for connections on port 27017
Thu Jan 13 20:50:17 [websvr] web admin interface listening on port 28017</pre>
Etwas seltsam, aber vielleicht erschliesst sich mir der Grund noch.

<strong>Start der Webanwendung</strong>

Meine Anwendung starte ich jetzt wieder per <em>leiningen</em>. Dazu rufe ich eine REPL auf, lade meinen Sourcecode und rufe anschliessend die Funktion <code>dev</code> auf, die den Jetty-Server hochfährt. Änderungen an meinem Sourcecode werden automatisch geladen und so kann ich das Ergebnis direkt nach dem Neuladen der Seite begutachten.
<pre>$ lein repl
REPL started; server listening on localhost:30939.
=&gt;</pre>
Anschliessend in der REPL:
<pre>=$&gt; (use 'tweetit)
nil
=$&gt; (dev)
2011-01-13 20:49:12.755:INFO::Logging to STDERR via org.mortbay.log.StdErrLog
2011-01-13 20:49:12.757:INFO::jetty-6.1.26
2011-01-13 20:49:12.792:INFO::Started SocketConnector@0.0.0.0:8080</pre>
Jetzt kann ich unter http://127.0.0.1:8080 auf meine Seite zugreifen.
<pre>Testing

{:_id #, :content "this is a first note", :title "title #1"}
title #1this is a first note</pre>
