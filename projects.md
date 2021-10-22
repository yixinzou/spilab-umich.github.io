---
title: Projects
permalink: /projects/
---

{% assign projects_sorted = site.projects | sort: 'name' %}
{% assign status_array = "active|finished" | split: "|" %}

{% for status in status_array %}

{% assign projects_in_role = projects_sorted | where: 'status', status %}

<!-- Skip section if there's nobody -->
{% if projects_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if status == 'active' %}
<h3>Ongoing Projects</h3>
 {% elsif status == 'finished' %}
<h3>Finished Projects</h3>
{% endif %}
</div>
<hr>

<div class="content list people" style="text-align: left">
  {% for project in projects_sorted %}
    {% if project.status contains status %}
    <a class="project-title" href="{{ site.baseurl }}{{ project.url }}">{{ project.name }}</a>
      <div class="projectdiv">
        <div style="width: 30%">
          {% if project.image %}
            <a href="{{ site.baseurl }}{{ project.url }}"><img class="project-thumbnail imgppl" src="{{site.baseurl}}/images/projects/{{project.image}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ project.url }}"><img class="project-thumbnail imgppl" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
          {% endif %}
        </div>
        {% if project.blurb %}
        <div class="project-text"> {{ project.blurb }} </div>
        {% else %}
        <div class="project-text"> {{ project.excerpt }} </div>
        {% endif %}
      </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>

{% endfor %}