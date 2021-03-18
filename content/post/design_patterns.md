---
title: "Design_Patterns"
date: 2021-03-18T08:51:04+08:00
draft: true
---

设计模式七大原则  

代码网址:

https://github.com/xiet16/go_design_patterns


开闭原则: 对扩展开放，对修改关闭  

理解: 当新增某一功能时，应该与原有的代码逻辑没有关系，也就是不需要修改原有的代码  

里式替换原则:父类出现的任何地方，都可以用子类替换  

理解:面向对象继承的体现，子类继承父类，子类就拥有父类的一切行为和属性

单一职责原则:一个类有且仅有一个引起它变化的原因，否则这个类就需要拆分

依赖倒置原则:抽象不依赖于具象，具象依赖抽象

理解:抽象类或者父类不关心继承类的实现，但是继承类要实现抽象类的约定

接口隔离原则:客户端不应该去依赖一个它不使用的接口(一个类对另一个类的依赖，应该在最小的接口上)

理解:某一功能接口的定义或者暴露，应该是尽可能少和紧密相关的

(迪米特原则)最少知道原则:高内聚

理解:后面这两个原则，暂时不做解释，虽有点的理解

合成复用原则:

理解:这个原则是说用组合的方式而不是继承的方式复用，但是我觉得要是具体场景，原则性不是很强

