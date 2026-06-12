<section id="equipe">
  <div class="container">

    {% assign membros = site.members | where: "category", "equipe" %}

    <!-- BASÍLIO -->
    <div class="row">
      {% for post in membros %}
        {% if post.name == "Basilio" %}
          <div class="col-md-12 text-center" style="margin-bottom:40px;">

            <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
              onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
              class="img-responsive img-circle"
              style="width:200px;height:200px;object-fit:cover;margin:auto;">

            <h4 style="margin-top:15px;">{{ post.name }}</h4>
            <p class="text-muted">{{ post.role }}</p>

          </div>
        {% endif %}
      {% endfor %}
    </div>

    <!-- OUTROS -->
    {% assign outros = membros | where_exp: "item", "item.name != 'Basilio'" | sort: "name" %}

    <div class="row">
      {% for post in outros %}

        <div class="col-md-4 text-center" style="margin-bottom:40px;">

          <img src="{{ site.baseurl }}/img/members/{{ post.img }}"
            onerror="this.onerror=null;this.src='{{ site.baseurl }}/img/members/aeasc.jpg';"
            class="img-responsive img-circle"
            style="width:200px;height:200px;object-fit:cover;margin:auto;">

          <h4 style="margin-top:15px;">{{ post.name }}</h4>
          <p class="text-muted">{{ post.role }}</p>

        </div>

        {% if forloop.index % 3 == 0 and forloop.last == false %}
          </div><div class="row">
        {% endif %}

      {% endfor %}
    </div>

  </div>
</section>