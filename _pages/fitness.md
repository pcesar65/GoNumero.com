---
layout: test
title: Fitness
permalink: /fitness
comments: true
---

<p>
 {% for category in categories_list %}                        
                    <a href="{{site.baseurl}}/categories#{{ category[0] | url_escape | strip | replace: ' ', '-' }}">{{ category[0] | camelcase }} ({{ category[1].size }})</a>
                {% endfor %}
  </p>
