---
layout: default
title: Teaching
---

<section class="page-header">
 <h1 class="page-title">Teaching</h1>

<p class="page-subtitle"> My teaching approach draws on constructivist principles and focuses on creating meaningful learning experiences that bridge theoretical concepts with real-world applications. I design learning environments that foster student creativity and critical thinking in engineering and computer science.</p>

My courses emphasize hands-on, project-based learning that allows students to develop both technical skills and the ability to apply these skills to solve real-world problems. I believe in creating inclusive learning environments that support diverse learners and promote collaboration.

</section> 
## Current Courses

{% for course in site.courses %}
{% if course.current %}

<div class="course-card">
  <div class="course-card-header">
    <span class="course-level">{{ course.level }}</span>
    <h3 class="course-title"><a href="{{ course.url }}">{{ course.title }}</a></h3>
  </div>
  <div class="course-card-body">
    <p class="course-meta">{{ course.students }} • {{ course.years }}</p>
    <p class="course-desc">{{ course.excerpt | strip_html | truncatewords: 30 }}</p>
    <div class="course-tags">
      {% for tag in course.tags %}
      <span class="course-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    <a href="{{ course.url }}" class="course-link">View course details</a>
  </div>
</div>
{% endif %}
{% endfor %}

## Previous Courses

{% for course in site.courses %}
{% if course.current != true %}

<div class="course-card">
  <div class="course-card-header">
    <span class="course-level">{{ course.level }}</span>
    <h3 class="course-title"><a href="{{ course.url }}">{{ course.title }}</a></h3>
  </div>
  <div class="course-card-body">
    <p class="course-meta">{{ course.students }} • {{ course.years }}</p>
    <p class="course-desc">{{ course.excerpt | strip_html | truncatewords: 30 }}</p>
    <div class="course-tags">
      {% for tag in course.tags %}
      <span class="course-tag">{{ tag }}</span>
      {% endfor %}
    </div>
    <a href="{{ course.url }}" class="course-link">View course details</a>
  </div>
</div>
{% endif %}
{% endfor %}

## Teaching Philosophy

I believe in creating learning experiences that:

1. **Connect theory to practice** through authentic projects that solve real problems
2. **Support diverse learners** by providing multiple pathways to engagement and understanding
3. **Foster creativity** by encouraging students to explore and take risks in a supportive environment
4. **Develop computational thinking** as a transferable skill applicable across disciplines
5. **Build community** through collaborative learning and peer support

My goal is to help students develop not just technical skills, but also the confidence and creativity to apply these skills in innovative ways across disciplines.
