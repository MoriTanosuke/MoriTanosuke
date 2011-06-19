--- 
wordpress_id: 181
layout: post
title: Memory-Mapped Files mit Java
wordpress_url: http://blog.kopis.de/?p=181
---

    <b>Das</b> wu&Atilde;&#159;te ich auch noch nicht:
<blockquote> A region of a file may be <a href="http://java.sun.com/j2se/1.4.2/docs/api/java/nio/channels/FileChannel.html#map%28java.nio.channels.FileChannel.MapMode,%20long,%20long%29"><code></code>mapped<code></code></a>    directly into memory; for large files this is often much more efficient    than invoking the usual <tt>read</tt> or <tt>write</tt> methods.</blockquote>
Weiterlesen in den <a href="http://java.sun.com/j2se/1.4.2/docs/api/java/nio/channels/FileChannel.html#map(java.nio.channels.FileChannel.MapMode,%20long,%20long)">JDK API Docs FileChannel#map(...)</a> und im <a href="http://www.exampledepot.com/egs/java.nio/CreateMemMap.html">Java Almanac e166</a>. Und aufpassen:
<blockquote class="posterous_short_quote"> A mapping, once established, is not dependent upon the file channel  that was used to create it.  Closing the channel, in particular, has no  effect upon the validity of the mapping.</blockquote>
Das ist dann wieder so ein Ding, an dem man sich totsucht, wenn man fremden Code &Atilde;&frac14;bernimmt, oder? ;-)
  
