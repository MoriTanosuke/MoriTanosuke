--- 
wordpress_id: 140
layout: post
title: Things to avoid when creating software
wordpress_url: http://blog.kopis.de/?p=140
---

    <span class="dropCap"><a href="http://coliveira.net/">C</a></span><a href="http://coliveira.net/">arlos Coliveira</a> has another <a href="http://coliveira.net/software/how-to-create-robust-software-designs/">good blog post about robust software design</a>. I like to comment on his thoughts, because this is something that is on my mind every single day when staring at the screen in front of me. Because I'm working in the defense business, I need to care about the long live of software. It's not that releases come out every 8 weeks here, and the software is not replaced after only one or two years. So when you start implementing software, you have to take care about the maintainability and readability of your code, most likely it will be continued by someone else anyway.

Carlos has a good point:
<blockquote class="posterous_medium_quote">
<strong>Avoid useless abstractions</strong>: this is related to the previous topic, but deserves to be treated separately. Abstractions are useful if they simplify the way a feature is implemented. However, some abstractions exist only to satisfy the needs of developers.</blockquote>

<img src="http://posterous.com/getfile/files.posterous.com/import-rzzc/iamjEIiqsntiqIIgsvepkeywvecvBvBdfAqkfmIxEyxitfxyezigioepEJwj/media_httpblogkopisde_sAdvD.jpg.scaled500.jpg" width="300" height="225"/>
I tend to fall into this pit, because I'm a big fan of patterns. And you can throw a bunch of patterns in every day. ;-) But is it always as useful as you might think? I don't think so. Do you really need the plugin mechanism for a simple file access? Do you really have to implement all the interfaces and classes just to be able to add a new kind of transportation container soon? I try to follow <a href="http://en.wikipedia.org/wiki/KISS_principle">KISS</a> and avoid unneccessary code. A good example for this: I created a small servlet that reads LDAP information and displays them on a web page. All implemented as a servlet. Yes, I know, separation of code and display. But do I have to add a templating layer, JSPs, a model and all that if the application is more likely to vanish than to be continued in a few months?

The next tips in <a href="http://coliveira.net/software/how-to-create-robust-software-designs/">Carlos article</a> are good to keep in mind too.
<ul>
	<li><strong>Make it easy to change your implementation</strong></li>
	<li><strong>Avoid using components that will require effort to understand/change</strong></li>
</ul>
A few days after implementing my LDAP information servlet, I was asked to add a way to get information from a remote server. I added XML output to my servlet, placed an instance of it on the remote server, added the ability to read the XML, started a local instance and it was ready to go. I invested some time upfront to get my code clean and separated in methods for easy access, so it was not a problem to add this behavior.

But what's more important: I didn't had to fight with a templating engine, didn't had to add dozens of JSPs and used pure JDK for this changes. I think this little servlet is easy enough to change, so if it don't die in a few months, the next guy can jump right in, read throught my (hopefully clean enough) code and add what is needed then.

Or change to a template engine with an SQL backend, cached LDAP information if the remote host doesn't respond, AJAX for the frontend and a few plugin algorithms and patterns. ;-)
  
