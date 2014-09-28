---
layout: post
category : all
tags : []
---
{% include JB/setup %}

Javascript Tracking client How-to
===================

嵌入的代码，放在head里面

<script type="text/javascript">
    var _paq = _paq || [];
    (function(){ var u=(("https:" == document.location.protocol) ? "https://{$ATHENA_URL}/nf/" : "http://{$ATHENA_URL}/nf/");
    _paq.push(['setSiteId', {$IDSITE}]);
    _paq.push(['setTrackerUrl', u+'track/']);
    _paq.push(['trackPageView']);
    _paq.push(['enableLinkTracking']);
    var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0]; g.type='text/javascript'; g.defer=true; g.async=true; g.src=u+'piwik.js';
    s.parentNode.insertBefore(g,s); })();
</script>



<!-- End Piwik Code -->

_paq
	全局数组，和t.js独立，格式：_paq.push([ 'API_method_name', parameter_list ]); _paq.push(['setCustomVariable','1','VisitorType','Member']);

Features of the JavaScript Tracker

使用通俗的名称标记用户当前访问page
_paq.push(['setDocumentTitle', document.title]);
_paq.push(['trackPageView']);

通过php渲染，定制被跟踪的page的title
_paq.push(['setDocumentTitle', "<?php echo $myPageTitle ?>"]);

手动触发一个事件

例子：
<a href="#" onclick="javascript:_paq.push(['trackEvent', 'Menu', 'Freedom']);">Freedom page</a>

Manually Trigger a Conversion for a Goal
手动触发一个转化事件
_paq.push(['trackGoal', 1]);

自定义变量
场景：同一篇文章在不同的目录出现
setCustomVariable (index, name, value, scope = "page")
index=1
1,2,3,4,5
name="category"
, one with 
value="Sports"
 and another with 
value="Europe"

