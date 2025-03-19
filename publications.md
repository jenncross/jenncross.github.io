---
layout: default
title: Publications
---

<style>
.page-title h1{
  margin-bottom: 0; }

.publications-container {
  margin-top: 0;
}

.publication-category {
  margin-bottom: 2.5rem;
}

.publication-list {
  list-style-type: none;
  padding-left: 0;
}

.publication-list li {
  margin-bottom: 1.5rem;
  display: grid;
  grid-template-columns: 3.5rem 1fr;
  grid-gap: 1rem;
  align-items: start;
}

.publication-id {
  font-weight: bold;
  color: #333;
  grid-column: 1;
  justify-self: start;
}

.publication-content {
  grid-column: 2;
}

.publication-cite {
  font-size: 0.95rem;
  line-height: 1.4;
  margin-bottom: 0.25rem;
}

.publication-award {
  color: #d14;
  font-weight: 500;
  display: inline-block;
  margin-top: 0.25rem;
}

.publication-links {
  margin-top: 0.25rem;
  font-size: 0.85rem;
  display: block;
  width: 100%;
}

.publication-link {
  display: inline;
  white-space: nowrap;
}

.separator {
  display: inline;
  color: #777;
  white-space: nowrap;
}
</style>

<div class="publications-container">
<h1 class="page-title"> Publications </h1>
  <!-- Journal Publications -->
  <div class="publication-category">
    <h2>Journal Publications</h2>
    <ol class="publication-list">
      {% assign journal_pubs = site.data.publications | where: "type", "journal" | sort: "year" | reverse %}
      {% assign journal_count = journal_pubs.size %}
      
      {% for pub in journal_pubs %}
        <li>
          <span class="publication-id">[J{{ journal_count | minus: forloop.index0 }}]</span>
          <div class="publication-content">
            <p class="publication-cite">
              {% assign author_list = "" %}
              {% for author in pub.authors %}
                {% if author.highlight %}
                  {% assign author_name = "<strong>" | append: author.name | append: "</strong>" %}
                {% else %}
                  {% assign author_name = author.name %}
                {% endif %}
                
                {% if forloop.last %}
                  {% assign author_list = author_list | append: " and " | append: author_name %}
                {% elsif forloop.first %}
                  {% assign author_list = author_name %}
                {% else %}
                  {% assign author_list = author_list | append: ", " | append: author_name %}
                {% endif %}
              {% endfor %}
              
              {{ author_list }}. {{ pub.year }}. {{ pub.title }}. <em>{{ pub.venue }}</em>{% if pub.volume and pub.volume != "" %} {{ pub.volume }}{% if pub.issue and pub.issue != "" %}({{ pub.issue }}){% endif %}{% endif %}{% if pub.pages and pub.pages != "" %}, {{ pub.pages }}{% endif %}. {% if pub.publisher and pub.publisher != "" %}{{ pub.publisher }}.{% endif %}
              
              {% if pub.award %}
              <span class="publication-award">{{ pub.award }}</span>
              {% endif %}
            </p>
            
            {% if pub.links.size > 0 %}
            <div class="publication-links">
              {% for link in pub.links %}
              {% if forloop.first == false %}
              <span class="separator">&nbsp;&nbsp;|&nbsp;&nbsp;</span>
              {% endif %}
              <a href="{{ link.url }}" class="publication-link" target="_blank">{{ link.text }}</a>
              {% endfor %}
            </div>
            {% endif %}
          </div>
        </li>
      {% endfor %}
    </ol>
  </div>
  
  <!-- Conference Publications -->
  <div class="publication-category">
    <h2>Conference Publications</h2>
    <ol class="publication-list">
      {% assign conf_pubs = site.data.publications | where: "type", "conference" | sort: "year" | reverse %}
      {% assign conf_count = conf_pubs.size %}
      
      {% for pub in conf_pubs %}
        <li>
          <span class="publication-id">[C{{ conf_count | minus: forloop.index0 }}]</span>
          <div class="publication-content">
            <p class="publication-cite">
              {% assign author_list = "" %}
              {% for author in pub.authors %}
                {% if author.highlight %}
                  {% assign author_name = "<strong>" | append: author.name | append: "</strong>" %}
                {% else %}
                  {% assign author_name = author.name %}
                {% endif %}
                
                {% if forloop.last %}
                  {% assign author_list = author_list | append: " and " | append: author_name %}
                {% elsif forloop.first %}
                  {% assign author_list = author_name %}
                {% else %}
                  {% assign author_list = author_list | append: ", " | append: author_name %}
                {% endif %}
              {% endfor %}
              
              {{ author_list }}. {{ pub.year }}. {{ pub.title }}. {% if pub.venue contains "Proceedings" %}{{ pub.venue }}{% else %}In <em>{{ pub.venue }}</em>{% endif %}{% if pub.pages and pub.pages != "" %}, {{ pub.pages }}{% endif %}{% if pub.location and pub.location != "" %}, {{ pub.location }}{% endif %}. {% if pub.publisher and pub.publisher != "" %}{{ pub.publisher }}.{% endif %}
              
              {% if pub.award %}
              <span class="publication-award">{{ pub.award }}</span>
              {% endif %}
            </p>
            
            {% if pub.links.size > 0 %}
            <div class="publication-links">
              {% for link in pub.links %}
              {% if forloop.first == false %}
              <span class="separator">&nbsp;&nbsp;|&nbsp;&nbsp;</span>
              {% endif %}
              <a href="{{ link.url }}" class="publication-link" target="_blank">{{ link.text }}</a>
              {% endfor %}
            </div>
            {% endif %}
          </div>
        </li>
      {% endfor %}
    </ol>
  </div>
  
  <!-- Dissertation -->
  <div class="publication-category">
    <h2>Dissertation</h2>
    <ol class="publication-list">
      {% assign thesis_pubs = site.data.publications | where: "type", "thesis" | sort: "year" | reverse %}
      
      {% for pub in thesis_pubs %}
        <li>
          <span class="publication-id">[T1]</span>
          <div class="publication-content">
            <p class="publication-cite">
              <strong>{{ pub.authors[0].name }}</strong>. {{ pub.year }}. <em>{{ pub.title }}</em>. {{ pub.venue }}. {% if pub.publisher and pub.publisher != "" %}{{ pub.publisher }}.{% endif %}
              
              {% if pub.award %}
              <span class="publication-award">{{ pub.award }}</span>
              {% endif %}
            </p>
            
            {% if pub.links.size > 0 %}
            <div class="publication-links">
              {% for link in pub.links %}
              {% if forloop.first == false %}
              <span class="separator">&nbsp;&nbsp;|&nbsp;&nbsp;</span>
              {% endif %}
              <a href="{{ link.url }}" class="publication-link" target="_blank">{{ link.text }}</a>
              {% endfor %}
            </div>
            {% endif %}
          </div>
        </li>
      {% endfor %}
    </ol>
  </div>
</div>
