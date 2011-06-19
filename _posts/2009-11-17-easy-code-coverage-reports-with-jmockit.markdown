--- 
wordpress_id: 146
layout: post
title: "Easy code coverage reports with JMockIt "
wordpress_url: http://blog.kopis.de/?p=146
---

    <p>In this blog post I want to describe how I use <a href="http://code.google.com/p/jmockit/">JMockIt</a> not only for stubs &amp; mocks, but for easy generation of code coverage reports while developing.  <a href="http://code.google.com/p/jmockit/">JMockIt</a> is my favorite tool for unit testing, because of it's ease of use and the many options you get out of this framework. Only recently I decided to try the code coverage report that comes with JMockIt. I was searching for an easy way to monitor my test coverage while continuing development. I didn't want another tool or another VM running a fancy code review tool. I just wanted to see what my current test cases are covering.</p>
<p><strong>My class &amp; test</strong></p>
<p><strong>&nbsp;</strong> For all of you wanting to get working code I give you a <a href="http://codingdojo.org/cgi-bin/wiki.pl?KataCatalogue">code kata</a> that I created earlier. It's the <a href="http://codingdojo.org/cgi-bin/wiki.pl?KataFizzBuzz">FizzBuzz kata</a>, and it is already prepared to run with JMockIt. You can <a href="http://blog.kopis.de/wp-content/uploads/2009/11/fizzbuzzkata.zip">download a full eclipse project from my personal blog</a>.</p>
<p><p><a href="http://gist.github.com/615405">http://gist.github.com/615405</a></p></p>
<p><strong>How to create reports</strong></p>
<p><strong></strong> To create code coverage reports with JMockIt you don't have to go to hours and hours of tool setup before you get something done. Just drop these JAR in your classpath and you're setup to go:</p>
<ul>
<li>jmockit.jar</li>
<li><del>jmockit-coverage.jar</del></li>
<li>jmockit-coverage-html[basic|full].jar</li>
<li><del><em>JDK_HOME</em>/lib/tools.jar</del></li>
</ul>
<p><del datetime="2009-11-18T08:53:23+00:00">When you're working inside <a href="http://eclipse.org/">Eclipse</a> I recommend adding the tools.jar as a user library. See the <a href="http://help.eclipse.org/ganymede/index.jsp?topic=/org.eclipse.jdt.doc.user/reference/preferences/java/buildpath/ref-preferences-user-libraries.htm">Eclipse documentation</a> for some help with that.</del></p>
<p><del datetime="2009-11-18T08:53:23+00:00"></del> <strong>Update:</strong> With Version 0.933+ you don't need the JDK <tt>tools.jar</tt> nor the <tt>jmockit-coverage.jar</tt> in your classpath anymore. That reduces the setup to 2 JAR files. Notice that you only need the <tt>jmockit-coverage-htmlbasic.jar</tt> if you intend to view the report only in Eclipse. The FULL report has additional information, that might be useful to you, but I prefer fast tests and simple reports while developing. <a href="http://blog.kopis.de/2009/11/17/easy-code-coverage-reports-with-jmockit/comment-page-1/#comment-1044">Thanks for the tips, Rog&eacute;rio</a>.</p>
<p>Now run your <a href="http://www.junit.org/">JUnit test</a> and you get a directory coverage-report with an index.html file in it. Open it in your favorite browser (or with the <a href="http://eclipse.org/home/categories/index.php?category=enterprise">Eclipse/Java EE</a> internal web browser) and you see a report like this:  <a href='http://posterous.com/getfile/files.posterous.com/import-rzzc/icmkDfhzIspophGIJduBHrhcEIczumHpqekhIspacmljgjIvEFvgqmqnGJEB/media_httpwikikopisde_teBrb.png.scaled1000.png'><img src="http://posterous.com/getfile/files.posterous.com/import-rzzc/icmkDfhzIspophGIJduBHrhcEIczumHpqekhIspacmljgjIvEFvgqmqnGJEB/media_httpwikikopisde_teBrb.png.scaled500.png" width="500" height="185"/></a>
</p>
<p>When you dig into the FizzBuzz.java you see the details:</p>
<p><a href='http://posterous.com/getfile/files.posterous.com/import-rzzc/arqBfqvBovfsGDBGbnGeuqanvzujBneymkcDaFCrnuJamAoxlqeErhfHFHaE/media_httpwikikopisde_oqBeg.png.scaled1000.png'><img src="http://posterous.com/getfile/files.posterous.com/import-rzzc/arqBfqvBovfsGDBGbnGeuqanvzujBneymkcDaFCrnuJamAoxlqeErhfHFHaE/media_httpwikikopisde_oqBeg.png.scaled500.png" width="500" height="446"/></a>
</p>
<p>Do you smell something? What is that red line about? Is there code that is redundant or maybe plain wrong? Is the testcase testing the wrong things or taking false results for true? If you stumble upon something like this, this is the point where you notice that quick coverage reports are worth the setup time.</p>
<p>There is also a way of creating the reports from your ant script. But I'll save that for a later blog post. If you want to try it yourself, go read the official documentation about JVM parameters.</p>
<p><strong>What I think about it</strong></p>
<p><strong></strong> This is as easy as code coverage gets: Covered lines are green, uncovered lines are red. You even get a little counter before each line telling you how many times this line was hit. Searching for performance bottlenecks? Start looking on high line counters. A whole method appearing in red? Examine the preconditions and write a test that calls that method.</p>
<p>Best thing on JMockIt coverage reports is: They don't slow down your tests very much. You can just drop the JARs in your classpath and continue with your unit testing. If you want to check on your current coverage status, open the report and take a quick look. I think this is easy enough for every developer to integrate into his process. And you are already doing unit tests, right? So it shouldn't take you more than a few mouse clicks to get a first coverage report...</p>
  
