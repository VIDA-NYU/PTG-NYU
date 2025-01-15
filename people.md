---
title: People
permalink: /people/
---

{% assign people_sorted = site.people | sort: 'joined' %}
<!-- {% assign role_array = "pi|faculty|researchstaff||gradstudent|others|alumni" | split: "|" %} -->
{% assign role_array = "pi|faculty|researchstaff|gradstudent|former|others|alumni" | split: "|" %}


{% for role in role_array %}

{% assign people_in_role = people_sorted | where: 'position', role %}

<!-- Skip section if there's nobody -->
{% if people_in_role.size == 0 %}
  {% continue %}
{% endif %}

<div class="pos_header">
{% if role == 'faculty' %}
<h3>Faculty</h3>
 {% elsif role == 'pi' %}
<h3>Principal Investigator</h3>
 {% elsif role == 'gradstudent' %}
<h3>Graduate Students</h3>
 {% elsif role == 'researchstaff' %}
<h3>Research Associates</h3>
 {% elsif role == 'former' %}
<h3>Alumni</h3>
 {% elsif role == 'others' %}
<h3>Honorary Members</h3>
 <!-- {% elsif role == 'alumni' %}
<h3>Alumni</h3>  -->
{% endif %}
</div>

{% if role != 'alumni' %}
<div class="content list people">
  {% for profile in people_sorted %}
    {% if profile.position contains role %}
      <div class="list-item-people">
        <p class="list-post-title">
          {% if profile.avatar %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="{{site.baseurl}}/images/people/{{profile.avatar}}"></a>
          {% else %}
            <a href="{{ site.baseurl }}{{ profile.url }}"><img class="profile-thumbnail" src="http://evansheline.com/wp-content/uploads/2011/02/facebook-Storm-Trooper.jpg"></a>
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
| [Tony Liu](https://tliutony.github.io/) | Graduate Student (2018-2024) | Assistant Professor of Computer Science, Mount Holyoke College |
| [Xinyue Wang](https://www.charonwangg.com/) | Graduate Student (2021-2023) | PhD Student, Halıcıoğlu Data Science Institute, UCSD |
| Justin Brantley | Post-doc (2021-2023) | Data Scientist, Texas Rangers, yes they did win the super something twice in a row after he joined them |
Laboratory |
| [Titipat Achakulvisut](https://kordinglab.com/people/titipat_achakulvisut/.index.html) | Graduate Student (2014 - 2021) | [Biomedical and Data Lab](https://biodatlab.github.io/), Dept of Biomedical Engineering, Mahidol University, Thailand |
| [Pedro Ribeiro](https://www.linkedin.com/in/pedro-ribeiro/) | Graduate Student (2018 - 2021) | Programmer Analyst at Cedars-Sinai Department of Computational Biomedicine|
{% endif %}
{% endfor %}
