---
title: "Go_tools"
date: 2021-04-07T12:45:12+08:00
draft: true
---


```

(1)编译过程
go tool compile -N -l -S main.go

(2) 查看内存逃逸
go build -gcflags=-m

(3) 查看CPU 和 内存
go tool pprof mem.prof

pprof 工具  runtime/pprof  和 net/http/pprof

go run main.go  -cpuprofile cpu.prof -memprofile mem.prof

查看.prof 文件 
go tool pprof mem.prof

http://127.0.0.1:8880/debug/pprof

go tool pprof http://*:*/debug/pprof/profile

如果你的go程序不是web服务器，而是一个服务进程，那么你也可以选择使用net/http/pprof包，同样引入包net/http/pprof，然后在开启另外一个goroutine来开启端口监听。

比如：

go func() {
        log.Println(http.ListenAndServe("localhost:6060", nil)) 
}()

```




