
{% for item in site.data.classes %}
- **{{ item.title }}**<br>{{ item.university }}, {{ item.mooc }}<br>{{ item.from }}-{{ item.to }}<br>{% if item.description %}{{ item.description }}<br>{% endif %}{% if item.grade %}Grade: {{ item.grade }}{% endif %}{% if item.certificate_url %}[Certificate]({{ item.certificate_url }}){% endif %}

{% endfor %}
