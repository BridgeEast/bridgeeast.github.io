---
layout: post
title: "octopress个人博客搭建"
date: 2013-11-16 16:57
comments: true
categories: 
---
octopress搭建个人博客的方法在网上有很多，在<a href="http://octopress.org/">octopress</a>网站上也有详细介绍,
只要参照教程，很容易就能理解搭建的流程，个人的实现方法如下：

* 安装好ruby和git（已经有ruby开发环境的就不用了）

* 克隆octopress项目，并进行配置

{% codeblock lang:objc %}
git clone git://github.com/imathis/octopress.git blog 
{% endcodeblock %}

* 设置默认ruby版本（如果不使用rvm则不需要）,更新相应的gem

{% codeblock lang:objc %}
rvm use 1.9.3-p374  
bundle update
{% endcodeblock %}

* 安装默认主题

{% codeblock lang:objc %}
rake install
{% endcodeblock %}

<!-- more -->

* 建立一个新的github项目

点击【Create a New Repository】，然后以 用户名/用户名.github.io 的格式建立一个新项目。

* 部署到github上 

{% codeblock lang:objc %}
rake setup_github_pages
{% endcodeblock %}
这条命令会询问你刚才建立的项目的地址，按要求输入;

* 接着执行

{% codeblock lang:objc %}
rake generate
rake deploy
{% endcodeblock %}
上面的命令首先生成博客文件，并将生成的博客文件拷贝到_deploy/目录下，然后将这些内容添加到git中，并commit和push到仓库的master分支。

* 本地生成和预览
{% codeblock lang:objc %}
rake generate
rake watch
rake preview  #在浏览器中输入http://localhost:4000即可预览。
{% endcodeblock %}

* 推送到github
{% codeblock lang:objc %}
git add .
git commit -m"your message"
git push origin source
rake deploy
{% endcodeblock %}

过几分钟后去自己的博客页面就可以看到自己的博客了
理解每句命令的作用，就可以diy自己的博客了。

* 写博客

Octopress的博文存储在source/_posts目录下,并且是按照Jekyll的命名规范对文章进行命名：YYYY-MM-DD-post-title.markdown
通过Octopress提供的task可以正确的按照命名规范创建新博客。
{% codeblock lang:objc %}
rake new_post["title"]
{% endcodeblock %}
其中title为博文的文件名,接着去找到source/_posts/YYYY-MM-DD-title.markdown，编辑它。完成后可以预览和部署博文。
