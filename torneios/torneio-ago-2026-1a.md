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
          <span>2ª Etapa do 4º Circuito AEA de Vôlei de Praia</span>
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
let categoriaSelecionada = "kids";
let generoSelecionado = "";

// /* === REGULAMENTO === */
// const regulamentoLink = "https://1drv.ms/x/c/b894b1671d1e3831/IQTRBNrxqSUXQptynbVlWKFSAbrqZRBGV5aOQmT0hcSsZNs?em=2&wdAllowInteractivity=False&wdHideGridlines=True&wdHideHeaders=True&wdInConfigurator=True&wdInConfigurator=True&edaebf=rslc0%22%3E%3C/iframe%3E";

// /* === ONLY THESE TWO HAVE IMAGES === */
// const imageMap = {
//   "sub15-masc": "/img/torneio/notavailable.jpeg",
//   "sub21-fem": "/img/torneio/notavailable.jpeg"
// };

// const winnersMap = {
//   "sub15-fem": "/img/torneio/jun26/sub15-fem.jpeg",
//   "sub17-masc": "/img/torneio/jun26/sub17-masc.jpeg",
//   "sub17-fem": "/img/torneio/jun26/sub17-fem.jpeg",
//   "sub19-masc": "/img/torneio/jun26/sub19-masc.jpeg",
//   "sub19-fem": "/img/torneio/jun26/sub19-fem.jpeg",
//   "sub21-masc": "/img/torneio/jun26/sub21-masc.jpeg",
//   "open-masc": "/img/torneio/jun26/open-masc.jpeg",
//   "open-fem": "/img/torneio/jun26/open-fem.jpeg",
  
// };

/* === SHEETS === */
const sheetMap = {
  "kids-masc": "https://1drv.ms/x/c/b894b1671d1e3831/IQRy0DN0kfJZR6KAK8KtaUsvAdgYQssIDcYnBRjRNiStVOQ?em=2&wdAllowInteractivity=False&Item='SUB%20MASC'!A1%3ABB500&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
  "kids-fem": "https://1drv.ms/x/c/b894b1671d1e3831/IQRy0DN0kfJZR6KAK8KtaUsvAdgYQssIDcYnBRjRNiStVOQ?em=2&wdAllowInteractivity=False&Item='SUB%20FEM'!A1%3ABB500&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True",
};

// /* === REGULAMENTO === */
// function setRegulamento(reg, element) {

//   const iframe = document.getElementById("bracket-frame");
//   const image = document.getElementById("bracket-image");
//   const message = document.getElementById("message");
//   const winnerPhotoContainer = document.getElementById("winner-photo-container");

//   if (regulamentoSelecionado === reg) {
//     regulamentoSelecionado = "";
//     element.classList.remove("active");

//     iframe.style.display = "none";
//     image.style.display = "none";
//     winnerPhotoContainer.style.display = "none";
//     message.style.display = "block";

//   } else {
//     regulamentoSelecionado = reg;

//     document.querySelectorAll("button").forEach(btn => {
//       btn.classList.remove("active");
//     });

//     element.classList.add("active");

//     categoriaSelecionada = "";
//     generoSelecionado = "";

//     iframe.src = regulamentoLink;
//     iframe.style.display = "block";
//     image.style.display = "none";
//     winnerPhotoContainer.style.display = "none";
//     message.style.display = "none";
//   }
// }

// /* === CATEGORY === */
// function setCategoria(cat, element) {

//   categoriaSelecionada = (categoriaSelecionada === cat) ? "" : cat;

//   document.querySelectorAll(".category-btn").forEach(btn => {
//     btn.classList.remove("active");
//   });

//   if (categoriaSelecionada) element.classList.add("active");

//   updateBracket();
// }

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

  const key = "kids-" + generoSelecionado;

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
