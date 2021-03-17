---
title: "Hugocreate"
date: 2021-03-17T19:29:21+08:00
draft: true
---

1、装好git 和hugo 

2、新建博客站点
hugo new site myblog

3、进入myblog/themes 文件夹，下载主题并命名文件夹
git clone https://github.com/vaga/hugo-theme-m10c.git m10c

4、在myblog 文件夹下执行
hugo server -t m10c --buildDrafts

5、在myblog 文件夹下创建md 文件
hugo new post/hugocreate.md


