<section id="apoio">
  <div class="container" style="text-align:center;">

    <h2>Apoio</h2>
    <hr class="star-primary">

    {% assign sponsors = site.data.sponsors %}

    <!-- DESTAQUE -->
    {% if sponsors.size > 0 %}
      {% assign principal = sponsors[0] %}

      <div style="margin-bottom:60px;">

        <a href="{{ principal.url }}" target="_blank">
          <img src="{{ '/img/sponsors/' | append: principal.img | relative_url }}"
               onerror="this.onerror=null;this.src='{{ '/img/sponsors/default.png' | relative_url }}';"
               style="max-width:220px; display:block; margin:0 auto;">
        </a>

        <h4 style="margin-top:15px;">{{ principal.name }}</h4>

      </div>
    {% endif %}

    <!-- SEPARADOR -->
    <hr style="margin:40px 0; border-top:1px solid #ddd;">

    <!-- OUTROS -->
    <div>

      {% for sponsor in sponsors offset:1 %}

        <div style="
          display:inline-block;
          width:30%;
          min-width:220px;
          vertical-align:top;
          margin:1%;
          margin-bottom:40px;
        ">

          <a href="{{ sponsor.url }}" target="_blank">
            <img src="{{ '/img/sponsors/' | append: sponsor.img | relative_url }}"
                 onerror="this.onerror=null;this.src='{{ '/img/sponsors/default.png' | relative_url }}';"
                 style="max-width:180px; display:block; margin:0 auto;">
          </a>

          <h5 style="margin-top:10px;">{{ sponsor.name }}</h5>

        </div>

      {% endfor %}

    </div>

  </div>
</section>
``