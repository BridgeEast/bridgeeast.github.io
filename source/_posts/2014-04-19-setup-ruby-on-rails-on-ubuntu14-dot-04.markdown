---
layout: post
title: "Setup ruby on rails on ubuntu14.04"
date: 2014-04-19 16:11
comments: true
categories: 
---

昨天刚发布的ubuntu14.04，今天就想体验下新系统的新鲜感，于是折腾了一下，配上ruby on rails的开发环境。失败了很多次，因为是新系统，默认的更新源里没有全面的依赖。

## 所以安装前先更新源。

* 先备份源列表:

{% codeblock lang:objc %}
  sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
{% endcodeblock %}

* 然后打开 sources.list

{% codeblock lang:objc %}
  sudo vim /etc/apt/sources.list 
{% endcodeblock %}

* 替换为官方提供的更新源：

{% codeblock lang:objc %}
  deb http://archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
  deb http://archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
  deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
  deb http://archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe multiverse
  deb http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu/ trusty main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu/ trusty-proposed main restricted universe multiverse
  deb-src http://archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
  Ubuntu官方提供的其他软件（第三方闭源软件等）：
  deb http://archive.canonical.com/ubuntu/ trusty partner
  deb http://extras.ubuntu.com/ubuntu/ trusty main
{% endcodeblock %}

## 然后就可以参考12.04的方法安装了

* 其它一些依赖
{% codeblock lang:objc %}
  sudo apt-get install bison build-essential zlib1g-dev libssl-dev libreadline5-dev libxml2-dev build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion
{% endcodeblock %}

<!-- more -->


