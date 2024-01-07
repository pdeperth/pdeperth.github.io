---
layout: page
permalink: /reviewing/
title: Reviewing
description:
nav: true
nav_order: 6
---


<div class="news">
    {% if site.reviewing != blank -%}
    {%- assign reviewing_size = site.reviewing | size -%}
    <div class="table-responsive" {% if include.limit and site.announcements.scrollable and reviewing_size> 3
        %}style="max-height: 80vw"{% endif %}>
        <table class="table table-sm table-borderless">
            {%- assign reviewing = site.reviewing | reverse -%}
            <!-- {% if include.limit and site.announcements.limit %}
            {% assign reviewing_limit = site.announcements.limit %}
            {% else %} -->
            {% assign reviewing_limit = reviewing_size %}
            <!-- {% endif %} -->
            {% for item in reviewing limit: reviewing_limit %}
            <tr>
                <th scope="row" style="width: 20%">{{ item.year | date: "%Y" }}</th>
                <td>
                    {% if item.inline -%}
                    {{ item.content | remove: '<p>' | remove: '</p>' | emojify }}
                    {%- else -%}
                    <a class="news-title" href="{{ item.url | relative_url }}">{{ item.title }}</a>
                    {%- endif %}
                </td>
            </tr>
            {%- endfor %}
        </table>
    </div>
    {%- else -%}
    <p>No new reviewing.</p>
    {%- endif %}
</div>