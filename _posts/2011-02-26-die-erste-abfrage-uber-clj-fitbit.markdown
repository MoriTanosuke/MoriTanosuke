--- 
wordpress_id: 496
layout: post
title: "Die erste Abfrage \xC3\xBCber clj-fitbit"
wordpress_url: http://blog.kopis.de/?p=496
---
Ich arbeite gerade an einer <a href="https://github.com/MoriTanosuke/clj-fitbit">Clojure-Library für die Fitbit API</a> und heute ist mir der erste Request gelungen:

[clojure]
;;REPL started; server listening on localhost:20161.
user=&gt; (use 'example)
Open this URL in your browser: http://api.fitbit.com/oauth/authorize?oauth_token=XXXXXXXXXXXXXXXXXXXXX
Enter your PIN:
XXXXXXXXXXXXXXXXXXXXXXXXXX
{:activities [], :summary {:activeScore 606, :caloriesOut 2516, :distances [{:activity total, :distance 0}], :fairlyActiveMinutes 55, :lightlyActiveMinutes 164, :sedentaryMinutes 630, :steps 8632, :veryActiveMinutes 29}}
nil
user=&gt;
[/clojure]

Jetzt kann ich anfangen, alle API-Methoden in meine Library zu mappen. :-)
