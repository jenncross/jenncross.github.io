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
    <button class="filter-button" data-filter="participatory">Participatory Design</button>
    <button class="filter-button" data-filter="research">Design-Based Research</button>
    <button class="filter-button" data-filter="interdisciplinary">Interdisciplinary</button>
    <button class="filter-button" data-filter="k12">K-12 Education</button>
    <button class="filter-button" data-filter="higher">Higher Education</button>
    <button class="filter-button" data-filter="current">Current Projects</button>
    <button class="filter-button" data-filter="completed">Completed Projects</button>
  </div>
</section>

<div class="project-grid">
  {% for project in site.projects %}
  {% assign approach_classes = "" %}
  {% for approach in project.approaches %}
    {% assign approach_class = approach | downcase | replace: " ", "-" | replace: "-&-", "-" | replace: "-based", "" %}
    {% assign approach_classes = approach_classes | append: approach_class | append: " " %}
  {% endfor %}
  
  {% assign context_classes = "" %}
  {% for context in project.contexts %}
    {% assign context_class = context | downcase | replace: " ", "-" | replace: "-&-", "-" %}
    {% assign context_classes = context_classes | append: context_class | append: " " %}
  {% endfor %}
  
  <div class="project-card" data-category="{{ approach_classes }} {{ context_classes }} {{ project.status | downcase }}">
    {% if project.featured_image %}
    <img src="{{ project.featured_image }}" alt="{{ project.title }}" class="project-image">
    {% endif %}
    <div class="project-content">
      <h3 class="project-title">{{ project.title }}</h3>
      <p class="project-meta">{{ project.timeframe }}{% if project.grant %} | {{ project.grant }}{% endif %}</p>
      <p class="project-description">{{ project.excerpt }}</p>
      <div class="tag-container">
        {% for approach in project.approaches %}
        {% assign approach_class = approach | downcase | replace: " ", "-" | replace: "-&-", "-" | replace: "-based", "" %}
        <span class="tag"><span class="tag-indicator {{ approach_class }}"></span>{{ approach }}</span>
        {% endfor %}
      </div>
      <a href="{{ project.url }}" class="project-link">Project details</a>
    </div>
  </div>
  {% endfor %}
</div>

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
