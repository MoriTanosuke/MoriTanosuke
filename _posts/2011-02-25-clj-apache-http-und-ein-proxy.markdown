--- 
wordpress_id: 485
layout: post
title: clj-apache-http und ein Proxy
wordpress_url: http://blog.kopis.de/?p=485
---
Falls ihr mal in die Verlegenheit kommen solltet, eine HTTP-Verbindung per <a href="https://github.com/rnewman/clj-apache-http">clj-apache-http</a> debuggen zu wollen (z.B. wegen einer störrischen OAuth-Authorisierung), dann solltet ihr euch <a href="http://www.fiddler2.com/fiddler2/">Fiddler</a> installieren und anschliessend alle Requests durch diesen Proxy leiten. In <a href="https://github.com/rnewman/clj-apache-http">clj-apache-http</a> macht man das wie folgt:

[clojure]
(require ['com.twinql.clojure.http :as 'http])

(:content 
  (http/get (java.net.URI. &quot;http://www.kopis.de&quot;)
    :parameters (http/map-&gt;params {
      :default-proxy (http/http-host
        :host &quot;127.0.0.1&quot; 
        :port 8765)}) :as :string))
[/clojure]
