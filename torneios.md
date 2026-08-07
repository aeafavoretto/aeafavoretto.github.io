---
layout: page
title: 
permalink: /torneios/
---

<section id="torneios" class="py-5">
  <div class="container">

    <div class="text-center mb-5">
      <h2>Torneios</h2>
      <hr class="star-primary">
      <p class="text-muted">
        Confira os torneios realizados e acompanhe os próximos eventos.
      </p>
    </div>

    <div class="torneios-lista">

      <div class="torneio-card">
        <span class="torneio-data">Junho de 2026</span>

        <h4>
          <a href="{{ site.baseurl }}/torneios/torneio-jun-2026/>2ª Etapa do 4º Circuito AEA de Vôlei de Praia
          </a>
        </h4>

        <a href="">📸 Fotos
        </a>
      </div>

    </div>

  </div>
</section>

<style>
.torneios-lista {
  max-height: 600px;
  overflow-y: auto;
  padding-right: 10px;
}

.torneio-card {
  background: #fff;
  border-left: 5px solid #ff5c00;
  padding: 20px;
  margin-bottom: 15px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  transition: all 0.3s ease;
}

.torneio-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 15px rgba(0,0,0,0.12);
}

.torneio-data {
  display: inline-block;
  background: #ffe7d8;
  color: #ff5c00;
  font-size: 0.85rem;
  font-weight: 600;
  padding: 5px 10px;
  border-radius: 20px;
  margin-bottom: 12px;
}

.torneio-card h4 {
  margin: 0 0 10px 0;
}

.torneio-card h4 a {
  color: #222;
  text-decoration: none;
}

.torneio-card h4 a:hover {
  color: #ff5c00;
}

.fotos-link {
  display: inline-block;
  margin-top: 5px;
  padding: 7px 14px;
  background: #ff5c00;
  color: #fff !important;
  border-radius: 20px;
  text-decoration: none;
  font-size: 0.85rem;
  font-weight: 600;
  transition: background 0.3s ease;
}

.fotos-link:hover {
  background: #e04f00;
  text-decoration: none;
}
</style>