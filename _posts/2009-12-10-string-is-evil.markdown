--- 
wordpress_id: 139
layout: post
title: String is evil
wordpress_url: http://blog.kopis.de/?p=139
---

    <p><span class="dropCap">O</span>ver the last days I had to fight with legacy sourcecode <strong>again</strong>. It is always hard to figure out what other developers meant years ago when the code was written. But it gets even harder when every single parameter is a <em>String</em>. It's annoying and slows you down, because you always have to look up which format the String should be. Is it maybe an <em>Integer</em>? Or some kind of flag? Or is there more information encoded in this <em>String</em> and do you have to rebuild a strange ASCII format filled with information to call that method?</p>
<p>Truth is, you don't know. You just want to call a method called <em>addToAcl(String role)</em>, but what is that parameter? The name of a role? Or the longer display name of the role? Or is it the UID of the role? How is the UID represented?</p>
<p>I have to deal with legacy sourcecode all the time, sometimes it's <strong>years</strong> old. Often the developers are not available anymore. And there is a lot of string-passing around, integer return codes and other awful things I try to avoid whenever I write code. It's not always possible to avoid it myself, but that doesn't stop me ranting about it here on my blog. ;-) I came upon so many methods were I couldn't tell what I need to pass by reading the method and parameter names. I had to open the method source, look up what it wanted to do with the parameter and then give the right value to the method.</p>
<p>Stephan wrote a <a href="http://codemonkeyism.com/never-never-never-use-string-in-java-or-at-least-less-often/">good article about evil Strings over at codemonkeyism</a>, so I won't give another example here. But if you are tempted to add a integer parameter or a String parameter to any method, ask yourself: Will <em>The Next Guy[tm] </em> know what this parameter means? Or should I use a real object here?</p>
  
