---
layout: post
title:  "Building R 3.3.0 for Debian wheezy"
author: Jens Preussner
tags: make r debian
categories: bioinformatics
---

The R version 3.3.0 was released today (hooray!). It relies on a curl library version of newer than 7.28. Unfortunately, the latest curl available to wheezy is version 7.26. 
Instead of using backports and/or update to a newer curl version from jessie, I decided to have the newest curl in a non-standard directory and reconfigure R to use the newest version:

{% highlight bash %}
cd /tmp
wget https://curl.haxx.se/download/curl-7.48.0.tar.gz
tar xfvz curl-7.48.0.tar.gz
cd curl-7.48.0
./configure --prefix=/some/non/standard/lib/curl
make
make install
{% endhighlight %}

When configuring curl, make sure that *HTTPS* is listed as one of the supported protocols, since the new R version relies on *HTTPS* from curl.

Then, download the R source code, configure and build:
{% highlight bash %}
cd /tmp
wget https://cran.r-project.org/src/base/R-3/R-3.3.0.tar.gz
tar xfvz R-3.3.0.tar.gz
cd R-3.3.0

export LDFLAGS=-L/some/non/standard/lib/curl/lib
export CPPFLAGS=-I/some/non/standard/lib/curl/include

./configure --prefix=/prefix/to/r/3.3.0 --enable-R-shlib
make
make check
make install
{% endhighlight %}

In the code snippet above, we set the two environmental variables *LDFLAGS* and *CPPFLAGS* to the corresponding paths in the curl installation. This will make R use the newest curl.
