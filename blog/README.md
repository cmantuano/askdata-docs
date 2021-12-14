Wow version 3

{% for file in site.static_files %}
  {% if file.path contains "blog/" %}
    https://docs.askdata.com/blog/{{ file.basename }}
  {% endif %}
{% endfor %}
