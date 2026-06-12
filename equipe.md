<section id="equipe">
  <div class="container">

    {% assign membros = site.members | where: "category", "equipe" %}

    <!-- BASÍLIO -->
    <div style="width:100%; text-align:center; margin-bottom:40px;">
      {% for post in membros %}
        {% if post.name == "Basilio Favoretto" %}

          <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
               onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
               class="img-circle"
               style="width:200px;height:200px;object-fit:cover;margin:auto;display:block;">

          <h4 style="margin-top:15px;">{{ post.name }}</h4>
          <p class="text-muted">{{ post.role }}</p>

        {% endif %}
      {% endfor %}
    </div>

    <!-- OUTROS -->
    {% assign outros = membros | where_exp: "item", "item.name != 'Basilio Favoretto'" | sort: "name" %}

    <div style="display:flex; flex-wrap:wrap; justify-content:center;">

      {% for post in outros %}

        <div style="
          width:33.33%;
          min-width:250px;
          text-align:center;
          margin-bottom:40px;
        ">

          <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
               onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
               class="img-circle"
               style="width:200px;height:200px;object-fit:cover;margin:auto;display:block;">

          <h4 style="margin-top:15px;">{{ post.name }}</h4>
          <p class="text-muted">{{ post.role }}</p>

        </div>

      {% endfor %}

    </div>

  </div>
</section>