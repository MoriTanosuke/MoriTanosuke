--- 
wordpress_id: 50
layout: post
title: Jekyll und related posts mit LSI
wordpress_url: http://blog.kopis.de/?p=50
---

    <p>Ich versuche gerade die&nbsp;related posts&nbsp;verf&uuml;gbar zu machen. Das ist unter Jekyll anscheinend nicht so einfach, denn eine Generierung der Seite mit der Option&nbsp;&ndash;lsi&nbsp;scheint sehr, sehr lange zu dauern, sobald man eine nennenswerte Anzahl an Artikeln hat.</p>
<p>Um diesen Vorgang zu beschleunigen, muss man die&nbsp;<a href="http://www.gnu.org/software/gsl/">GNU Scientific Library</a>&nbsp;installieren und die Bindings f&uuml;r&nbsp;<a href="http://www.ruby-lang.org/de/">ruby</a>. Das ganze gestaltet sich unter Windows und&nbsp;<a href="http://cygwin.com/">Cygwin</a>&nbsp;etwas schwierig. Die Installation vonGSL&nbsp;kann zwar mit dem Cygwin-Setup erledigt werden, aber anschliessend muss das Ruby Gem installiert werden:</p>
<div class="CodeRay">
  <div class="code"><pre>$ gem install gsl
Building native extensions.  This could take a while...
...
wavelet.o:wavelet.c:(.text+0x6d6): undefined reference to `_cNArray'
wavelet.o:wavelet.c:(.text+0x92a): undefined reference to `_cNArray'
wavelet.o:wavelet.c:(.text+0x9df): undefined reference to `_cNArray'
wavelet.o:wavelet.c:(.text+0xccd): more undefined references to `_cNArray' follow
wavelet.o:wavelet.c:(.text+0xcf0): undefined reference to `_na_make_object'
wavelet.o:wavelet.c:(.text+0xf93): undefined reference to `_cNArray'
wavelet.o:wavelet.c:(.text+0x1220): undefined reference to `_cNArray'
wavelet.o:wavelet.c:(.text+0x12d5): undefined reference to `_cNArray'
collect2: ld gab 1 als Ende-Status zur&quot;uck
make: *** [rb_gsl.so] Fehler 1


Gem files will remain installed in /usr/lib/ruby/gems/1.8/gems/gsl-1.12.109 for inspection.
Results logged to /usr/lib/ruby/gems/1.8/gems/gsl-1.12.109/ext/gem_make.out</pre></div>
</div>

<p>Auch der Versuch,&nbsp;<a href="http://rb-gsl.rubyforge.org/">rb-gsl</a>&nbsp;direkt zu installieren, ist mit folgender Meldung gescheitert:</p>
<div class="CodeRay">
  <div class="code"><pre>...
wavelet.o:wavelet.c:(.text+0x12d5): undefined reference to `_cNArray'
collect2: ld gab 1 als Ende-Status zur&quot;uck
make: *** [rb_gsl.so] Fehler 1
setup.rb:655:in `command': system(&quot;make&quot;) failed (RuntimeError)
    from setup.rb:664:in `make'
    from setup.rb:1258:in `setup_dir_ext'
    from setup.rb:1532:in `__send__'
    from setup.rb:1532:in `traverse'
    from setup.rb:1549:in `dive_into'
    from setup.rb:1530:in `traverse'
    from setup.rb:1524:in `exec_task_traverse'
    from setup.rb:1519:in `each'
    from setup.rb:1519:in `exec_task_traverse'
    from setup.rb:1246:in `exec_setup'
    from setup.rb:996:in `exec_setup'
    from setup.rb:826:in `__send__'
    from setup.rb:826:in `invoke'
    from setup.rb:773:in `invoke'
    from setup.rb:1578</pre></div>
</div>

<p>Die Fehlermeldungen sind dabei die gleichen wie bei der Installation des Gem. Woran das jetzt liegt wei&szlig; ich nicht genau, aber es sind auf jeden Fall hausgemachte Probleme mit Windows. :-/</p>
  
