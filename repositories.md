---
layout: page
title: Repositories
---

<div>
{% comment %} Jekyll uses Liquid, an open-source template language {% endcomment %}
{% assign recent_projects = site.github.public_repositories | sort: 'pushed_at' | reverse %}
<table>
{% for project in recent_projects %}
    {% if forloop.index > 5 %}
        {% break %}
    {% endif %}
    
    <tr>
    <td class="repo-table fir-repo-col">
        <div>
            <h2> {{ project.name }} </h2>
            <p> Updated: {{ project.pushed_at | date: "%b %d, %Y" }} </p>
            <p> Stars: {{ project.stargazers_count }} </p>
            <p><a href="{{ project.html_url }}">Code</a></p>
            {% comment %} this is if you have a custom github pages site for the repository {% endcomment %}
            {% if project.has_pages %}
            <p><a href="http://{{ project.owner.login }}.github.io/{{ project.name }}">Demo</a></p>
            {% endif %}
        </div>
    </td>
    
    <td class="repo-table sec-repo-col"><p> {{ project.description | default: "No description available." }} </p></td>
    </tr>
{% endfor %}
</table>
<div>