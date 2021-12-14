Wow

{% for page in site.pages %}
{% if page.path.match('blog') %}
<li><a href="{{ page.url }}">{{ page.title }}</a></li>
{% endif %}
{% endfor %}
