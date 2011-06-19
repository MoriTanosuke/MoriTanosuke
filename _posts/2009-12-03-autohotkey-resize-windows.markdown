--- 
wordpress_id: 143
layout: post
title: "Autohotkey: Resize windows"
wordpress_url: http://blog.kopis.de/?p=143
---

    <p><span class="dropCap">I</span> was tired of moving and resizing windows by hand, so I created a small script for <a href="http://www.autohotkey.com/">AutoHotKey</a> that allows quick window organization. I added only what I need right now, so you have the following actions:</p>
<ul>
<li>WIN+Up: Maximize current window</li>
<li>WIN+Down: Restore current window</li>
<li>WIN+Left: Put window to the left side of the screen</li>
<li>WIN+Right: Put window to the right side of the screen</li>
</ul>
<p>The <em>Left/Right</em> actions are really useful if you like to work in splitscreen mode. I do that often, so this comes in handy. I think this little script allows for quick modification, so feel free to add any functionality you like to have.</p>
<p><span style="font-family: Times New Roman; font-size: medium;">
<div class="CodeRay">
  <div class="code"><pre>#InstallKeybdHook
#Up::WinMaximize A
#Down::WinRestore A
#Left::LeftHalfWindow()
#Right::RightHalfWindow()

LeftHalfWindow()
{
SysGet, area, MonitorWorkArea
w:=((areaRight-areaLeft)/2)
h:=(areaBottom-areaTop)

WinRestore, A
WinMove, A, , 0, 0,%w%,%h%
}

RightHalfWindow()
{
SysGet, area, MonitorWorkArea
w:=((areaRight-areaLeft)/2)
h:=(areaBottom-areaTop)

WinRestore, A
WinMove, A, , w, 0, w, h   ;Middle of screen is same as w.
}</pre></div>
</div>

</span></p>
  
