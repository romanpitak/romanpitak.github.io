---
layout: post
title:  "Change Magento's contacts page url"
author: "Roman Piták"
last-revision: 2014-11-03 15:17
categories: code
tags: magento
perex: |
    In my Magento development workflow I strive to avoid any non-code changes and settings when creating the e-shop (and yes - it is possible). 
    That' why I wrote an alternative to creating an unnecessary redirect for customizing the contact page url 
---

Magento does not provide a proper built in way to change the url of the default
contacts page. Some recommend creating a redirect in "Catalog" >> "URL Rewrite
Management", but I find it unnecessary and counterproductive. In my Magento
development workflow I strive to avoid any non-code changes and settings when 
creating the e-shop (and yes - it is possible). 

Changing the url of Magento's contacts page can be as easy as creating 2 files. 

`/app/etc/Zzz_ContactsPageUrl.xml` 

{% highlight xml %}
<?xml version="1.0" encoding="UTF-8"?>
<config>
    <modules>
        <Zzz_ContactsPageUrl>
            <active>true</active>
            <codePool>local</codePool>
        </Zzz_ContactsPageUrl>
    </modules>
</config>
{% endhighlight %}

and `/app/code/local/Zzz/ContactsPageUrl/etc/config.xml`

{% highlight xml %}
<?xml version="1.0"?>
<config>
    <frontend>
        <routers>
            <contacts>
                <args>
                    <frontName>contact-us.html</frontName>
                </args>
            </contacts>
        </routers>
    </frontend>
</config>
{% endhighlight %}

The vital part here is the "vendor name", `Zzz`. Since Magento loads the 
modules alphabetically, modules from the Zzz vendor will be loaded last. This
allows them to overwrite any previously defined settings. 

Although this might be considered a dirty hack by some, I believe it to be the
most elegant solution since it does not create extra database overhead and can
be easily stored in the VCS. 

[All source codes from this article are available for download on Github](https://github.com/romanpitak/Magento-contacts-page-url).
