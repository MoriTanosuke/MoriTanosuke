--- 
wordpress_id: 179
layout: post
title: "N\xC3\x83\xC2\xA4chstes Tool: Tail in Java"
wordpress_url: http://blog.kopis.de/?p=179
---

    Tja, schon wieder ein neues kleines Tool: Ich hab gerade tail in Java nachgebaut. F&Atilde;&frac14;r alle, die unter Windows sowas &Atilde;&curren;hnliches suchen. ;-) Den Quelltext gibt es im vollst&Atilde;&curren;ndigen Artikel oder unter <a href="http://wikihost.org/wikis/kopis/programm/gebo.prg?name=prog:tail.java">http://wikihost.org/wikis/kopis/programm/gebo.prg?name=prog:tail.java</a>

Als n&Atilde;&curren;chstes sind noch das Einlesen von STDIN geplant und die Angabe der auszugebenden Bytes per Parameter. Vorschl&Atilde;&curren;ge bitte wieder in die Kommentare. :-)

&lt;!--more-->

<code></code>
<div class="CodeRay">
  <div class="code"><pre>import java.io.File;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.RandomAccessFile;
import java.nio.ByteBuffer;

public class Tail {

        /**
         * Application version.
         */
        private static final String VERSION = &quot;0.1&quot;;

        /**
         * Default number of bytes to show.
         */
        private static final int DEFAULT_LENGTH = 100;

        public static void tail(String filename) throws IOException {
                File f = new File(filename);
                if(!f.exists()) throw new FileNotFoundException();

                RandomAccessFile file = new RandomAccessFile(f, &quot;r&quot;);
                if(file.length() &gt; DEFAULT_LENGTH) {
                        file.seek(file.length() - DEFAULT_LENGTH);
                }
                //go back to last n
                long newPos = file.getFilePointer();
                while(file.read() != 'n') {
                        file.seek(newPos);
                        newPos = file.getFilePointer() - 1;
                }
                // display file
                ByteBuffer buf = ByteBuffer.allocate(DEFAULT_LENGTH * 2);
                int length = -1;
                while((length = file.getChannel().read(buf)) != -1) {
                        System.out.print(new String(buf.array()).trim());
                }
        }

        public static void main(String[] args) {
                if(args.length == 0) {
                        System.out.println(&quot;tail v&quot; + VERSION);
                        System.out.println(&quot;USAGE:ttail &quot;);
                } else {
                        try {
                                Tail.tail(args[0]);
                        } catch (IOException e) {
                                // TODO Auto-generated catch block
                                e.printStackTrace();
                        }
                }
        }

}</pre></div>
</div>
  
