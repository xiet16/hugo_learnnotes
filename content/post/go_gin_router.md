---
title: "Go_gin_router"
date: 2021-04-05T10:39:49+08:00
draft: true
---

```

1 设置环境(debug release)
2 初始化内核gin.Engine，
3 注册路由 gin.Engine 是一个结构体，结构体中包含RouterGroup，RouterGroup 也是一个结构体，定义如下
        type RouterGroup struct {
            Handlers HandlersChain
            basePath string
            engine   *Engine
            root     bool
        }
  gin.Engine.Use() 方法: 主要是拼接中间件,rebuild404Handlers 和rebuild405Handlers调用的居然是同一个方法，为什么 
    func (engine *Engine) Use(middleware ...HandlerFunc) IRoutes {
        engine.RouterGroup.Use(middleware...)
        engine.rebuild404Handlers()
        engine.rebuild405Handlers()
        return engine
    }

  gin.Engine.RouterGroup.Use() 方法
    func (group *RouterGroup) Use(middleware ...HandlerFunc) IRoutes {
        group.Handlers = append(group.Handlers, middleware...)
        return group.returnObj()
    }
    
    
  gin.Engine 注入action 实际上还是注入RouterGroup
    func (group *RouterGroup) GET(relativePath string, handlers ...HandlerFunc) IRoutes {
        return group.handle(http.MethodGet, relativePath, handlers)
    }

    func (group *RouterGroup) handle(httpMethod, relativePath string, handlers HandlersChain) IRoutes {
        absolutePath := group.calculateAbsolutePath(relativePath)
        handlers = group.combineHandlers(handlers)
        group.engine.addRoute(httpMethod, absolutePath, handlers)
        return group.returnObj()
    }

    func (group *RouterGroup) Group(relativePath string, handlers ...HandlerFunc) *RouterGroup {
        return &RouterGroup{
            Handlers: group.combineHandlers(handlers),
            basePath: group.calculateAbsolutePath(relativePath),
            engine:   group.engine,
        }
    }
  gin.Engine 注入action 例子:两种写法
    router.GET("/swagger/*any", ginSwagger.WrapHandler(swaggerFiles.Handler))
  
    store := sessions.NewCookieStore([]byte("secret"))
	apiNormalGroup := router.Group("/api")
	apiNormalGroup.Use(sessions.Sessions("mysession", store),
		middleware.RecoveryMiddleware(),
		middleware.RequestLog(),
		middleware.TranslationMiddleware())
	{
		controller.ApiRegister(apiNormalGroup)
	}


```





