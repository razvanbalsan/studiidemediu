---
layout: page
title: Proiecte
permalink: /proiecte/
subtitle: Portofoliul nostru de proiecte
description: "Portofoliu de peste 1000 proiecte de mediu: energie regenerabilă, infrastructură, industrie, dezvoltare urbană, arii protejate, cercetare biodiversitate."
keywords: "proiecte energie regenerabilă, studii impact eoliene, fotovoltaice, proiecte infrastructură, arii protejate Natura 2000, cercetare biodiversitate"
---

<div class="proiecte-intro">
  <p>Explorați proiectele noastre curente și descoperiți portofoliul nostru vast de realizări în domeniul consultanței de mediu, dezvoltare durabilă și protecție a biodiversității.</p>
</div>

## Proiecte curente

{% assign proiecte_curente = site.proiecte | where_exp: "item", "item.status == 'in-desfasurare' or item.status == 'in-pregatire' or item.status == 'consultare-publica'" | sort: 'status' %}

{% if proiecte_curente.size > 0 %}
<div class="proiecte-grid">
  {% for proiect in proiecte_curente %}
  <div class="proiect-card">
    <div class="proiect-card-header">
      {% if proiect.category %}
        <span class="proiect-category">{{ proiect.category | replace: '-', ' ' | capitalize }}</span>
      {% endif %}
      {% if proiect.status %}
        <span class="proiect-status status-{{ proiect.status }}">{{ proiect.status | replace: '-', ' ' | capitalize }}</span>
      {% endif %}
    </div>
    <h3><a href="{{ proiect.url }}">{{ proiect.title }}</a></h3>
    <p>{{ proiect.excerpt }}</p>
    {% if proiect.location %}
    <p class="proiect-location">
      <svg class="icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
        <circle cx="12" cy="10" r="3"></circle>
      </svg>
      {{ proiect.location }}
    </p>
    {% endif %}
    <a href="{{ proiect.url }}" class="btn-link">Detalii →</a>
  </div>
  {% endfor %}
</div>
{% else %}
<p class="no-proiecte">Nu există proiecte curente în derulare. Verificați secțiunea portofoliu pentru proiectele noastre finalizate.</p>
{% endif %}

---

<div class="portfolio-section" markdown="1">

## Portofoliu reprezentativ

<p class="portfolio-intro">De-a lungul anilor, am colaborat cu numeroși clienți din sectorul public și privat pentru realizarea de studii de mediu și documentații tehnice. Cu un portofoliu de <strong>peste 1000 de proiecte reglementate pe linie de mediu</strong>, ne mândrim cu realizări în diverse domenii.</p>

{% assign proiecte_portfolio = site.proiecte | where_exp: "item", "item.status == nil or item.status == ''" | sort: 'category' %}

{% if proiecte_portfolio.size > 0 %}
<div class="portfolio-grid">
  {% for proiect in proiecte_portfolio %}
  <div class="portfolio-card{% if proiect.highlight %} portfolio-card-highlight{% endif %}">
    <div class="portfolio-card-icon">
      {% if proiect.icon == 'users' %}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
        <circle cx="9" cy="7" r="4"></circle>
        <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
        <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
      </svg>
      {% elsif proiect.icon == 'cloud' %}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M18 10h-1.26A8 8 0 1 0 9 20h9a5 5 0 0 0 0-10z"></path>
      </svg>
      {% elsif proiect.icon == 'home' %}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z"></path>
        <polyline points="9 22 9 12 15 12 15 22"></polyline>
      </svg>
      {% elsif proiect.icon == 'hexagon' %}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M21 16V8a2 2 0 0 0-1-1.73l-7-4a2 2 0 0 0-2 0l-7 4A2 2 0 0 0 3 8v8a2 2 0 0 0 1 1.73l7 4a2 2 0 0 0 2 0l7-4A2 2 0 0 0 21 16z"></path>
        <polyline points="3.27 6.96 12 12.01 20.73 6.96"></polyline>
        <line x1="12" y1="22.08" x2="12" y2="12"></line>
      </svg>
      {% elsif proiect.icon == 'building' %}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <rect x="2" y="7" width="20" height="14" rx="2" ry="2"></rect>
        <path d="M16 21V5a2 2 0 0 0-2-2h-4a2 2 0 0 0-2 2v16"></path>
      </svg>
      {% elsif proiect.icon == 'star' %}
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M12 2l3.09 6.26L22 9.27l-5 4.87 1.18 6.88L12 17.77l-6.18 3.25L7 14.14 2 9.27l6.91-1.01L12 2z"></path>
      </svg>
      {% endif %}
    </div>
    <h3><a href="{{ proiect.url }}">{{ proiect.title }}</a></h3>
    <p>{{ proiect.excerpt }}</p>
    <a href="{{ proiect.url }}" class="btn-link">Detalii →</a>
  </div>
  {% endfor %}
</div>
{% endif %}

---

## Consultări publice

Pentru fiecare proiect major, organizăm consultări publice conform legislației în vigoare. Verificați secțiunea [Anunțuri](/anunturi/) pentru detalii despre consultările în desfășurare.

Pentru întrebări sau solicitări de informații despre proiectele noastre, [contactați-ne](/contact/).

</div>
