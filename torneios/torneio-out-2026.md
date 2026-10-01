---
layout: page
title: 
permalink: /torneios/torneio-out-2026/
---

<section id="torneios">
  <div class="container">

    <!-- TITLE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2 class="title-lines">
          <span>3ª Etapa do 4º Circuito AEA de Vôlei de Praia</span>
        </h2>
        <hr class="star-primary">
      </div>
    </div>

    <!-- REGULAMENTO -->
    <div class="row text-center" style="margin-bottom:20px;">
      <div class="col-lg-12">
        <h4>Regulamento</h4>

        <button class="btn btn-default regulamento-btn"
          onclick="setRegulamento('reg', this)">
          Regulamento
        </button>
      </div>
    </div>

    <!-- CATEGORY -->
    <div class="row text-center" style="margin-bottom:20px;">
      <div class="col-lg-12">
        <h4>Categoria</h4>

        <button class="btn btn-default category-btn" onclick="setCategoria('sub15', this)">Sub-15</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('sub17', this)">Sub-17</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('sub19', this)">Sub-19</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('sub21', this)">Sub-21</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('quali', this)">Quali</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('open', this)">Open</button>
      </div>
    </div>

    <!-- MODALITY -->
    <div class="row text-center" style="margin-bottom:30px;">
      <div class="col-lg-12">
        <h4>Modalidade</h4>

        <button class="btn btn-default gender-btn" onclick="setGenero('masc', this)">Masculino</button>
        <button class="btn btn-default gender-btn" onclick="setGenero('fem', this)">Feminino</button>
      </div>
    </div>

    <!-- MESSAGE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <p id="message" class="text-muted">
          Selecione uma categoria e uma modalidade ou clique em Regulamento.
        </p>
      </div>
    </div>

    <!-- DISPLAY -->
    <div class="row">
      <div class="col-lg-12 text-center">

        <!-- FOTO DOS CAMPEÕES -->
        <div id="winner-photo-container"
            style="display:none; margin-bottom:20px;">

          <img id="winner-photo"
              style="max-width:100%; border-radius:8px;" />

        </div>

        <!-- IFRAME -->
        <iframe id="bracket-frame"
          width="100%"
          height="700"
          frameborder="0"
          scrolling="yes"
          style="border:none; display:none;">
        </iframe>

        <!-- IMAGE -->
        <img id="bracket-image"
             style="max-width:100%; display:none; margin-top:20px;" />

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
let categoriaSelecionada = "";
let generoSelecionado = "";

/* === REGULAMENTO === */
const regulamentoLink = "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='DISPUTA'!A1&Item='DISPUTA'!A1%3AO13&wdInConfigurator=True&wdInConfigurator=True";

/* === ONLY THESE TWO HAVE IMAGES === */
const imageMap = {
  "sub15-masc": "/img/torneio/notavailable.jpeg",
  "sub21-fem": "/img/torneio/notavailable.jpeg"
};

const winnersMap = {
  "sub15-fem": "",
  "sub17-masc": "",
  "sub17-fem": "",
  "sub19-masc": "",
  "sub19-fem": "",
  "sub21-masc": "",
  "open-masc": "",
  "open-fem": "",
};

/* === SHEETS === */
const sheetMap = {
  "sub15-masc": "",
  "sub15-fem": "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='SUB 15 FEM'!A1&Item='SUB%2015%20FEM'!A1%3ABA62&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",

  "sub17-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='SUB 17 MASC'!A1&Item='SUB%2017%20MASC'!A1%3ABA49&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "sub17-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='SUB 17 FEM'!A1&Item='SUB%2017%20FEM'!A1%3ABA95&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",

  "sub19-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='SUB 19 MASC'!A1&Item='SUB%2019%20MASC'!A1%3ABA60&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "sub19-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='SUB 19 FEM'!A1&Item='SUB%2019%20FEM'!A1%3ABA62&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",

  "sub21-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='SUB 21 MASC'!A1&Item='SUB%2021%20MASC'!A1%3ABA58&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "sub21-fem":  "",

  "quali-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='QUALI MASC'!A1&Item='QUALI%20MASC'!A1%3AAX23&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "quali-fem":  "",

  "open-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='OPEN MASC'!A1&Item='OPEN%20MASC'!A1%3ABB67&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "open-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQRsxQT3TqPMSZiCYK833A9hAfQk1Vkpn1MQtaULKNTo3is?em=2&wdAllowInteractivity=False&ActiveCell='OPEN FEM'!A1&Item='OPEN%20FEM'!A1%3ABB67&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
};

/* === REGULAMENTO === */
function setRegulamento(reg, element) {

  const iframe = document.getElementById("bracket-frame");
  const image = document.getElementById("bracket-image");
  const message = document.getElementById("message");
  const winnerPhotoContainer = document.getElementById("winner-photo-container");

  if (regulamentoSelecionado === reg) {
    regulamentoSelecionado = "";
    element.classList.remove("active");

    iframe.style.display = "none";
    image.style.display = "none";
    winnerPhotoContainer.style.display = "none";
    message.style.display = "block";

  } else {
    regulamentoSelecionado = reg;

    document.querySelectorAll("button").forEach(btn => {
      btn.classList.remove("active");
    });

    element.classList.add("active");

    categoriaSelecionada = "";
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

  const key = categoriaSelecionada + "-" + generoSelecionado;

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