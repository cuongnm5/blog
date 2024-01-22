
{% for tag in site.tags %}

  <h4 id="{{ tag[0] }}">{{ tag[0] }}</h4>
  <ul>
    {% for post in site.posts %}
      {% if post.tags contains tag[0] and post.lang == 'vi' %}
        <div class="article__wrapper">

            {% if post.image %}
              <a href="{{post.url | prepend: site.baseurl_root}}" class="article__image" style="background-image: url({{site.baseurl_root}}/images/{{post.image}})">
              </a>
            {% else %}
              {% assign without-image = 'article-without-image' %}
            {% endif %}

            <div class="article__content {{ without-image }}">
              <div class="article-tags">
              {% if post.tags.size >= 1 %}
              {% else %}
              {% endif %}
              </div>

              <h2 class="article__title">
                <a href="{{ post.url | prepend: site.baseurl }}">{{post.title}}</a>
              </h2>

              <p class="article__excerpt">{% if post.description %}{{ post.description }}{% else %}{{ post.content | strip_html | truncate: 185 }}{% endif %}</p>

              <div class="article__footer">
                <div class="article__meta">
                  <b><span class="article__date"><time datetime="{{ post.date | date_to_xmlschema }}">{% assign date_format = site.minima.date_format | default: "%B %-d, %Y" %}{{ post.date | date: date_format }}</time></span></b>
                </div>
              </div>

            </div>

          </div>




      {% endif %}
    {% endfor %}

  </ul>
{% endfor %}
