---
layout: post
title:  "Jekyll 本地调试环境搭建"
categories: [ 前端 ]
author: yld
tag: article
marks: ["前端", "源代码", "Jekyll"]
---

<p>在搭建之前先简单介绍一波JeKyll。Jekyll（发音/'dʒiːk əl/，"杰克尔"）是一个静态站点生成器，它会根据网页源码生成静态文件。它提供了模板、变量、插件等功能，你可以利用它发布一个免费的博客网站，而且还无限流量，不需要服务器，不需要后台。</p>

<p>
Jekyll 本地调试环境搭建
</p>
<ol>

<li>
  <p>安装一个完整的Ruby开发环境<p>
<pre><code>
# Install Homebrew
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
brew install ruby
export PATH=/usr/local/opt/ruby/bin:$PATH
</code></pre>
  <p>其他平台访问：<a href="https://jekyllrb.com/docs/installation/macos/" target="blank">https://jekyllrb.com/docs/installation/macos/</a></p>
</li>

<li>Install Jekyll and bundler gems
<pre><code>gem install jekyll bundler</code></pre>
</li>

<li>Create a new Jekyll site at ./myblog
<pre><code>jekyll new myblog</code></pre>
</li>
<li>Change into your new directory
<pre><code>cd myblog</code></pre>
</li>
<li>Build the site and make it available on a local server
<pre><code>bundle exec jekyll serve</code></pre>
</li>

</ol>

<p>更多详情访问：<a href="https://jekyllrb.com/docs/" target="_blank">https://jekyllrb.com/docs/</a></p>
<pre><code>
bundle init
bundle install
bundle add jekyll
bundle exec jekyll serve
</code></pre>