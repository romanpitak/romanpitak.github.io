---
layout: post
redirect_from: "/code/2014/10/31/setting-up-p4merge/"
title:  "P4Merge as a git mergetool and difftool on Linux"
author: "Roman Piták"
last_modified_at: 2014-11-20 18:38
tags: code
perex: |
    Sadly, there's no Sourcetree for Linux. Console it is. Not for merging though. P4Merge 
---

Sadly, no Sourcetree for Linux. Console it is. Not for merging though. P4Merge. 

## P4Merge

[Download P4Merge](http://www.perforce.com/downloads/Perforce/20-User?qt-perforce_downloads_step_3=1#product-10),
extract the archive and create a link (somewhere in your $PATH).

{% highlight bash %}
$ sudo tar \
    --no-same-owner \
    --extract --ungzip \
    --file ~/Downloads/p4v.tgz \
    --directory /opt
$ sudo ln \
    --symbolic \
    /opt/p4v-2014.2.951414/bin/p4merge \
    /usr/bin/p4merge
{% endhighlight %}

`--no-same-owner` ensures the files are owned by the current user (root) and not by whomever created the original archive. 

`--directory /opt` sets the destination (installation) directory for p4v.

## Mergetool

Edit your `~/.gitconfig` file:

{% highlight docker %}
[merge]
        tool = p4merge
[mergetool "p4merge"]
        cmd = p4merge "$BASE" "$LOCAL" "$REMOTE" "$MERGED"
        trustExitCode = true
{% endhighlight %}

## Difftool

Edit your `~/.gitconfig` file:

{% highlight docker %}
[diff]
        tool = p4merge
[difftool "p4merge"]
        cmd = p4merge "$LOCAL" "$REMOTE"
{% endhighlight %}

## Nice to have

This has nothing to do with p4merge, but it makes the `git mergetool` and `git difftool` commands a bit more usable from the console by not asking stupid questions and creating sissy backup files.

Edit your `~/.gitconfig` file:

{% highlight docker %}
[mergetool]
        prompt = false
        keepBackup = false
        keepTemporaries = false
[difftool]
        prompt = false
{% endhighlight %}
