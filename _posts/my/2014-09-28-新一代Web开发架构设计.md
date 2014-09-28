---
layout: post
category : all
tags : []
---
{% include JB/setup %}


新一代Web开发架构设计
三层:应用层(负责API的提供),API代理层,Render层

原则: 系统之间通过rest api通信

缓存策略,消息系统

场景问题:
API间互相访问同样要走API代理层

优点:
层次简单清晰
各个层次间耦合性非常低
提高生产效率
便于模块化
便于部署
安全性增强
可用性增加
可以作为统一化产品提供
便于形成各个层次间的标准化开发框架,如前端开发框架,API代理层开发框架,权限DSL,业务DSL
便于优化
便于业务抽象化

rest api相对于rpc的优缺点


各层的作用:
render层,通过请求内部API获取需要的数据进行渲染.其中URL在此层的处理需要考虑,包含生成,参数处理变化

API代理层负责API的访问管理,授权逻辑.要有内外API的标志字段.需要有后台管理界面

权限需求
editor 只可以编辑自己写的文章

流程
同一个URI下有权限逻辑的
editor登录,请求post /blog/1,gateway check blog[1].ownerid==editor.uid
关键点,权限业务逻辑中ownerid如何获取:
1:gateway发起网络请求R1(/bussiness-server/blog/1)获取blog对象

URI:get /blog/[id]
上海的editor只能看上海的blog
GET user`s tags and tags order
GET blog=1 的信息
判断 user.geo = blog.geo

同一个URI无权限逻辑
URI:get /blog/[id]

管理
权限管理员登录gateway系统,添加URI:/blog/1 post

debug tool
一次请求,勾画出所有关键点数据的生成变化,利于查找bug

非实时性的job使用url访问式调度
