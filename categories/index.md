---
layout: page
permalink: /categories/
title: Categories
---


<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugize }}"></div>
    <p></p>
    
    <h3 class="category-head">{{ category_name }}</h3>
    <a name="{{ category_name | slugize }}"></a>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <h4><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></h4>
    </article>
    {% endfor %}
  </div>
{% endfor %}
</div>




<div class="archives" itemscope itemtype="http://schema.org/Blog">
    {% for category in site.categories %}
        {% capture category_name %}{{ category | first }}{% endcapture %}
        <h2 class="category">{{ category_name }}</h2>
        <ul>
            {% for post in site.categories[category_name] %}
                {% if post.layout == 'post' %}
                    <li>
                        <h3 class="title"><a href="{{ post.url }}">{{post.title}}</a></h3>
                        <div class="meta">
                            <span class="date"><time datetime="{{ date | datetime | date_to_xmlschema }}" itemprop="datePublished">{{ date | date: "%b %e" }}</time></span>
                            {% if site.disqus_short_name and post.comments == true and site.disqus_show_comment_count == true %}
                                {% include post/comments_link.html %}
                            {% endif %}
                            <span class="edit">{% include post/edit.html %}</span>
                        </div>
                    </li>
                {% endif %}
            {% endfor %}
        </ul>
    {% endfor %}
</div>
