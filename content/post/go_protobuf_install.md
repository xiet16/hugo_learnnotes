---
title: "Go_protobuf_install"
date: 2021-04-24T23:14:46+08:00
draft: true
---


```
docker pull cap1573/cap-protoc
docker pull thethingsindustries/protoc:3.1.27

docker run -rm -v $(PWD):$(PWD) -w $(PWD) -e ICODE =CF388DF1EFC5EB cap1573/cap-protoc -I  ./  --go_out =./  --micro_out=././*.proto

docker run --rm -v E:/Go/go_micro:E:/Go/go_micro -w E:/Go/go_micro thethingsindustries/protoc:3.1.27 -I  ./  --go_out =./  --micro_out=././*.proto


或者手动在系统中安装(放过gopath 路径下面)  
go get -u github.com/golang/protobuf/proto
go get -u github.com/golang/protobuf/protoc-gen-go
go get -u github.com/micro/micro
go get github.com/micro/protoc-gen-micro/v2

进入文件夹运行生成
protoc -I . --go_out=.  --micro_out=. product.proto
protoc --plugin=protoc-gen-go=C:/Go/bin/protoc-gen-go --plugin=protoc-gen-micro=C:/Go/bin/protoc-gen-micro -I .  --go_out=.  --micro_out=.   product.p
roto

-I 是当前目录寻找
--go_out=plugins=grpc:proto 是依赖这个grpc:proto 这个插件



相关url:
https://blog.csdn.net/zoeou/article/details/86739528

```


