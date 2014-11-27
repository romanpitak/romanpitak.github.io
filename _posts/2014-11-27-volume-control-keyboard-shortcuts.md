---
layout: post
title:  "Volume control with a&nbsp;non-multimedia keyboard on&nbsp;linux&nbsp;Mint&nbsp;17&nbsp;Xfce"
author: "Roman Piták"
last_modified_at: 2014-11-27 10:39
tags: code linux
perex: |
    I&nbsp;used to&nbsp;have a&nbsp;nice multimedia keyboard with all the&nbsp;fancy volume buttons and&nbsp;even a&nbsp;calculator button. 
    I never even noticed them being there until it&nbsp;grew too nasty to look at and&nbsp;I&nbsp;had to have it incinerated and I&nbsp;bought a&nbsp;new&nbsp;one.
    A&nbsp;normal, cheapish, office-grade keyboard. It&nbsp;dawned on&nbsp;me soon after. 
    I'll have to&nbsp;change the&nbsp;volume by&nbsp;clicking on&nbsp;the&nbsp;tray icon and&nbsp;scrolling like a&nbsp;peasant in&nbsp;the&nbsp;middle ages. 
    I&nbsp;decided to&nbsp;deal with it and&nbsp;soon found a&nbsp;viable solution.
    
---

I&nbsp;used to&nbsp;have a&nbsp;nice multimedia keyboard with all the&nbsp;fancy volume buttons and&nbsp;even a&nbsp;calculator button. 
I never even noticed them being there until it&nbsp;grew too nasty to look at and&nbsp;I&nbsp;had to have it incinerated and I&nbsp;bought a&nbsp;new&nbsp;one.
A&nbsp;normal, cheapish, office-grade keyboard. It&nbsp;dawned on&nbsp;me soon after. 
I'll have to&nbsp;change the&nbsp;volume by&nbsp;clicking on&nbsp;the&nbsp;tray icon and&nbsp;scrolling like a&nbsp;peasant in&nbsp;the&nbsp;middle ages. 
I&nbsp;decided to&nbsp;deal with it and&nbsp;soon found a&nbsp;viable solution. 

Run the Keyboard settings for Xfce

<pre class="pitak"><code><span class="user-host">roman@u310 </span><span 
class="path">~ $ </span><span class="function">xfce4-keyboard-settings</span></code></pre>

and add two new shortcuts for the following commands:

<pre class="pitak"><code><span class="user-host">roman@u310 </span><span 
class="path">~ $ </span><span class="function">amixer</span> set Master 5%+
<span class="user-host">roman@u310 </span><span class="path">~ $ </span><span 
class="function">amixer</span> set Master 5%-</code></pre>

You can map it to&nbsp;any&nbsp;free shortcuts you have lying around. I mapped it to 
<strong>Alt</strong>+<strong>*</strong> and&nbsp;<strong>Alt</strong>+<strong>/</strong> 
inspired by the standard mplayer volume shortcuts the first time I was doing it. 

I later discovered this to be quite impractical with all the having to put 
the pizza down to fiddle with the volume, but I was so used to it at that point 
that I never got around to changing it.
Even when setting it up on other computers later on, I still mapped it 
to the same impractical shortcuts and I still have to put my pizza down. 
