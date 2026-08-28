---
layout: page
title: 
permalink: /torneios/torneio-ago-2026-1a/
---

<section id="torneios">
  <div class="container">

    <!-- TITLE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2 class="title-lines">
          <span>1ª Etapa Kids do Circuito AEA de Vôlei de Praia</span>
        </h2>
        <hr class="star-primary">
      </div>
    </div>

    <!-- MODALITY -->
    <div class="row text-center" style="margin-bottom:30px;">
      <div class="col-lg-12">
        <h4>Gênero</h4>

        <button class="btn btn-default gender-btn" onclick="setGenero('kids-masc', this)">Masculino</button>
        <button class="btn btn-default gender-btn" onclick="setGenero('kids-fem', this)">Feminino</button>
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
let regulamentoSelecionado = "";
let categoriaSelecionada = "kids";
let generoSelecionado = "";

/* === REGULAMENTO === */
const regulamentoLink = "https://1drv.ms/x/c/b894b1671d1e3831/IQTRBNrxqSUXQptynbVlWKFSAbrqZRBGV5aOQmT0hcSsZNs?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E";

/* === SHEETS === */
const sheetMap = {
  "kids-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRy0DN0kfJZR6KAK8KtaUsvAdgYQssIDcYnBRjRNiStVOQ?em=2&wdAllowInteractivity=False&Item='SUB%20MASC'!A1%3ABB500&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "kids-fem": "https://1drv.ms/x/c/b894b1671d1e3831/IQRy0DN0kfJZR6KAK8KtaUsvAdgYQssIDcYnBRjRNiStVOQ?em=2&wdAllowInteractivity=False&Item='SUB%20FEM'!A1%3ABB500&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
};

/* === REGULAMENTO === */
function setRegulamento(reg, element) {

  const iframe = document.getElementById("bracket-frame");
  const image = document.getElementById("bracket-image");
  const message = document.getElementById("message");
  const winnerPhotoContainer = document.getElementById("winner-photo-container");

    element.classList.add("active");

    // categoriaSelecionada = "kids";
    generoSelecionado = "";

    iframe.src = regulamentoLink;
    iframe.style.display = "block";
    image.style.display = "none";
    winnerPhotoContainer.style.display = "none";
    message.style.display = "none";
  }
}

/* === CATEGORY === */
function setCategoria(cat, element) {

  categoriaSelecionada = (categoriaSelecionada === cat) ? "" : cat;

  document.querySelectorAll(".category-btn").forEach(btn => {
    btn.classList.remove("active");
  });

  if (categoriaSelecionada) element.classList.add("active");

  updateBracket();
}

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
  const image = document.getElementById("bracket-image");
  const message = document.getElementById("message");

  const winnerPhotoContainer =
    document.getElementById("winner-photo-container");

  const winnerPhoto =
    document.getElementById("winner-photo");

  if (!categoriaSelecionada || !generoSelecionado) {

    iframe.style.display = "none";
    image.style.display = "none";
    winnerPhotoContainer.style.display = "none";
    message.style.display = "block";

    return;
  }

  const key = generoSelecionado;

  /* MOSTRA FOTO DOS CAMPEÕES SE EXISTIR */
  if (winnersMap[key]) {
    winnerPhoto.src = winnersMap[key];
    winnerPhotoContainer.style.display = "block";
  } else {
    winnerPhotoContainer.style.display = "none";
  }

  /* MODALIDADES COM IMAGEM */
  if (imageMap[key]) {

    image.src = imageMap[key];

    image.style.display = "block";
    iframe.style.display = "none";
    message.style.display = "none";

    return;
  }

  /* MODALIDADES COM PLANILHA */
  if (sheetMap[key]) {

    iframe.src = sheetMap[key];

    iframe.style.display = "block";
    image.style.display = "none";
    message.style.display = "none";

  } else {

    iframe.style.display = "none";
    image.style.display = "none";
    message.style.display = "block";
  }
}
</script>