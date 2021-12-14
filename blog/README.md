Wow

{% for file in site.static_files %}
  {% if file.path contains "/blog/" %}
    {{ file.path }}
  {% endif %}
{% endfor %}
