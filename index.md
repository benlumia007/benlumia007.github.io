---
layout: default
title: Blog
---
<header class="entry-header">
    <ul>
        {% for post in site.posts %}
            <li>
                <h1 class="entry-title"><a href="{{ post.url }}">{{ post.title }}</a></h1>
                <span class="entry-metadata">
                {%- assign date_format = site.minima.date_format | default: "%B %-d, %Y" -%}
                <time class="dt-published" datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">
                    {{ post.date | date: date_format }}
                </time>
                {%- if post.modified_date -%}
                    ~ 
                    {%- assign mdate = post.modified_date | date_to_xmlschema -%}
                    <time class="dt-modified" datetime="{{ mdate }}" itemprop="dateModified">
                    {{ mdate | date: date_format }}
                    </time>
                {%- endif -%}
                {%- if post.author -%}
                    • {% for author in post.author %}
                    <span itemprop="author" itemscope itemtype="http://schema.org/Person">
                        <span class="p-author h-card" itemprop="name">{{ author }}</span></span>
                        {%- if forloop.last == false %}, {% endif -%}
                    {% endfor %}
                {%- endif -%}</span>
                {{ post.excerpt }}
            </li>
        {% endfor %}
    </ul>
</header>