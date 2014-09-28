---
layout: post
category : all
tags : []
---
{% include JB/setup %}

config目录下修改
<schemaFactory class="ManagedIndexSchemaFactory">
  <bool name="mutable">true</bool>
  <str name="managedSchemaResourceName">managed-schema</str>
</schemaFactory>
就可以支持通过http rest api添加 字段，貌似没有删除

solr 新的document地址
https://cwiki.apache.org/confluence/display/solr/Apache+Solr+Reference+Guide

lucene设计
http://blog.csdn.net/liweisnake/article/category/1607677

