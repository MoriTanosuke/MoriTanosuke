--- 
wordpress_id: 145
layout: post
title: Code Coverage - what are we talking about?
wordpress_url: http://blog.kopis.de/?p=145
---

    <p>Today <a href="http://groups.google.com/group/jmockit-users/browse_thread/thread/42fc076e61843907">an interesting discussion</a> about the definition of <a href="http://en.wikipedia.org/wiki/Code_coverage">code coverage</a> took place in the <a href="http://groups.google.com/group/jmockit-users">JMockit Users group</a>. I hope my english was good enough to follow the details and maybe contribute something useful. ;-)</p>
<p>There was a bit of a confusion about the kind of coverage analysis <em>JMockIt</em> does for its coverage reports. For me, as an <a href="http://www.istqb.org/">ISTQB certified tester</a>, the german terms <a href="http://de.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren#C0._Anweisungs.C3.BCberdeckungstest_.28Statement_Coverage.29">Anweisungs&uuml;berdeckung</a>, <a href="http://de.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren#C1._Zweig.C3.BCberdeckungstest_.28Branch_Coverage.29">Zweig&uuml;berdeckung</a> and <a href="http://de.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren#C2._Pfad.C3.BCberdeckungstest_.28Path_Coverage.29">Pfad&uuml;berdeckung</a> have a clear meaning. It's based on the ISTQB definitions. The german Wikipedia article <a href="http://de.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren">Kontrollflussorientierte Testverfahren</a> has a good explanation of all the different coverage analysis. (Including the <a href="http://de.wikipedia.org/wiki/Kontrollflussorientierte_Testverfahren#C3._Bedingungs.C3.BCberdeckungstest">Bedingungs&uuml;berdeckung</a>, which you can have the most fun with. And with fun I mean sleepless nights of whitebox testing... ;-))</p>
<p>Unfortunatly most of the tools doing some kind of code coverage analysis try to explain their metrics without the use of control flow graphs or any other kind of graphical representation. I think this adds to the confusion.</p>
<p>Using real world terms like <em>branch</em> and <em>path</em> don't help to clear things up either. That 100% branch coverage means empty branches too isn't very clear for the beginner who thinks of a branch as a real world thing.</p>
<p>After all this discussion shows once again, that you really have to know the metrics you use or chance is good you're measuring the wrong things.</p>
  
