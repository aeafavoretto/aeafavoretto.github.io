---
layout: page
title: 
permalink: /torneios/torneio-ago-2026-2a/
---

<section id="torneios">
  <div class="container">

    <!-- TÍTULO -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2 class="title-lines">
          <span>2ª Etapa Inter-Escolar do Circuito AEA de Vôlei de Praia</span>
        </h2>
        <hr class="star-primary">
      </div>
    </div>

    <!-- MODALITY -->
    <div class="row text-center" style="margin-bottom:30px;">
      <div class="col-lg-12">
        <h4>Gênero</h4>

        <button class="btn btn-default gender-btn" onclick="setGenero('masc', this)">Masculino</button>
        <button class="btn btn-default gender-btn" onclick="setGenero('fem', this)">Feminino</button>
      </div>
    </div>

    <!-- MESSAGE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <p id="message" class="text-muted">
          Selecione um gênero.
        </p>
      </div>
    </div>

    <!-- DISPLAY -->
    <div class="row">
      <div class="col-lg-12 text-center">
      
        <!-- IFRAME -->
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
// let regulamentoSelecionado = "";
let categoriaSelecionada = "sub";
let generoSelecionado = "";

/* === SHEETS === */
const sheetMap = {
  "sub-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRy0DN0kfJZR6KAK8KtaUsvAdgYQssIDcYnBRjRNiStVOQ?em=2&wdAllowInteractivity=False&Item='SUB%20MASC'!A1%3ABB500&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "sub-fem": "https://1drv.ms/x/c/b894b1671d1e3831/IQRy0DN0kfJZR6KAK8KtaUsvAdgYQssIDcYnBRjRNiStVOQ?em=2&wdAllowInteractivity=False&Item='SUB%20FEM'!A1%3ABB500&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",

/* === GENDER === */
function setGenero(gen, element) {

  generoSelecionado = (generoSelecionado === gen) ? "" : gen;

  document.querySelectorAll(".gender-btn").forEach(btn => {
    btn.classList.remove("active");
  });

  if (generoSelecionado) element.classList.add("active");

  updateBracket();
}

/* === UPDATE === */
function updateBracket() {

  const iframe = document.getElementById("bracket-frame");
  const message = document.getElementById("message");

  if (!generoSelecionado) {
    iframe.style.display = "none";
    message.style.display = "block";
    return;
  }

  const key = "sub-" + generoSelecionado;

  if (sheetMap[key]) {

    iframe.src = sheetMap[key];

    iframe.style.display = "block";
    message.style.display = "none";

  } else {

    iframe.style.display = "none";
    message.style.display = "block";
  }
}
</script>
