---
layout: page
title: 
permalink: /torneios/torneio-mai-2026/
---

<section id="torneios">
  <div class="container">

    <!-- TITLE -->
    <div class="row">
      <div class="col-lg-12 text-center">
        <h2>2a Etapa Intermediário Masc/Fem & 2a Etapa Sub-15/Sub-17</h2>
        <hr class="star-primary">
      </div>
    </div>

    <!-- CATEGORY -->
    <div class="row text-center" style="margin-bottom:20px;">
      <div class="col-lg-12">
        <h4>Categoria</h4>

        <button class="btn btn-default category-btn" onclick="setCategoria('sub15', this)">Sub-15</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('sub17', this)">Sub-17</button>
        <button class="btn btn-default category-btn" onclick="setCategoria('inter', this)">Intermediário</button>
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
  "sub15-masc": "",
  "sub15-fem":  "https://1drv.ms/x/c/732e38d02ee9cc09/IQDVh7haTrdrTJOLNFiscW7PASMA2tnmrnF3okiCrQlW0NE?e=PdBBaN",

  "sub17-masc": "https://1drv.ms/x/c/732e38d02ee9cc09/IQB8p3kCTLTbSIZBQMIJDqU3AcG7uScR4poMIxr-AHX-GqY?e=bSmvBI",
  "sub17-fem":  "https://1drv.ms/x/c/732e38d02ee9cc09/IQASrdS8U-8ZR53fDbfdXwLfAc7-6MibhEU8Nml-br0y4Wo?e=FLdT1L",


  "inter-masc": "https://1drv.ms/x/c/732e38d02ee9cc09/IQBTIhd-EdBERLPj25jWcEhXAWp67yJRnV3ZPjsuuaxjaEc?e=AaBgJ8",
  "inter-fem":  "https://1drv.ms/x/c/732e38d02ee9cc09/IQD72Nhr9sPjRKbNsccA5A7vARpvjzyILZWgfVRYRlvLyKc?e=ia950b",
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