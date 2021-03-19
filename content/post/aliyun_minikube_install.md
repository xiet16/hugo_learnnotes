---
title: "Aliyun_minikube_install"
date: 2021-03-19T12:17:07+08:00
draft: true
---




```
1、安装docker
2、安装minikube
下载minikube
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-1.9.2-0.x86_64.rpm
sudo rpm -ivh minikube-1.9.2-0.x86_64.rpm

添加k8s 用户
sudo useradd k8s
sudo passwd k8s
sudo usermod -aG docker k8s

chmod u+w /etc/sudoers
vim /etc/sudoers
chmod u-w /etc/sudoers

切换用户 su k8s 环境还是上一个用户的 
su - k8s

3、执行minikube start
minikube start \
    --image-mirror-country=cn \
    --registry-mirror=https://xxx.mirror.aliyuncs.com \
    --image-repository=registry.cn-hangzhou.aliyuncs.com/google_containers \
    --iso-url=https://kubernetes.oss-cn-hangzhou.aliyuncs.com/minikube/iso/minikube-v1.9.0.iso


3、启动 minikube dashboard
minikube dashboard


访问minikube dashboard
http://47.104.237.197:33567/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/#/node?namespace=default

相关url:

https://blog.csdn.net/qq_25951401/article/details/105961820
http://www.bubuko.com/infodetail-3673213.html


curl -Lo minikube https://kubernetes.oss-cn-hangzhou.aliyuncs.com/minikube/releases/v1.13.0/minikube-linux-amd64 && chmod +x minikube && sudo mv minikube /usr/local/bin/
```


