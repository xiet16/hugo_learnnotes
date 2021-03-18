---
title: "Go_env_init"
date: 2021-03-18T15:33:27+08:00
draft: true
---
1、登陆https://studygolang.com/dl下载安装包(这里忽略安装过程)

2、环境配置(开启Module和代理，不然可能更新不下来依赖包)

go env -w GO111MODULE=on

go env -w GOPROXY=https://goproxy.io,direct


3、新建项目

(1)首先用vscode 打开一个空文件夹,添加main.go 文件 并编辑好代码

(2)在终端中执行以下命令

go mod init "your_project_name"

go mod tidy

go mod vendor

go modules 我的理解是go 项目依赖包管理。执行 go mod init "xxx" 以后
会生成一个go.mod的文件，这个文件展示的是项目所依赖的依赖包以及版本信息
所以如果要改某个包的版本，可以手动改，然后执行go mod tidy. go mod tidy
是更新依赖包命令，这里包含删除、新增、修改依赖包。go mod vendor 是讲依
赖包下载到vendor 文件夹。顺便提一下，go modules 是1.11后新加的特性之前
是GOPATH的方式


