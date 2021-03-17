---
title: "Hugo_Web_Create"
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

6、生成静态网页(https://github_name.github.io)要用自己名字，不然访问不了
hugo --theme=m10c --baseUrl="https://xiet16.github.io" --buildDrafts

7、编译好的网页放在./public 目录下面，所有要把public文件的内容传到https://github_name.github.io.git仓库上

8、再建一个仓库存myblog 项目就好了

9、上传可以建一个shell脚本

10、git 保存密码命令
 git config --global credential.helper store

