---
layout: default
title: Anunțuri
permalink: /anunturi/
---

<section class="anunturi-page">
  <header class="page-header">
    <div class="container">
      <h1 class="page-title">Anunțuri</h1>
      <p class="page-subtitle">Anunțuri de interes public și consultări</p>
    </div>
  </header>

  <div class="anunturi-content">
    <div class="container">
      <p class="anunturi-intro">
        Pe această pagină găsiți anunțurile de interes public privind proiectele pentru care se desfășoară proceduri de evaluare a impactului asupra mediului și consultări publice. Verificați periodic această secțiune pentru informații despre dezbaterile publice și termenele de depunere a observațiilor.
      </p>

      <div class="anunturi-list">
        {% assign sorted_anunturi = site.anunturi | sort: 'date' | reverse %}
        {% for anunt in sorted_anunturi %}
        <article class="anunt-card">
          <div class="anunt-card-header">
            <span class="anunt-card-date">
              <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                <line x1="16" y1="2" x2="16" y2="6"></line>
                <line x1="8" y1="2" x2="8" y2="6"></line>
                <line x1="3" y1="10" x2="21" y2="10"></line>
              </svg>
              {{ anunt.date | date: "%d.%m.%Y" }}
            </span>
            {% if anunt.category %}
            <span class="anunt-card-category">{{ anunt.category }}</span>
            {% endif %}
          </div>

          <h2 class="anunt-card-title">
            <a href="{{ anunt.url | relative_url }}">{{ anunt.title }}</a>
          </h2>

          {% if anunt.company %}
          <p class="anunt-card-company">{{ anunt.company }}</p>
          {% endif %}

          {% if anunt.excerpt %}
          <p class="anunt-card-excerpt">{{ anunt.excerpt }}</p>
          {% endif %}

          <div class="anunt-card-meta">
            {% if anunt.location %}
            <span class="meta-item">
              <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
                <circle cx="12" cy="10" r="3"></circle>
              </svg>
              {{ anunt.location }}
            </span>
            {% endif %}

            {% if anunt.public_debate %}
            <span class="meta-item meta-highlight">
              <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                <circle cx="12" cy="12" r="10"></circle>
                <polyline points="12 6 12 12 16 14"></polyline>
              </svg>
              Dezbatere: {{ anunt.public_debate.date }}
            </span>
            {% endif %}
          </div>

          <a href="{{ anunt.url | relative_url }}" class="anunt-card-link">
            Vezi detalii complete
            <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </a>
        </article>
        {% endfor %}

        {% if site.anunturi.size == 0 %}
        <p class="no-anunturi">Nu există anunțuri publicate în acest moment. Reveniți pentru actualizări.</p>
        {% endif %}
      </div>
    </div>
  </div>
</section>
