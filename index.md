---
layout: page
title: ^_^!
tagline: 
---
{% include JB/setup %}

blog list
_______

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

blog list
---------
<script type="text/javascript" src="{{ ASSET_PATH }}/twitter/plugins/syntaxhighlighter_3.0.83/scripts/shBrushPhp.js"></script>>
<div style="background-color:black;">
<pre class="brush: php;">
function echo() {
  echo 'example';
}
</pre>
</div>

