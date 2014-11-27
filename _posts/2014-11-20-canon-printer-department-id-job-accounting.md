---
layout: post
title:  "How to set up Canon iR-ADV C7260 department&nbsp;ID for job accounting on Mint&nbsp;17"
author: "Roman Piták"
last_modified_at: 2014-11-20 19:12
tags: linux "Mint 17" Canon Printer "job accounting" "department id"
perex: |
    I have, sadly, spent more time than I&nbsp;care to admit trying to&nbsp;get the&nbsp;printer in&nbsp;our&nbsp;office to&nbsp;work.
    In the end, the solution was quite easy, but unintuitive. So I've decided to share it
    
---

I have, sadly, spent more time than I&nbsp;care to admit trying to&nbsp;get the&nbsp;printer in&nbsp;our&nbsp;office to&nbsp;work.
In the end, the solution was quite easy, but unintuitive, so I've decided to share it.  

## Obtain and install the driver

Go to the [Canon software page](http://software.canon-europe.com/), select your
**language** (English), **product** (OfficePrint &&nbsp;Copy Solutions) and&nbsp;**Model** 
(imageRUNNER ADVANCE C7260i) and&nbsp;click&nbsp;**"Go"**. That should get you to 
the&nbsp;[ir-ADV C7260 product software page](http://software.canon-europe.com/products/0011103.asp).   

On the&nbsp;product software page, select your&nbsp;**operating system** (Linux) and&nbsp;**language**
(English) and&nbsp;click&nbsp;**"Submit"**. From the&nbsp;software list below, select the&nbsp;deb&nbsp;package: 
**[CQue 2.0.7 Linux Driver DEB 64-bit (v2.0.7)](http://software.canon-europe.com/software/0045505.asp)**.

Click on the download link for the deb package,
read and accept the Software license agreement, 
and click **"Download Software"**. 
If the download doesn't start automatically, there's also a&nbsp;
[direct link](http://files.canon-europe.com/files/soft45505/software/g1489en_lindeb64_0207.deb).

If you'd like to read some PR about this software, here's 
the&nbsp;[Canon enterprise printing on Linux](http://www.canon-europe.com/For_Work/Solutions/enterpriseprint/#Linux_Printing)
page.

## Install the driver 

Install the deb package into your system. Either with `dpkg` or `gdebi-gtk` if you want a graphical interface.  

{% highlight bash %}
$ sudo dpkg --install ~/Downloads/g1489en_lindeb64_0207.deb
{% endhighlight %}

or

{% highlight bash %}
$ gdebi-gtk ~/Downloads/g1489en_lindeb64_0207.deb
{% endhighlight %}

This will install the **cque-en** package into your system.
The package will be installed mostly into the `/opt/cel/` directory.
There's also a **"Quick" User Guide** (46 pages) and a **Reference Manual** (98 pages) available in `/usr/share/doc/CQue2.0/`.
You can find loads of additional information there. 

## Add a printer to the system

Editing an existing printer with `cque` has never worked for me,
so I'll describe the process of adding a new printer to the system. 

- Start the `cque` graphical interface as root.

{% highlight bash %}
$ sudo cque
{% endhighlight %}

- Select **"File"** >> **"Create"** to add a new printer (queue) to the system.

<img src="{{ site.baseurl }}/public/2014/11/20/01-create-queue.png" alt="Create queue screenshot" />

- Set the **"Queue Type"** to "PostScript"
- **"Name of the queue"** will be the printer name in the system.  
- Click **"Next"**

<img src="{{ site.baseurl }}/public/2014/11/20/02-edit-queue-basic.png" alt="Edit queue screenshot" />

- Select "Remote TCP/IP (9100)" as **"Connection Type"**. 
- Set the **"Printer Hostname or IP Address"** to your printer IP. 
- Specify the **"Port"**. The default port is 9100. 
- Click **"Next"**.

<img src="{{ site.baseurl }}/public/2014/11/20/03-edit-queue-port.png" alt="Edit queue port screenshot" />

- Click **"Browse"** and select the appropriate printer model. 
- Click **"Ok"**.
- Click **"Next"**.

<img src="{{ site.baseurl }}/public/2014/11/20/04-select-queue-model.png" alt="Select printer model screenshot" />

<!--<img src="{{ site.baseurl }}/public/2014/11/20/05-save-queue-model.png" alt="Save printer model screenshot" />-->

- Set the "secured printing" option, if enabled on your printer. 
- Click **"Next"**.

<img src="{{ site.baseurl }}/public/2014/11/20/06-device-options.png" alt="Device options screenshot" />

- If you want to use the "secured printing", enable it again in the "Printing options" again.
- Click **"Create"** to create the printer.

<img src="{{ site.baseurl }}/public/2014/11/20/07-print-options-create.png" alt="Print options screenshot" />

- Click **"Ok"** to confirm the printer creation. 

<img src="{{ site.baseurl }}/public/2014/11/20/08-print-options-confirm.png" alt="Create queue confirm screenshot" />

> At this point it may be necessary to restart `cque`.

- Click on the printer name in the left frame, then click **"Edit"** >> **"Advanced"**.

<img src="{{ site.baseurl }}/public/2014/11/20/09-select-advanced.png" alt="Select advanced edit screenshot" />

- Select **"accounting"**.

<img src="{{ site.baseurl }}/public/2014/11/20/10-select-accounting.png" alt="Select accounting screenshot" />

- Fill in your **"User"**, **"User ID"** (or department ID) and **"Password"**. 
- Select **"Force"** on both **"User ID"** and **"Password"** to enforce the policy.
- Click **"Update"**.

<img src="{{ site.baseurl }}/public/2014/11/20/11-save-accounting.png" alt="Save accounting screenshot" />

- You can now close the window and try to print something. 

## Conclusions

Words of advice in the end: **Do not change the name of the printer once it works**. 
If you change the name in some cups interface, it will not effect the cque settings 
and you'll end up removing the printer in all interfaces and installing it again.  

Good luck and thank you reading this far. As a reward, please enjoy this comic about 
[Printers Sent From Hell To Make Us Miserable](http://theoatmeal.com/comics/printers)
by [the Oatmeal](http://theoatmeal.com/).
