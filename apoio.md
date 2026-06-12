---
layout: page
title: 
permalink: /apoio/
---

<!-- ================= SPONSORS SECTION ================= -->
<section id="apoio">
  <div class="container text-center">

    <h2>Apoio</h2>
    <hr class="star-primary">

    {% assign sponsors = site.data.sponsors %}

    {% if sponsors and sponsors.size > 0 %}
      <div class="sponsor-slider">
        <div class="sponsor-track">

          {% for sponsor in sponsors %}
            <div class="sponsor-item">
              <img src="{{ '/img/sponsors/' | append: sponsor.img | relative_url }}"
                   class="sponsor-logo"
                   alt="{{ sponsor.name }}">
            </div>
          {% endfor %}

          {% for sponsor in sponsors %}
            <div class="sponsor-item">
              <img src="{{ '/img/sponsors/' | append: sponsor.img | relative_url }}"
                   class="sponsor-logo"
                   alt="{{ sponsor.name }}">
            </div>
          {% endfor %}

        </div>
      </div>

    {% else %}
      <p>Nenhum patrocinador cadastrado.</p>
    {% endif %}

  </div>
</section>