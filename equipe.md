---
layout: page
title: 
permalink: /equipe/
---

<!-- ================= TEAM SECTION ================= -->
<section id="equipe">
  
  <
div class="portfolio-flex-row">

  {% assign membros = site.members | where: "category", "equipe" %}
  
  <!-- BASÍLIO (primeira linha sozinho) -->
  {% for post in membros %}
    {% if post.name == "Basilio" %}
      <div style="width:100%; text-align:center; margin-bottom:40px;">
        
        {{ site.baseurl }}/img/members/{{ post.img }}

        <h4 style="margin-top:15px;">{{ post.name }}</h4>
        <p class="text-muted">{{ post.role }}</p>

      </div>
    {% endif %}
  {% endfor %}

  <!-- OUTROS MEMBROS ORDENADOS -->
  {% assign outros = membros | where_exp: "item", "item.name != 'Basilio'" | sort: "name" %}

  <div class="row">
    {% for post in outros %}
      <div class="col-md-4 text-center" style="margin-bottom:40px;">
        
        {{ site.baseurl }}/img/members/{{ post.img }}

        <h4 style="margin-top:15px;">{{ post.name }}</h4>
        <p class="text-muted">{{ post.role }}</p>

      </div>

      {% if forloop.index % 3 == 0 %}
        </div><div class="row">
      {% endif %}
      
    {% endfor %}
  </div>

</div>



</section>



!-- ================= SPONSORS SECTION ================= -->
<section id="patrocinadores" style="padding:60px 0; background:#ffffff;">
  <div class="container text-center">

    <h2>Patrocinadores</h2>
    <hr class="star-primary">

    {% assign sponsors = site.sponsors | sort: "name" %}

    <div class="sponsor-slider">
      <div class="sponsor-track">

        <!-- LOOP DUPLICADO PARA EFEITO INFINITO -->
        {% for sponsor in sponsors %}
          <div class="sponsor-item">
            {{ site.baseurl }}/img/sponsors/{{ sponsor.img }}
          </div>
        {% endfor %}

        {% for sponsor in sponsors %}
          <div class="sponsor-item">
            {{ site.baseurl }}/img/sponsors/{{ sponsor.img }}
          </div>
        {% endfor %}

      </div>
    </div>

  </div>
</section>
