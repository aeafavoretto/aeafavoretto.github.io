---
layout: page
title: 
permalink: /patrocinadores/
---

<!-- ================= SPONSORS SECTION ================= -->
<section id="patrocinadores">
<!-- <section id="patrocinadores" style="padding:60px 0; background:#ffffff;"> -->
  <div class="container text-center">

    <h2>Patrocinadores</h2>
    <hr class="star-primary">

    {% if site.sponsors %}
      {% assign sponsors = site.sponsors | sort: "name" %}
    {% else %}
      {% assign sponsors = "" %}
    {% endif %}

    <div class="sponsor-slider">
      <div class="sponsor-track">

        {% for sponsor in sponsors %}
          <div class="sponsor-item">
            <img src="{{ site.baseurl }}/img/sponsors/{{ sponsor.img }}"
                 class="sponsor-logo">
          </div>
        {% endfor %}

        {% for sponsor in sponsors %}
          <div class="sponsor-item">
            <img src="{{ site.baseurl }}/img/sponsors/{{ sponsor.img }}"
                 class="sponsor-logo">
          </div>
        {% endfor %}

      </div>
    </div>

  </div>
</section>