---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'name' %}
{% assign role_array = "pi|postdoc|phdstudent|masterstudent|undergradstudent|researchstaff|visiting|others|alumni" | split: "|" %}

{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'postdoc' %}
<h3>Postdoctoral Fellows</h3>
 {% elsif role == 'pi' %}
<h3>Faculty</h3>
 {% elsif role == 'phdstudent' %}
<h3>PhD Students</h3>
 {% elsif role == 'masterstudent' %}
<h3>Masters Students</h3>
 {% elsif role == 'undergradstudent' %}
<h3>Undergraduate Students</h3>
 {% elsif role == 'researchstaff' %}
<h3>Research Staff</h3>
 {% elsif role == 'visiting' %}
<h3>Visiting Scholars</h3>
 {% elsif role == 'others' %}
<h3>Honorary Members</h3>
 {% elsif role == 'alumni' %}
<h3>Alumni</h3>
{% endif %}
</div>

{% if role != 'alumni' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail imgppl" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail imgppl" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
          {% endif %}
          <a class="name" href="{{ site.baseurl }}{{ profile.url }}">{{ profile.name }}</a>
        </p>
      </div>    
    {% endif %}
  {% endfor %}
</div>
<hr>

{% else %}

<br>

| Who are they | When were they here | Where they went |
| :------------- |:-------------| :-----------|
| [Steve Antos](http://kordinglab.com/people/steve_antos/index.html) | Graduate Student (2012 - 2019) | - |
| [Max Berniker](http://sensorimotorcontrolatorium.uic.edu/)   | Postdoc (2014) | Asst Prof, Univ of Illinois at Chicago, Mechanical &amp; Industrial Eng |
| [Mathieu d'Acremont](https://scholar.google.com/citations?user=D7ys4VQAAAAJ&hl=en) | Postdoc (2014) | - |
| [Iris Vilares](https://scholar.google.com/citations?user=Ztwn608AAAAJ&hl=en)   | Graduate Student (2009-2013) | Postdoc, University of Virginia and University College London (w. Peter Dayan) |

{% endif %}
{% endfor %}
