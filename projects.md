---
layout: default
title: Projects
---

<section class="page-header">
  <h1 class="page-title">Research Projects</h1>
  <p class="page-subtitle">My research integrates participatory design methodologies with empirical investigation to create innovative systems and interfaces. Each project typically spans multiple methodological approaches and disciplinary boundaries.</p>
</section>

<section class="filter-controls">
  <h2 class="filter-title">Filter projects by:</h2>
<div class="filter-options">
  <button class="filter-button active" data-filter="all">All Projects</button>
  
  <!-- Primary disciplines -->
  <button class="filter-button" data-filter="computing-and-coding">Computing & Coding</button>
  <button class="filter-button" data-filter="robotics">Robotics</button>
  <button class="filter-button" data-filter="interface-and-interaction-design">Interface & Interaction Design</button>
  <button class="filter-button" data-filter="electronics">Electronics</button>
  <button class="filter-button" data-filter="mechanical">Mechanical Design</button>
  <button class="filter-button" data-filter="education">Education</button>
  <button class="filter-button" data-filter="data-analysis">Data Analysis</button>
  
  <!-- Project types -->
  <button class="filter-button" data-filter="research-projects">Research Projects</button>
  <button class="filter-button" data-filter="personal">Personal Projects</button>
  <button class="filter-button" data-filter="graduate">Graduate Work</button>
  <button class="filter-button" data-filter="undergraduate">Undergraduate Work</button>
</div>
</section>

<div class="project-grid">
  {% for project in site.projects %}
  {% assign discipline_classes = "" %}
  {% for discipline in project.disciplines %}
    {% assign discipline_class = discipline | downcase | replace: " ", "-" | replace: "&", "and" %}
    {% assign discipline_classes = discipline_classes | append: discipline_class | append: " " %}
  {% endfor %}
  
  {% assign type_classes = "" %}
  {% for type in project.project_type %}
    {% assign type_class = type | downcase | replace: " ", "-" | replace: "&", "and" %}
    {% assign type_classes = type_classes | append: type_class | append: " " %}
  {% endfor %}
  
<div class="project-card" data-category="{% for discipline in project.disciplines %}{{ discipline | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %} {% for type in project.project_type %}{{ type | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %}">
  {% if project.featured_image %}
  <div class="project-image-container">
    <img src="{{ project.featured_image }}" alt="{{ project.title }}" class="project-image">
  </div>
  {% endif %}
  <div class="project-content">
    <h3 class="project-title">{{ project.title }}</h3>
    <p class="project-description">{{ project.excerpt }}</p>
    <div class="tag-container">
      {% for discipline in project.disciplines limit:3 %}
      <span class="tag">{{ discipline }}</span>
      {% endfor %}
    </div>
    <a href="{{ project.url }}" class="project-link">Details</a>
  </div>
</div>
 {% endfor %}

<script>
  document.addEventListener('DOMContentLoaded', function() {
    const filterButtons = document.querySelectorAll('.filter-button');
    const projectCards = document.querySelectorAll('.project-card');
    
    filterButtons.forEach(button => {
      button.addEventListener('click', function() {
        // Remove active class from all buttons
        filterButtons.forEach(btn => btn.classList.remove('active'));
        
        // Add active class to clicked button
        this.classList.add('active');
        
        // Get filter value
        const filterValue = this.getAttribute('data-filter');
        
        // Filter projects
        projectCards.forEach(card => {
          if (filterValue === 'all' || card.getAttribute('data-category').includes(filterValue)) {
            card.style.display = 'block';
          } else {
            card.style.display = 'none';
          }
        });
      });
    });
  });
</script>
