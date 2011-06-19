--- 
wordpress_id: 110
layout: post
title: "Tools zur Qualit\xC3\xA4tsanalyse"
wordpress_url: http://blog.kopis.de/?p=110
---

    Weil ich sowieso gerade dabei bin, will ich hier auch noch eine kurze Liste mit meinen Lieblingstools zur Analyse von Codequalit&auml;t posten. Das ganze zielt auf Java als Entwicklungssprache, da ich am meisten dort unterwegs bin.&nbsp;Ich setze diese Tools selbst gern und oft ein und sie k&ouml;nnen ohne Ausnahme auch in einer Continuous Integration (z.B. via <a href="http://hudson-ci.org/">Hudson</a>) eingesetzt werden:
<ul>
	<li>
<a href="http://checkstyle.sourceforge.net/">Checkstyle</a> plus <a href="http://eclipse-cs.sourceforge.net/">Eclipse Plugin</a>
</li>
	<li>
<a href="http://findbugs.sourceforge.net/">Findbugs</a> inkl. <a href="http://findbugs.sourceforge.net/">Eclipse Plugin</a>
</li>
	<li><a href="http://sourceforge.net/projects/eclipse-metrics/">Metrics Plugin</a></li>
	<li>
<a href="http://www.junit.org/">JUnit</a> + <a href="http://cobertura.sourceforge.net/">Cobertura</a>
</li>
	<li><a href="http://code.google.com/p/jmockit/">JMockit</a></li>
	<li>
<a href="http://mercurial.selenic.com/">Mercurial</a> bzw <a href="http://git-scm.com/">Git</a>
</li>
	<li><a href="http://www.vim.org/">VIM</a></li>
</ul>
Welche Tools setzt ihr ein? Und mit welchem Ziel?

(Kleine Anmerkung: Die Beobachtung von Metriken wie Testabdeckung oder LOC macht eigentlich nur Sinn, wenn man historische Daten zur Auswertung speichert. Aber auch w&auml;hrend der Entwicklung, z.B. bei Refaktoring kann man die Kenngr&ouml;&szlig;en im Auge behalten. Tools wie FindBugs und Checkstyle sollten eigentlich immer mitlaufen.)
  
