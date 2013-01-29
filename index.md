---
layout: page
title: Hello World!
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
{% highlight php %}
function echo() {
  echo 'example';
}
{% endhighlight %}

```javascript
function() {
	console.log(this);
}
```

