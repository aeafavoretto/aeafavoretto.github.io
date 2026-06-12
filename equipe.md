---
layout: page
title: 
permalink: /equipe/
---

<!-- ================= TEAM SECTION ================= -->
<section id="equipe">

  <div class="container">
    <div class="portfolio-flex-row">

      {% assign membros = site.members | where: "category", "equipe" %}

      <!-- BASÍLIO -->
      {% for post in membros %}
        {% if post.name == "Basilio" %}
          <div style="width:100%; text-align:center; margin-bottom:40px;">
            
            <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
                 onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
                 class="img-responsive img-circle"
                 style="width:200px;height:200px;object-fit:cover;margin:auto;">

            <h4 style="margin-top:15px;">{{ post.name }}</h4>
            <p class="text-muted">{{ post.role }}</p>

          </div>
        {% endif %}
      {% endfor %}

      <!-- OUTROS -->
      {% assign outros = membros | where_exp: "item", "item.name != 'Basilio'" | sort: "name" %}

      <div class="row">
        {% for post in outros %}

          <div class="col-md-4 text-center" style="margin-bottom:40px;">
            
            <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
                 onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
                 class="img-responsive img-circle"
                 style="width:200px;height:200px;object-fit:cover;margin:auto;">

            <h4 style="margin-top:15px;">{{ post.name }}</h4>
            <p class="text-muted">{{ post.role }}</p>

          </div>

          {% if forloop.index | modulo: 3 == 0 and forloop.last == false %}
            </div><div class="row">
          {% endif %}

        {% endfor %}
      </div>

    </div>
  </div>

</section>


<!-- ================= SPONSORS SECTION ================= -->
<section id="patrocinadores" style="padding:60px 0; background:#ffffff;">
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