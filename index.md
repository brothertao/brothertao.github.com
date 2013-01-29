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
<script type="text/javascript" src="{{ ASSET_PATH }}/plugins/syntaxhighlighter_3.0.83/scripts/shBrushPhp.js"></script>>
<pre class="brush: php;">
function echo() {
  echo 'example';
}
</pre>

<pre class="brush: js;">
$(document).ready(function() {
    $('#new-status form').submit(function(e) {
        e.preventDefault();

        $.ajax({
            url: '/status',
            type: 'POST',
            dataType: 'json',
            data: { text: $('#new-status').find('textarea').val() },
            success: function(data) {
                $('#statuses').append('<li>' + data.text + '</li>');
                $('#new-status').find('textarea').val('');
            }
        });
    });
});
</pre>

