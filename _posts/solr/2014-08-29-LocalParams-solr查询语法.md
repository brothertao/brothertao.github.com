---
layout: post
category : all
tags : []
---
{% include JB/setup %}


LocalParams
-------------

### 基础语法

功能：为特定的查询参数提供mete-data（描述特定参数）的方法
例子：
q=solr rocks  =>  q={!q.op=AND df=title}solr rocks
格式：
使用{!}包裹后面接特定参数的值foo，例 {!k1=v1 k2=v2 k3=v3}foo, kv用空格分隔
特殊：q={!type=dismax qf='myfield yourfield'}solr rocks 引号内可用\转义

### short-form

q={!dismax qf=myfield}solr rocks  means  q={!type=dismax qf=myfield}solr rocks

### 其他
q={!dismax qf=myfield}solr rocks   means  q={!type=dismax qf=myfield v='solr rocks'}
q={!dismax qf=myfield}solr rocks   means  q={!type=dismax qf=myfield v=$qq}&qq=solr rocks






