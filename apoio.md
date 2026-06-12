<section id="apoio">
  <div class="container" style="text-align:center;">

    <h2>Apoio</h2>
    <hr class="star-primary">

    {% assign sponsors = site.data.sponsors %}

    <!-- APOIADOR DE DESTAQUE -->
    {% for sponsor in sponsors %}
      {% if sponsor.name == "Nome do Apoiador Principal" %}

        <div style="margin-bottom:60px;">

          <img src="{{ '/img/sponsors/' | append: sponsor.img | relative_url }}"
               onerror="this.onerror=null;this.src='{{ '/img/sponsors/default.png' | relative_url }}';"
               style="width:220px;height:220px;object-fit:contain;display:block;margin:0 auto;">

          <h4 style="margin-top:15px;">{{ sponsor.name }}</h4>

        </div>

      {% endif %}
    {% endfor %}

    <!-- SEPARADOR -->
    <hr style="margin:40px 0; border-top:1px solid #ddd;">

    <!-- OUTROS APOIADORES -->
    {% assign outros = sponsors | where_exp: "item", "item.name != 'Nome do Apoiador Principal'" | sort: "name" %}

    <div>

      {% for sponsor in outros %}

        <div style="
          display:inline-block;
          width:30%;
          min-width:220px;
          vertical-align:top;
          margin:1%;
          margin-bottom:40px;
        ">

          <img src="{{ '/img/sponsors/' | append: sponsor.img | relative_url }}"
               onerror="this.onerror=null;this.src='{{ '/img/sponsors/default.png' | relative_url }}';"
               style="width:180px;height:180px;object-fit:contain;display:block;margin:0 auto;">

          <h5 style="margin-top:10px;">{{ sponsor.name }}</h5>

        </div>

      {% endfor %}

    </div>

  </div>
</section>