Wow version 2

{% for file in site.static_files %}
  {% if file.path contains "/blog" %}
    https://docs.askdata.com/blog{{ file.path }}
  {% endif %}
{% endfor %}
