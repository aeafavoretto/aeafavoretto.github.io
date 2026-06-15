<section id="apoio">
  <div class="container" style="text-align:center;">

    <h2>Apoio</h2>
    <hr class="star-primary">
    
    <hr style="margin:40px 0; border-top:1px solid #ddd;">

    {% assign sponsors = site.data.sponsors %}

    {% for sponsor in sponsors %}

      {% if forloop.first %}
        <!-- DESTAQUE -->
        <div style="margin-bottom:60px;">

          <a href="{{ sponsor.url }}" target="_blank">
            <img src="{{ '/img/sponsors/' | append: sponsor.img | relative_url }}"
                 onerror="this.onerror=null;this.src='{{ '/img/sponsors/default.png' | relative_url }}';"
                 style="max-width:220px; display:block; margin:0 auto;">
          </a>

          <h4 style="margin-top:15px;">{{ sponsor.name }}</h4>

        </div>

        <!-- <hr style="margin:40px 0; border-top:1px solid #ddd;"> -->

        <div>

      {% else %}
        <!-- OUTROS -->
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
      {% endif %}

      {% if forloop.last %}
        </div>
      {% endif %}

    {% endfor %}

  </div>
</section>