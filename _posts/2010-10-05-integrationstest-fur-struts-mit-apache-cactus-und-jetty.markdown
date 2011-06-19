--- 
wordpress_id: 46
layout: post
title: "Integrationstest f\xC3\xBCr Struts mit Apache Cactus und Jetty"
wordpress_url: http://blog.kopis.de/?p=46
---

    <p>Ich versuche gerade&nbsp;einen Unit-Test f&uuml;r&nbsp;meine Struts-Actions in einem Servlet-Container zu schreiben. Dazu will ich <a href="http://jakarta.apache.org/cactus">Cactus</a> und <a href="http://jetty.codehaus.org/jetty/">Jetty</a> verwenden. Leider hapert es nach dem Einrichten meines <a href="http://eclipse.org/">Eclipse</a>-Projekts beim Start der <a href="http://junit.org/">JUnit</a>-Testsuite:</p>
<div class="CodeRay">
  <div class="code"><pre>java.lang.NoSuchMethodException: org.mortbay.jetty.nio.SelectChannelConnector.setPort(java.lang.String)
        at java.lang.Class.getMethod(Class.java:1078)
        at org.apache.cactus.extension.jetty.Jetty6xTestSetup.createServer(Jetty6xTestSetup.java:374)
        at org.apache.cactus.extension.jetty.Jetty6xTestSetup.setUp(Jetty6xTestSetup.java:210)
        at org.apache.cactus.extension.jetty.Jetty6xTestSetup$1.protect(Jetty6xTestSetup.java:166)
        at junit.framework.TestResult.runProtected(TestResult.java:124)
        at org.apache.cactus.extension.jetty.Jetty6xTestSetup.run(Jetty6xTestSetup.java:175)
        at org.eclipse.jdt.internal.junit.runner.junit3.JUnit3TestReference.run(JUnit3TestReference.java:130)
        at org.eclipse.jdt.internal.junit.runner.TestExecution.run(TestExecution.java:38)
        at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.runTests(RemoteTestRunner.java:460)
        at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.runTests(RemoteTestRunner.java:673)
        at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.run(RemoteTestRunner.java:386)
        at org.eclipse.jdt.internal.junit.runner.RemoteTestRunner.main(RemoteTestRunner.java:196)</pre></div>
</div>

<p>Jetzt bin ich einigermassen verzweifelt, denn <a href="http://jakarta.apache.org/cactus/integration/integration_jetty.html">die Hilfeseite zum Setup von Cactus und Jetty</a> gibt nicht viel her. Also fange ich ein neues Projekt an und erstelle mir eine simple Action, die einen Parameterstring umkehrt und als Attribut in den Request legt und einen Unit Test dazu. Ausserdem werden einige Properties von Cactus ben&ouml;tigt, um den Servlet-Container hochfahren zu k&ouml;nnen.</p>
<p><p><a href="http://gist.github.com/611307">http://gist.github.com/611307</a></p></p>
<p>Leider bringt das nicht den gew&uuml;nschten Erfolg, den die Ausf&uuml;hrung des Tests bringt dieses Fenster zutage:<img src="http://blog.kopis.de/wp-content/uploads/2010/10/SS-2010-10-05_12.05.42.png.scaled500-300x147.png" width="357" height="175"/>
</p>
<p>Damit kann ich im Moment noch gar nichts anfangen. Bis jetzt habe ich meine Junit-Tests immer direkt mit Annotations versehen und konnte sie einfach ausf&uuml;hren. Das Zusammenspiel der TestSuite, des Tests und des Servlet-Containers stimmt anscheinend nicht.</p>
<p><strong>Update</strong> Ich habe jetzt versucht, den Unit Test mit Junit 3 auszuf&uuml;hren und das Ergebnis sieht schon anders aus:</p>
<div class="CodeRay">
  <div class="code"><pre>java.lang.SecurityException: sealing violation: package org.mortbay.jetty is sealed
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:234)
        at java.net.URLClassLoader.access$000(URLClassLoader.java:58)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:197)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:248) </pre></div>
</div>

<p>Also geht's weiter bei <a href="http://www.google.de/search?q=SecurityException:+sealing+violation+cactus+jetty">Google</a> und <a href="http://stackoverflow.com/">Stackoverflow</a>.</p>
  
