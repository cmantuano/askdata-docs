## Blog posts

{% for file in site.static_files %}
  {% if file.path contains "blog/" %}
    <a href="/blog/{{ file.basename }}">https://docs.askdata.com/blog/{{ file.basename }}</a>
  {% endif %}
{% endfor %}
