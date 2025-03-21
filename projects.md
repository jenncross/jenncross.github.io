---
layout: default
title: Projects
---

<section class="page-header">
  <h1 class="page-title">Research & Design Projects</h1>
  <p class="page-subtitle">My work integrates participatory design methodologies with empirical investigation to create innovative systems and interfaces. Each project spans multiple methodological approaches and disciplinary boundaries.</p>
</section>

<section class="filter-controls">
  <h2 class="filter-title">Filter projects by:</h2>
  <div class="filter-options">
    <button class="filter-button active" data-filter="all">All Projects</button>
    
    <!-- Primary disciplines -->
    <button class="filter-button" data-filter="computing-and-coding">Computing & Coding</button>
    <button class="filter-button" data-filter="robotics">Robotics</button>
    <button class="filter-button" data-filter="interface-and-interaction-design">Interface & Interaction Design</button>
    <button class="filter-button" data-filter="education">Education</button>
    <button class="filter-button" data-filter="data-analysis">Data Analysis</button>
    
    <!-- Project types -->
    <button class="filter-button" data-filter="research-projects">Research Projects</button>
    <button class="filter-button" data-filter="personal">Personal Projects</button>
    <button class="filter-button" data-filter="graduate">Graduate Work</button>
    <button class="filter-button" data-filter="undergraduate">Undergraduate Work</button>
  </div>
</section>

<!-- Featured Projects Section -->
<h2 class="section-title">Featured Projects</h2>
<div class="project-grid">
  {% assign featured_projects = site.projects | where: "featured", true | sort: "weight" %}
  {% for project in featured_projects %}
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
</div>

<!-- Recent Projects Section -->
<h2 class="section-title">Recent Projects</h2>
<div class="project-grid">
  {% assign recent_projects = site.projects | where_exp: "item", "item.featured != true" | where_exp: "item", "item.weight < 100" | sort: "weight" %}
  {% for project in recent_projects %}
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
</div>

<!-- Additional Projects Section -->
<h2 class="section-title">Additional Projects</h2>

<!-- Group projects by category -->
<div class="project-categories">
  <!-- Graduate Projects -->
  {% assign graduate_projects = site.projects | where_exp: "item", "item.weight >= 100" | where: "project_category", "Graduate Project" | sort: "weight" %}
  {% if graduate_projects.size > 0 %}
  <h3 class="category-heading">Graduate Projects</h3>
  <div class="project-grid">
    {% for project in graduate_projects %}
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
  </div>
  {% endif %}
  
  <!-- Undergraduate Projects -->
  {% assign undergrad_projects = site.projects | where_exp: "item", "item.weight >= 100" | where: "project_category", "Undergraduate Project" | sort: "weight" %}
  {% if undergrad_projects.size > 0 %}
  <h3 class="category-heading">Undergraduate Projects</h3>
  <div class="project-grid">
    {% for project in undergrad_projects %}
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
  </div>
  {% endif %}
  
  <!-- Personal Projects -->
  {% assign personal_projects = site.projects | where_exp: "item", "item.weight >= 100" | where: "project_category", "Personal Project" | sort: "weight" %}
  {% if personal_projects.size > 0 %}
  <h3 class="category-heading">Personal Projects</h3>
  <div class="project-grid">
    {% for project in personal_projects %}
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
  </div>
  {% endif %}
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
