---
layout: default
---
<!-- TODO: REMOVE THE DIV SOUP!! -->
<div class="flex-container flex-container--space-around flex-container--fixed">
  <div class="flex-container flex-container--vertical flex-container--start-align">
    <article class="card">
        <header class="card__header card__header--no-padding">
          <h1>{{ site.product.tagline }}</h1>
        </header>
        <p class="card__body card__body--no-padding">
          {{ site.product.description }}
        </p>
    </article>
    <div class="flex-container flex-container--space-around">
      <a class="button" href="{{ site.product.url }}">Get Started</a>
      <a class="button" href="{{ site.product.url }}">Learn More</a>
    </div>
  </div>
  {% unless site.product.demo %}
    <div id="demo" class="demo"></div>
  {% else %}
    <img src="{{ site.demo }}" alt="">
  {% endunless %}
</div>

<!-- <section id="features">
  <h2>Why {{ site.product.name }}</h2>

</section> -->

<section id="blog">
  <h2 class="h--centered">Blog</h2>
    <ul class="flex-container flex-container--space-around">
      {% for post in site.posts %}
        {% assign time_to_read = post.content | number_of_words | divided_by: 180.0 | round %}
        <li>
          <a href="{{ post.url | relative_url }}">
            <article class="card card--shadow">
              <header class="card__header card__header--padded">
                <h3>{{ post.title | escape }}</h3>
                <span class="card__meta">{{ site.data.authors[post.author].name | default: site.name }} · <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%d %b, %Y" }}</time> · <time datetime="{{ "PT" | append: time_to_read | append: "M" }}">{{ time_to_read }} min</time></span>
              </header>
              <img src="{{ post.image }}" alt="" class="card__image">
              <p class="card__body">{{ post.excerpt | strip_html | truncate: 143 }}</p>
            </article>
          </a>
        </li>
      {% endfor %}
    </ul>
</section>

<!-- <article id="about" class="horizontal-card">
  <h2 class="horizontal-card__title">Who we are</h2>
    <figure class="horizontal-card__element">
      <img src="{{ site.data.organization.logo }}" alt="{{ site.data.organization.name }}">
      {% if site.data.organization.sameAs %}
        {% include social-profiles.html sites=site.data.organization.sameAs %}
      {% endif %}
    </figure>
    <p class="horizontal-card__element">
      {{ site.data.organization.description }}
    </p>

  <ol class="timeline">
    {% for event in site.data.timeline %}
        <li class="timeline__event">
          <a href="#">
            <article>
              <time datetime="{{ event.date | date_to_xmlschema }}" class="timeline__date"> {{  event.date | date: "%d %b, %Y" }}</time>
              <h3>{{ event.title }}</h3>
              <p>
                {{ event.text | truncate: 40 }}
              </p>
            </article>
          </a>
        </li>
    {% endfor %}
  </ol>
</article> -->

<section id="team">
  <h2 class="h--centered">Our team</h2>
  <ul class="flex-container flex-container--space-arond">
    {% for author in site.data.authors %}
      <li>
        <article id="{{ author.first }}" class="card card--shadow">
          <header class="card__header">
            <h3>{{ author.last.name }}</h3>
            <p class="card__meta">{{ author.last.job }}</p>
          </header>
          <figure class="card__image">
            <img src="{{ author.last.image }}" alt="">
            <figcaption>
              {% include social-profiles.html profiles= author.last.social %}
            </figcaption>
          </figure>
          <p class="card__body">
            {{ author.last.description }}
          </p>
        </article>
      </li>
    {% endfor %}
  </ul>
</section>
