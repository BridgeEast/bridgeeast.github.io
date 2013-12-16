---
layout: post
title: "Octopress添加新浪微博秀"
date: 2013-12-16 20:00
comments: true
categories: 
---

* 首先在自己的新浪微博首页中---设置---我的工具---新浪微博秀提取嵌入式代码

* 在source/_includes/asides/添加weibo.html

{% codeblock lang:objc %}

	{_% if site.weibo_uid %}
	<section>
	 <h1>新浪微博</h1>
	 <ul id="weibo">
	   <li>
	     <iframe 
	       width="100%" 
	       height="550" 
	       class="share_self" 
	       frameborder="0" 
	       scrolling="no" 
	       src="http://widget.weibo.com/weiboshow/index.php?width=0&height=550&ptype={% if site.weibo_pic %}1{% else %}0{% endif %}&speed=0&skin={{weibo_skin}}&isTitle=0&noborder=1&isWeibo={% if site.weibo_show %}1{% else %}0{% endif %}&isFans={{weibo_fansline}}&uid={{site.weibo_uid}}&verifier={{site.weibo_verifier}}">
	     </iframe>
	   </li>
	 </ul>
	</section>
	{_% endif %}
	
{% endcodeblock %}

<!-- more -->

* 在_config.yml里添加

{% codeblock lang:objc %}

default_asides: [asides/recent_posts.html, asides/github.html, asides/weibo.html]

# Weibo
# Please refer to http://weibo.com/tool/weiboshow to get your uid and verifier. 
weibo_uid: 1098907490
weibo_verifier: abd54ad9
weibo_fansline: 0   # 粉丝显示多少行
weibo_show: true    # 是否显示最近微博内容
weibo_pic: true     # 是否显示微博中的图片
weibo_skin: 10      # 使用哪种配色风格，数字为从1开始的微博秀风格序号

{% endcodeblock %}

就ok了,可以去预览下效果了