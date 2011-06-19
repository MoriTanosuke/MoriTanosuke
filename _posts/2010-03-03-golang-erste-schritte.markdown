--- 
wordpress_id: 130
layout: post
title: "golang: Erste Schritte"
wordpress_url: http://blog.kopis.de/?p=130
---

    <p><span class="dropCap">I</span>ch bin in den letzten Tagen wieder &ouml;fter auf <a href="http://golang.org/">Go</a> gestossen, <a href="http://www.google.com/">Googles</a> neue Programmiersprache. Und jetzt habe ich beschlossen, das ganze auch auszuprobieren - obwohl mir die Syntax erstmal nicht gef&auml;llt. Zu nah an C, zu viele Pointer... ;-) Aber trotzdem bin ich an neuen Inputs in Sachen Softwareentwicklung interessiert und gerade die Ausrichtung auf Mehrprozessorsysteme und message-basierte Anwendungen hat eine gro&szlig;e Anziehungskraft. Also richte ich mir eine kleine Linux-VM ein und installiere alle notwendigen Pakete f&uuml;r <strong>Go</strong> (und ab jetzt werde ich mit <em>golang</em> auf die Sprache verweisen, denn 2 Buchstaben sind einfach zu wenig f&uuml;r eine Suchmaschine...).</p>
<p><strong>Mercurial</strong></p>
<p><strong></strong> Als erstes wird <a href="http://mercurial.selenic.com/">Mercurial</a> installiert, da ich auf die neuste Version von Golang zugreifen m&ouml;chte. Unter <a href="http://www.debian.org/">Debian</a> geht das mit folgendem Kommando:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>$ apt-get install mercurial</pre></div>
</div>

</span></p>
<p><strong>Golang</strong></p>
<p><strong></strong> Seltsamerweise konnte ich nicht zu 100% der <a href="http://golang.org/doc/install.html">offiziellen Installationsanleitung</a> folgen. Meine Installation von Mercurial wollte das Repository partout nicht &uuml;ber <a href="http://de.wikipedia.org/wiki/Hypertext_Transfer_Protocol_Secure">HTTPS</a> klonen. Aber <a href="http://code.google.com">Google Code</a> liefert <a href="http://go.googlecode.com/hg">das Golang-Repository auch &uuml;ber HTTP</a> und damit bin ich schliesslich zum Ziel gekommen:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>$ export GOROOT=/pfad/zu/go # Standard ist $HOME/go
$ export GOARCH=386
$ export GOOS=linux
$ hg clone -r release http://go.googlecode.com/hg/ $GOROOT</pre></div>
</div>

</span></p>
<p>Um Golang selbst zu bauen, m&uuml;ssen noch ein paar Tools der <a href="http://gcc.gnu.org/">GCC</a> Toolchain installiert werden:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>$ apt-get install bison gcc libc6-dev ed gawk make</pre></div>
</div>

</span></p>
<p>Da ich zum Zeitpunkt der Installation hinter einem Proxy sass, musste ich die Testcases f&uuml;r die Pakete <strong>http</strong> und <strong>net</strong> in der Datei <tt>$GOROOT/src/pkg/Makefile</tt>&nbsp;deaktivieren:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>NOTEST =  # nach dieser Zeile einfügen
    http
    net
    ... # hier geht das Original weiter</pre></div>
</div>

</span></p>
<p>Anschliessend kann muss das Zielverzeichnis f&uuml;r die Binaries erstellt und Golang gebaut werden:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>$ mkdir $HOME/bin # Standardverzeichnis, umzusetzen über $GOBIN
$ cd $GOROOT/src
$ ./all.bash</pre></div>
</div>

</span></p>
<p>Wenn alles glatt geht, dann sollte folgende Ausgabe kommen:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>--- cd ../test
0 known bugs; 0 unexpected bugs</pre></div>
</div>

</span></p>
<p><strong>Hallo Welt</strong></p>
<p><strong></strong> Jetzt folgt das erste Programm, in sch&ouml;ner Tradition nat&uuml;rlich ein <em>Hello World</em>. Einfach den Lieblingseditor starten und folgenden Text eingeben:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>package main

import fmt 'fmt'  // Package implementing formatted I/O.

func main() {
    fmt.Printf('Hello, World!')
}</pre></div>
</div>

</span></p>
<p>Anschliessend wird das Programm kompiliert:</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>$ ~/bin/8g helloworld.go
$ ~/bin/8l helloworld.8
$ ./8.out
Hello, World!</pre></div>
</div>

</span></p>
  
