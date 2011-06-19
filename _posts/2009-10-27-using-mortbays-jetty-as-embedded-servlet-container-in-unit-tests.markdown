--- 
wordpress_id: 149
layout: post
title: Using Mortbays Jetty as embedded servlet container in unit tests
wordpress_url: http://blog.kopis.de/?p=149
---

    <p><em>Ich habe diesen Blogeintrag in einem Firmenblog ver&ouml;ffentlicht, daher ist er in Englisch. Und bitte:</em></p>
<p>Today I created a simple unit test that runs <a href="http://www.mortbay.org/jetty/">Mortbays Jetty</a> as an embedded servlet container for a unit test with <a href="http://www.junit.org/">JUnit 4</a>. It's quite simple to run the ServletTester and add Servlets to it, so you can create HTTP requests and assert against the responses.</p>
<p>To run Jetty you need the following JAR files in your classpath:</p>
<ul>
<li>jetty-6.X.Y.jar</li>
<li>jetty-servlet-tester-6.X.Y.jar</li>
<li>jetty-util-6.X.Y.jar</li>
<li>servlet-api-2.5-*.jar</li>
</ul>
<p>The <em>HelloServletTest</em> simple setups Jetty to initialize a servlet, runs one test and stops Jetty after it.&nbsp;The <em>HelloServlet</em> I used for the first test. It's the obvious <em>Hello World</em> example.</p>
<p>Now you can remove HelloServlet, add your own servlet classes and go unit test them. ;-)</p>
<p><p><a href="http://gist.github.com/611340">http://gist.github.com/611340</a></p></p>
  
