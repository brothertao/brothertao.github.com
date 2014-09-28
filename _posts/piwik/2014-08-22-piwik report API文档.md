---
layout: post
category : all
tags : []
---
{% include JB/setup %}


API Request
===================

标准API参数(Standard API parameters)
-------------

idSite

  - 监控网站的ID（可以在Athena后台看）
  - 可以传递多个，例如：idSite=1,4,5,6
  - 全部：idSite=all
period
报表数据区间，例如：day, week, month, year或者自定义一个范围

  - day 返回指定那天的数据
  - week 返回指定某天(date=YYYY-MM-DD,YYYY-MM-DD)所在周的数据
  - month 同上
  - year 同上
  - range 同上

date

  - 标准格式：YYYY-MM-DD
  - 语义关键字 today或yesterday（具体和你所设置的timezone有关）. 具体你懂的,不懂google这个
  - range of dates

    * lastX

segment 
自定返回哪部分数据

  - 

format
返回格式：xml, json, tsv, html, php, rss, origin

可选参数（Optional API parameters）
----------------



传递数组（Passing an array of data as a parameter）
----------------

一些参数可以用数组的形式传递. 例如，SitesManager.addSite, SitesManager.addSiteAliasUrls, SitesManager.updateSite，直接上例子：
http://demo.piwik.org/?module=API&method=SitesManager.addSite&siteName=new%20example%20website&urls[0]=http://example.org&urls[1]=http://example-alias.org


高级：一次发送多个api请求（Advanced Users: Send multiple API Requests at once）
------------------

通过token_auth进行认证（Authenticate to the API via token_auth parameter）
------------------

API Response: Metric Definitions
------------------

API Method List
------------------












