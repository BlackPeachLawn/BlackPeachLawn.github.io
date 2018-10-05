---
title: 博客工具
layout: post
author: Yi
---





* Atom: 就是你正在用的这个编辑器，用它来写格式为.md的文档
* MarkDown: 是一种文本格式，它有一些特定的“语法规则”来定义文本的格式
* jekyll: 一个可以在本地电脑中渲染blog，提供访问blog服务的工具。<br>
 命令行下运行：<br>
         1. bundle new blog_1 -生成一个blog_1的目录<br>
         2. 进入到bolg_1所在的目录<br>
         3. bundle exec jeklly serve 运行jeklly服务，然后可以在网址 <font color="red">[http://127.0.0.1:4000/]</font> 访问到发布的网页
* GitHub Desktop: github 的可视化客户端，方便于把更改的文件push到github。

___________________________________________



**友情总结**：

  Atom-编辑器 <br>
  MarkDowm(.md)-文本格式<br>
  jekyll-一个可让你不需要网络，在离线的时候也能进行博客编写的工具<br>
  jekyll和github进行完美的配合,用github渲染出来的网页效果和在jekyll提供的本地服务上渲染的效果是一致的。最后所访问的网页，事实上就是github上一个后缀名为.github.io 的项目。所以，写的博客都需要push 到github 的项目之中，最后经github提供的服务进行访问。<br>
  jekyll 和 github 一个线上一个线下，完美搭配。

______________________________________________


***实战操作***：

  <font color="red" face="宋体" size="6">你需要写博客的话，只需要打开Autom（Ctrl+Shift+m 预览）<br>
  新建.md 格式的文件<br>
  用.md的语法规则进行书写。<br>
  然后，到C:\Ruby25-x64\YiBlog\_posts目录下<br>
  命令行运行 bundle exec jekyll serve <br>
  就可以在本地（http://127.0.0.1:4000/） 进行访问调整格式了。<br>
  最后用GitHub Desktop  push到远端BlackPeachLawn.github.io 项目中即可。
  </font>
