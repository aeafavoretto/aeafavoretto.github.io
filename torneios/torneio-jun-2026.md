---
layout: page
title: 
permalink: /torneios/torneio-jun-2026/
---

<section id="torneios">
  <div class="container">

    <!-- TITLE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2 class="title-lines">
          <span>2ª Etapa do 4º Circuito AEA de Vôlei de Praia</span>
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
const regulamentoLink = "https://1drv.ms/x/c/b894b1671d1e3831/IQTRBNrxqSUXQptynbVlWKFSAbrqZRBGV5aOQmT0hcSsZNs?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E";

/* === ONLY THESE TWO HAVE IMAGES === */
const imageMap = {
  "sub15-masc": "/img/torneio/notavailable.jpeg",
  "sub21-fem": "/img/torneio/notavailable.jpeg"
};

/* === SHEETS === */
const sheetMap = {
  "sub15-masc": "",
  "sub15-fem": "https://1drv.ms/x/c/b894b1671d1e3831/IQS999Xk9oDsRZaWtuAyTDcmAQfbWMnEkULavtbZzDYfPcI?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",

  "sub17-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQSg-BBiHhjvSJiZEAZ7_w4SAYU-FRZtfUl5RetruLn_saM?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",
  "sub17-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQSAllKj_CuFQo68V79ABewMAY94hmXwh6OgD607dF2cTtw?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",

  "sub19-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQR2G9GULCOGTZb5N6SSexzpAek39c4HOr1s_BG0dWMjSHU?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",
  "sub19-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQRprjv4Jc_2S7ej48j1Cz97AVVY6Yj5fghb0M7-vAQoOqU?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",

  "sub21-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRzueyN3_ioSKpr7BtGJorXARiLOY5-x3K2THSCyCrahgo?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",
  "sub21-fem":  "",

  "quali-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRGfggDR-jVQqIFk-EzCutHAYHkBuh6-5R83sHXQ_A4svU?em=2&wdAllowInteractivity=False&ActiveCell=%27Duplas_Quali%27!C12&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",
  "quali-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQRP3FbZKKX1SJ1F8nrmC822Abc0G9jcKnf-2yBM-HLPc-s?em=2&wdAllowInteractivity=False&ActiveCell=%27Duplas_Quali%27!A1&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",

  "open-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRGfggDR-jVQqIFk-EzCutHAYHkBuh6-5R83sHXQ_A4svU?em=2&wdAllowInteractivity=False&ActiveCell=%27Duplas%27!A1&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",
  "open-fem":  "https://1drv.ms/x/c/b894b1671d1e3831/IQRP3FbZKKX1SJ1F8nrmC822Abc0G9jcKnf-2yBM-HLPc-s?em=2&wdAllowInteractivity=False&ActiveCell=%27Duplas%27!A1&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E",
};

/* === REGULAMENTO === */
function setRegulamento(reg, element) {

  const iframe = document.getElementById("bracket-frame");
  const image = document.getElementById("bracket-image");
  const message = document.getElementById("message");

  if (regulamentoSelecionado === reg) {
    regulamentoSelecionado = "";
    element.classList.remove("active");

    iframe.style.display = "none";
    image.style.display = "none";
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

  if (!categoriaSelecionada || !generoSelecionado) {
    iframe.style.display = "none";
    image.style.display = "none";
    message.style.display = "block";
    return;
  }

  const key = categoriaSelecionada + "-" + generoSelecionado;

  // ONLY THESE 2 USE IMAGE
  if (imageMap[key]) {
    image.src = imageMap[key];
    image.style.display = "block";

    iframe.style.display = "none";
    message.style.display = "none";
    return;
  }

  // ALL OTHERS USE IFRAME
  if (sheetMap[key]) {
    iframe.src = sheetMap[key];
    iframe.style.display = "block";

    image.style.display = "none";
    message.style.display = "none";
  }
}
</script>