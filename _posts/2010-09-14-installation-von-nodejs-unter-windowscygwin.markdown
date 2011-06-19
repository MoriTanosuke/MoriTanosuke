--- 
wordpress_id: 55
layout: post
title: Installation von NodeJS unter Windows/cygwin
wordpress_url: http://blog.kopis.de/?p=55
---

    <p style="text-align: left;">Ich versuche seit gestern abend, <a href="http://nodejs.org/">NodeJS</a> ungter Windows 7 (64bit) und <a href="http://cygwin.com/">Cygwin</a> zu installieren. Die notwendigen Pakete von Cygwin sind installiert:</p>
<ul>
<li>python</li>
<li>make</li>
<li>g++ (mingw)</li>
<li>curl</li>
<li>git</li>
</ul>
<p>Anschliessend muss die ash ge&ouml;ffnet werden. Dazu dr&uuml;ckt man WINDOWSTASTE+R und gibt C:cygwinbinash.exe ein. Im daraufhin ge&ouml;ffneten Konsolenfenster gibt man folgendes Kommando ein:</p>
<div class="CodeRay">
  <div class="code"><pre>./rebaseall -v</pre></div>
</div>

<p>Damit werden die Links unter cygwin neu gesetzt. Jetzt sollte alles f&uuml;r die Installation von NodeJS bereit sein. Dazu &ouml;ffnet man eine cygwin-bash und gibt folgende Kommandos ein:</p>
<div class="CodeRay">
  <div class="code"><pre>git clone git://github.com/ry/node.git
cd node
./configure
make
make install</pre></div>
</div>

<p>Jetzt sollte NodeJS installiert sein. Sollte. Denn ich bekomme folgenden Fehler:</p>
<div class="CodeRay">
  <div class="code"><pre>$ ./configure
/cygdrive/c/Users/Carsten Ringe/Documents/workspace/node/wscript: error: Traceback (most recent call last):
  File &quot;/cygdrive/c/Users/Carsten Ringe/Documents/workspace/node/tools/wafadmin/
Utils.py&quot;, line 274, in load_module
    exec(compile(code, file_path, 'exec'), module.__dict__)
  File &quot;/cygdrive/c/Users/Carsten Ringe/Documents/workspace/node/wscript&quot;, line 12, in &lt;module&gt;
    import js2c
  File &quot;/cygdrive/c/Users/Carsten Ringe/Documents/workspace/node/tools/js2c.py&quot;,
 line 35, in &lt;module&gt;
    import jsmin
  File &quot;/cygdrive/c/Users/Carsten Ringe/Documents/workspace/node/tools/jsmin.py&quot;, line 1
    ../deps/v8/tools/jsmin.py
    ^
SyntaxError: invalid syntax</pre></div>
</div>

<p>Das deutet anscheinend auf einen Fehler in der Installation von Python hin. Aber auch nach einer Neuinstallation habe ich noch dieses Problem. Auch das rebase von cygwin bringt keine Verbesserung.  Ich vermute langsam, dass es an meinem 64bit-System liegt. Naja, oder halt an Windows. Deshalb l&auml;uft auch gerade der rsync-Job f&uuml;r das Backup, danach wird doch wieder Ubuntu installiert... gnah.</p>
  
