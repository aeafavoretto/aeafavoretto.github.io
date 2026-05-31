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
            <h2 class="title-lines">
            <span>2ª Etapa Intermediário Masc/Fem</span>
            <span>&amp;</span>
            <span>2ª Etapa Sub-15/Sub-17</span>
            </h2>
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
  "sub15-fem":  "https://1drv.ms/x/c/732e38d02ee9cc09/IQTVh7haTrdrTJOLNFiscW7PAdBZs9iz9NzD6Mx_USdO-I0?em=2&wdAllowInteractivity=False&wdHideHeaders=True&wdInConfigurator=True&edaebf=rslc0",

  "sub17-masc": "https://1drv.ms/x/c/732e38d02ee9cc09/IQR8p3kCTLTbSIZBQMIJDqU3ASeGpn6bl9I2pmv7V530KQY?em=2&wdAllowInteractivity=False&wdHideHeaders=True&wdInConfigurator=True&edaebf=rslc0",
  "sub17-fem":  "https://1drv.ms/x/c/732e38d02ee9cc09/IQQSrdS8U-8ZR53fDbfdXwLfATlBNh-GkCXD6d6LBR1jE-g?em=2&wdAllowInteractivity=False&wdHideHeaders=True&wdInConfigurator=True&edaebf=rslc0",


  "inter-masc": "https://1drv.ms/x/c/732e38d02ee9cc09/IQRTIhd-EdBERLPj25jWcEhXAXLQ40yNBLmAYPBEEi5U-y0?em=2&wdAllowInteractivity=False&wdHideHeaders=True&wdInConfigurator=True&edaebf=rslc0",
  "inter-fem":  "https://1drv.ms/x/c/732e38d02ee9cc09/IQT72Nhr9sPjRKbNsccA5A7vAfzo05ajF8dflEP_jOfCmss?em=2&wdAllowInteractivity=False&wdHideHeaders=True&wdInConfigurator=True&edaebf=rslc0",
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