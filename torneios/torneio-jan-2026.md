---
layout: page
title: Torneio Jun 2026
permalink: /torneios/torneio-jun-2026/
---

<section id="torneios">
  <div class="container">

    <!-- TITLE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2>{{ page.title }}</h2>
        <hr class="star-primary">
      </div>
    </div>

    <!-- CATEGORY -->
    <div class="row text-center" style="margin-bottom:20px;">
      <div class="col-lg-12">
        <h4>Categoria</h4>

        <button class="btn btn-default category-btn" onclick="setCategoria('sub17', this)">Sub-17</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('sub19', this)">Sub-19</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('sub21', this)">Sub-21</button>
      </div>
    </div>

    <!-- MODALITY -->
    <div class="row text-center" style="margin-bottom:30px;">
      <div class="col-lg-12">
        <h4>Modalidade</h4>

        <button class="btn btn-default gender-btn" onclick="setGenero('masc', this)">Masculino</button>
        <button class="btn btn-default gender-btn" onclick="setGenero('fem', this)">Feminino</button>
        <button class="btn btn-default gender-btn" onclick="setGenero('misto', this)">Misto</button>
      </div>
    </div>

    <!-- MESSAGE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <p id="message" class="text-muted">
          Selecione uma categoria e uma modalidade para visualizar a tabela.
        </p>
      </div>
    </div>

    <!-- IFRAME -->
    <div class="row">
      <div class="col-lg-12 text-center">

        <iframe id="bracket-frame"
          width="100%"
          height="700"
          frameborder="0"
          scrolling="yes"
          style="border:none; display:none;">
        </iframe>

      </div>
    </div>

  </div>
</section>

<style>
.btn.active {
  background-color: #18bc9c;
  color: white;
  border: none;
}
</style>

<script>
let categoriaSelecionada = "";
let generoSelecionado = "";

/* === ONEDRIVE EMBED LINKS === */
const sheetMap = {
  "sub17-masc": "https://1drv.ms/x/c/a965a62246706b8b/IQTeeCUDmA2uSoME6SKR5-XmAXIrlhKSYFGvL-YpxXGgF-k?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",
  "sub17-fem":  "https://1drv.ms/x/c/a965a62246706b8b/IQQ5JCIkRpGdS7zrS-DgzzjGARho_Fdq_7lnw25pzwut5iM?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",
  "sub17-misto":"https://1drv.ms/x/c/a965a62246706b8b/IQRalEceru88TrNH-zUNhcowAWfm6xsct-S7E-_wnAO-Gok?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",

  "sub19-masc": "https://1drv.ms/x/c/a965a62246706b8b/IQSXorE7LWyrRJoJ2ikueBMRAUcXsOfxDYtLLarfAlDxLq4?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",
  "sub19-fem":  "https://1drv.ms/x/c/a965a62246706b8b/IQRrjO5zT3enSaqeKoCuSza_AXHy0OyHtVNewq02li9fIVY?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",
  "sub19-misto":"https://1drv.ms/x/c/a965a62246706b8b/IQSo8PgJilROR6V92pqn5OHDAah_GhExSqa3IKKSNcXQUvc?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",


  "sub21-masc": "https://1drv.ms/x/c/a965a62246706b8b/IQRWAfVhZ9M0RqmZEiJCXtuyAX2HXej6QrRaOsvUlJKfY48?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",
  "sub21-fem":  "https://1drv.ms/x/c/a965a62246706b8b/IQTs8msxg4eVR4RfUZg-DvbPASeG3vPXn56GMe6vDtR38YY?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0",
  "sub21-misto":"https://1drv.ms/x/c/a965a62246706b8b/IQR0Ek58RYSzSrTpHQ8w5TtiAfbuDhznaTvy0HLTunHzCsE?em=2&wdAllowInteractivity=False&wdInConfigurator=True&edaebf=rslc0"
};

/* === CATEGORY CLICK === */
function setCategoria(cat, element) {
  categoriaSelecionada = cat;

  document.querySelectorAll(".category-btn").forEach(btn => {
    btn.classList.remove("active");
  });

  element.classList.add("active");
  updateBracket();
}

/* === GENDER CLICK === */
function setGenero(gen, element) {
  generoSelecionado = gen;

  document.querySelectorAll(".gender-btn").forEach(btn => {
    btn.classList.remove("active");
  });

  element.classList.add("active");
  updateBracket();
}

/* === UPDATE IFRAME === */
function updateBracket() {
  const key = categoriaSelecionada + "-" + generoSelecionado;
  const iframe = document.getElementById("bracket-frame");
  const message = document.getElementById("message");

  if (sheetMap[key]) {
    iframe.src = sheetMap[key]; // ✅ direct embed link only
    iframe.style.display = "block";
    message.style.display = "none";
  }
}
</script>