---
layout: page
title: Equipe
permalink: /equipe/
---

<!-- ================= TEAM SECTION ================= -->
<section id="equipe">
  <div class="container portfolio-flex-grid">

    <div class="row">
      <div class="col-lg-12 text-center">
        <h2>Equipe</h2>
        <hr class="star-primary">
      </div>
    </div>

    <div class="portfolio-flex-row">

      {% for post in site.members %}
        {% if post.category == "equipe" %}

        <div class="portfolio-flex-item portfolio-item" style="margin-bottom: 40px;">
          <div class="text-center">

            <!-- Portrait -->
            <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
                 class="img-responsive img-circle"
                 alt="{{ post.alt }}"
                 style="width:200px; height:200px; object-fit:cover; margin:auto;">

            <!-- Name -->
            <h4 style="margin-top:15px;">{{ post.name }}</h4>

            <!-- Role -->
            <p class="text-muted">{{ post.role }}</p>

          </div>
        </div>

        {% endif %}
      {% endfor %}

    </div>
  </div>
</section>


<!-- ================= TRAINING PLACE SECTION ================= -->
<section id="treino" style="padding:60px 0; background:#ffffff;">
  <div class="container text-center">

    <h2>Local de Treino</h2>
    <hr class="star-primary">

    <img src="{{ site.baseurl }}/img/training.jpg"
         class="img-responsive center-block"
         alt="Local de treino"
         style="max-width:700px; width:100%; margin-top:20px; border-radius:8px;">

    <p class="text-muted" style="margin-top:20px;">
      Nosso espaço de treinamento onde os atletas se desenvolvem e se preparam para os torneios.
    </p>

  </div>
</section>
