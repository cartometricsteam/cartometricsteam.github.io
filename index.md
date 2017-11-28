---
layout: default
---
<!-- TODO: REMOVE THE DIV SOUP!! -->
<div class="flex-container flex-container--space-around flex-container--fixed">
    <article class="landing">
        <header class="landing__title">
          <h1>{{ site.product.tagline }}</h1>
        </header>
        <p class="landing__description">
          {{ site.product.description }}
        </p>
        <a class="button landing__start" href="{{ site.product.url }}">Get Started</a>
        <a class="button landing__learn" href="{{ site.product.url }}">Learn More</a>
    </article>
  {% unless site.product.demo %}
    <div id="demo" class="demo"></div>
  {% else %}
    <img src="{{ site.demo }}" alt="">
  {% endunless %}
</div>

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

<section id="team">
  <h2 class="h--centered">Our team</h2>
  <ul class="flex-container flex-container--space-around">
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
