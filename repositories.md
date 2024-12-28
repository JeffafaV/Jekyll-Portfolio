---
layout: page
title: Repositories
---

<div>
{% comment %} Jekyll uses Liquid, an open-source template language {% endcomment %}
{% assign recent_projects = site.github.public_repositories | sort: 'pushed_at' | reverse %}
{% for project in recent_projects %}
    {% if forloop.index > 5 %}
        {% break %}
    {% endif %}

    <h2> {{ project.name }} </h2>
    
    <p> {{ project.description | default: "No description available." }} </p>

    {% comment %} this is if you have a custom github pages site for the repository {% endcomment %}
    {% if project.has_pages %}
    <p><a href="http://{{ project.owner.login }}.github.io/{{ project.name }}> Try it out</p>
    {% else %}
    <p><a href="{{ project.html_url }}">Try it out on GitHub</a></p>
    {% endif %}

    <p> Last updated: {{ project.pushed_at | date: "%B %d, %Y" }} </p>

    <p> Stars count: {{ project.stargazers_count }} </p>
{% endfor %}
<div>