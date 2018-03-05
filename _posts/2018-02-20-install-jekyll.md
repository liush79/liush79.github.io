---
layout: post
title: Install jekyll
date:   2018-02-20 
description: Install jekyll ..
tags: jekyll
comments: true
---

## Install
{% highlight bash %}
sudo apt-get install ruby-dev
sudo apt-get install ruby
sudo apt-gen install autogen autoconf libtool

sudo gem install jekyll

# If you are using the ubuntu 14.04 version, you MUST update ruby version 2.x before ruby jekyll.
sudo apt-add-repository ppa:brightbox/ruby-ng
sudo apt-get update
sudo apt-get install ruby2.x
sudo apt-get install ruby2.x-dev
{% endhighlight %}

---

