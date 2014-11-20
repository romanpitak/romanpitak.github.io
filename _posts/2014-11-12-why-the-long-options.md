---
layout: post
title:  "Why the long options?"
author: "Roman Piták"
published: 2014-11-12 21:34
last-revision: 2014-11-12 21:34
tags: code linux
perex: |
    Nobody really needs a short answer when looking to understand something.
    When I'm writing a script (or a blog post), chances are somebody is going to (have to) look at it at some point.
    Whether a devoted reader or an unlucky colleague (or me) two years from now, 
    long switches are like helpful little inline documentation.
---

Short answer - [Readability](http://en.wikipedia.org/wiki/Readability).

Long answer - short answers are for pricks. Nobody really needs a short answer when looking to understand something.
When I'm writing a script (or a blog post), chances are somebody is going to (have to) look at it at some point.
Whether a devoted reader or an unlucky colleague (or me) two years from now, 
long switches are like helpful little inline documentation. 
They make me a bit less pissed at my past self for writing things like this:
  
{% highlight bash %}
###################################################
#     _____    # 
# ^..^     \9  # WARNING - following source code
# (oo)_____/   #           may harm your eyes
#    WW  WW    #
###################################################
{% endhighlight %}

## Leave better code for "generations" to come

Yeah, let the future me worry about that. So much for professionals. 

The one thing that set me off on the path to the long arguments more than anything else 
was [this comic](http://xkcd.com/1168/) by [Randall Munroe](http://xkcd.com/about/):  

<a href="http://xkcd.com/1168/" target="_blank"><img src="http://imgs.xkcd.com/comics/tar.png" /></a>

It has no direct connection to long options and --in-all-honesty -
I don't remember the long options of `tar` while I do remember the short ones. 
But the point is this: 

> **Think about what you are writing and about the people who will be forced to read it**.

## Save yourself a trip to the man page

Consider this piece of code:

{% highlight bash %}
$ git config --global core.pager "less -FRSX"
{% endhighlight %}

My first reaction was `man ls` and a rewrite to: 

{% highlight bash %}
$ git config --global core.pager "\
less \
--quit-if-one-screen \
--RAW-CONTROL-CHARS \
--chop-long-lines \
--no-init"
{% endhighlight %}

Now, whenever I have to revise my `.gitconfig`, I can clearly see - or at least I have a faint idea of - what I was trying to achieve.   

Don't get me wrong. I am a strong believer in the 80 characters soft limit on line length, but that's what backslashes are for.
Escaping is inescapable.

## Discover new possibilities

Some (although admittedly not many) switches are only available in the long form. 

{% highlight bash %}
$ alias ls="ls \
--color=always \
--time-style=\"+%Y-%m-%d %H:%M:%S\" \
--human-readable"
{% endhighlight %}

In the above example, the switches `--color` and `--romanpitak.github.iotime-style` are only available in the long form because they are intended to be used in scripts.   

## Maintain laziness

The short form of the options is for typing the commands on the interactive shell. 
The long term is for the scripts. 
Seeing the long form helps you understand what the switch does immediately. 

A little more typing now, a lot less typing later. 

Laziness is maintained. 



