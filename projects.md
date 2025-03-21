---
layout: default
title: Projects
---

<section class="page-header">
  <h1 class="page-title">Research & Design Projects</h1>
  <p class="page-subtitle">My work creating robotics systems, software, innovative interactions and intuitive interfaces builds on participatory design methodologies and empirical investigations.</p>
</section>

<section class="filter-controls">
  <h2 class="filter-title">Filter projects by:</h2>
  <div class="filter-options">
    <button class="filter-button active" data-filter="all">All Projects</button>
    
    <!-- Primary disciplines -->
    <button class="filter-button" data-filter="computing-and-coding">Computing & Coding</button>
    <button class="filter-button" data-filter="robotics">Robotics</button>
    <button class="filter-button" data-filter="robotics">Prototyping</button>
    <button class="filter-button" data-filter="interface-and-interaction-design">Interfaces & Interactions</button>
    <button class="filter-button" data-filter="education">Education</button>
    <button class="filter-button" data-filter="data-analysis">Data</button>

  </div>
</section>

<!-- Featured Projects Section -->
<h2 class="section-title">Featured Projects</h2>
<div class="project-grid">
  {% assign featured_projects = site.projects | where: "featured", true | sort: "weight" %}
  {% for project in featured_projects %}
  <a href="{{ project.url }}" class="project-card-link">
    <div class="project-card" data-category="{% for discipline in project.disciplines %}{{ discipline | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %} {% for type in project.project_type %}{{ type | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %}">
      {% if project.featured_image %}
      <div class="project-image-container">
        <img src="{{ project.featured_image }}" alt="{{ project.title }}" class="project-image">
        {% if project.project_category == "Graduate Project" or project.project_category == "Undergraduate Project" %}
        <span class="card-category-badge">{{ project.project_category }}</span>
        {% endif %}
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
        <span class="project-link">Details</span>
      </div>
    </div>
  </a>
  {% endfor %}
</div>

<!-- Recent Projects Section -->
<h2 class="section-title">Recent Projects</h2>
<div class="project-grid">
  {% assign recent_projects = site.projects | where_exp: "item", "item.featured != true" | where_exp: "item", "item.weight < 100" | sort: "weight" %}
  {% for project in recent_projects %}
  <a href="{{ project.url }}" class="project-card-link">
    <div class="project-card" data-category="{% for discipline in project.disciplines %}{{ discipline | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %} {% for type in project.project_type %}{{ type | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %}">
      {% if project.featured_image %}
      <div class="project-image-container">
        <img src="{{ project.featured_image }}" alt="{{ project.title }}" class="project-image">
        {% if project.project_category == "Graduate Project" or project.project_category == "Undergraduate Project" %}
        <span class="card-category-badge">{{ project.project_category }}</span>
        {% endif %}
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
        <span class="project-link">Details</span>
      </div>
    </div>
  </a>
  {% endfor %}
</div>

<!-- Additional Projects Section -->
<h2 class="section-title">Additional Projects</h2>
<div class="project-grid">
  {% assign additional_projects = site.projects | where_exp: "item", "item.featured != true" | where_exp: "item", "item.weight >= 100" | sort: "weight" %}
  {% for project in additional_projects %}
  <a href="{{ project.url }}" class="project-card-link">
    <div class="project-card" data-category="{% for discipline in project.disciplines %}{{ discipline | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %} {% for type in project.project_type %}{{ type | downcase | replace: ' ', '-' | replace: '&', 'and' }} {% endfor %}">
      {% if project.featured_image %}
      <div class="project-image-container">
        <img src="{{ project.featured_image }}" alt="{{ project.title }}" class="project-image">
        {% if project.project_category == "Graduate Project" or project.project_category == "Undergraduate Project" %}
        <span class="card-category-badge">{{ project.project_category }}</span>
        {% endif %}
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
        <span class="project-link">Details</span>
      </div>
    </div>
  </a>
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
            card.closest('.project-card-link').style.display = 'block';
          } else {
            card.closest('.project-card-link').style.display = 'none';
          }
        });
      });
    });
  });
</script>
