<section id="equipe">
  <div class="container" style="text-align:center;">

    <h2>Equipe</h2>
    <hr class="star-primary">

    {% assign membros = site.members | where: "category", "equipe" %}

    <!-- BASÍLIO -->
    {% for post in membros %}
      {% if post.name == "Basilio Favoretto" %}

        <div style="margin-bottom:60px;">
          
          <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
               onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
               class="img-circle"
               style="width:200px;height:200px;object-fit:cover;display:block;margin:0 auto;">

          <h4 style="margin-top:15px;">{{ post.name }}</h4>
          <p class="text-muted">{{ post.role }}</p>

        </div>

      {% endif %}
    {% endfor %}

    <!-- SEPARADOR -->
    <hr style="margin:40px 0; border-top:1px solid #ddd;">

    <!-- OUTROS -->
    {% assign outros = membros | where_exp: "item", "item.name != 'Basilio Favoretto'" | sort: "name" %}

    <div>

      {% for post in outros %}

        <div style="
          display:inline-block;
          width:30%;
          min-width:220px;
          vertical-align:top;
          margin:1%;
          margin-bottom:40px;
        ">

          <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
               onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
               class="img-circle"
               style="width:200px;height:200px;object-fit:cover;display:block;margin:0 auto;">

          <h4 style="margin-top:15px;">{{ post.name }}</h4>
          <p class="text-muted">{{ post.role }}</p>

        </div>

      {% endfor %}

    </div>

  </div>
</section>