---
title: "Go_oauth2_password"
date: 2021-04-17T20:18:57+08:00
draft: true
---

```
1、设置密码回调
srv.SetPasswordAuthorizationHandler(passwordAuthorizationHandler)

2、调用 ValidationTokenRequest 验证信息
判断是不是POST 请求
取客户端id, 客户端密码
通过判断GrantType，执行回调密码验证

3、调用GetAccessToken
验证客户端id
如果设置了客户端验证，则执行客户端验证
通过判断GrantType, 执行刷新或者生成token 等操作，这里是生成token


redis 存储（key-value）
access_token 保存basicID
basicID 保存用户信息
refresh_token 保存basicID

保存实现源代码：
pipe := s.cli.TxPipeline()
pipe.Set(s.wrapperKey(refresh), basicID, rexp)
pipe.Set(s.wrapperKey(info.GetAccess()), basicID, aexp)
pipe.Set(s.wrapperKey(basicID), jv, rexp)

设置redis 持久化源码：
mgr.MapTokenStorage(tokenservice.NewRedisStore(&redis.Options{
                Addr:     addr,
	Password: pwd,
}))

access_token 解析网站：
https://jwt.io/

bug :
使用原生代码无法实现单点登录
无法实现redis 集群配置

```



