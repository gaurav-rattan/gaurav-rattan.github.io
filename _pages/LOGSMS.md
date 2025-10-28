---
layout: page
title: LOGSMS
permalink: /LOGSMS/
nav: false
nav_order: 5

---

<!-- HERO BLOCK — the introductory section of the page -->
<div class="logsms-hero">

  <!-- Main project title -->
  <h1>LOGSMS</h1>

  <!-- Short tagline -->
  <p class="subtitle">
    Learning on Graphs: Symmetry Meets Structure
  </p>

  <!-- One-paragraph description -->
  <p class="subdesc">
    LOGSMS develops a mathematical foundation for Graph Neural Networks—
    connecting graph isomorphisms, homomorphisms, and graph limits—
    to improve expressivity, scalability, and generalization.
  </p>

  <!-- Call-to-action buttons -->
  <p class="cta-row">
    <a class="btn-ghost" href="#publications">See our papers</a>
    <a class="btn-ghost" href="#open-positions">Open positions</a>
    <a class="btn-ghost" href="https://github.com/YOUR_GITHUB">GitHub</a>
  </p>
</div>


{% include logsms/section.html title="Team" id="team" %}
<div class="logsms-team-grid">
  {% for p in site.data.logsms_team %}
    {% include logsms/person.html person=p %}
  {% endfor %}
</div>


{% include logsms/section.html title="Publications" id="publications" %}

{% assign pubs = site.publications | where_exp: "p", "p.tags contains 'logsms'" | sort: 'year' | reverse %}
{% if pubs and pubs.size > 0 %}
  <ul class="paper-list">
    {% for p in pubs %}
      <li>
        <strong>{{ p.title }}</strong>
        {% if p.year %} ({{ p.year }}){% endif %}
        <br>
        {% if p.authors %}<span class="text-muted">{{ p.authors }}</span><br>{% endif %}
        {% if p.arxiv %}<a href="{{ p.arxiv }}">arXiv</a>{% endif %}
        {% if p.doi %}{% if p.arxiv %} · {% endif %}<a href="https://doi.org/{{ p.doi }}">DOI</a>{% endif %}
        {% if p.code %}{% if p.arxiv or p.doi %} · {% endif %}<a href="{{ p.code }}">code</a>{% endif %}
      </li>
    {% endfor %}
  </ul>
{% else %}
  <p>No LOGSMS-tagged publications yet. First preprints coming soon.</p>
{% endif %}




{% include logsms/section.html title="Open Positions" id="open-positions" %}
<p>Future hiring info goes here.</p>



{% include logsms/section.html title="News" id="news" %}

{%- assign logsms_posts = site.news | where_exp: "p", "p.tags contains 'logsms'" -%}
{%- assign recent = logsms_posts | slice: 0, 6 -%}

{% if recent and recent.size > 0 %}
  <ul class="logsms-news">
  {% for n in recent %}
    <li>
      <a href="{{ n.url | relative_url }}">{{ n.title }}</a>
      <span class="date">— {{ n.date | date: "%b %d, %Y" }}</span>
      {%- if n.excerpt -%}
        <div class="excerpt">{{ n.excerpt | strip_html | truncate: 140 }}</div>
      {%- endif -%}
    </li>
  {% endfor %}
  </ul>

  {% if logsms_posts.size > recent.size %}
    <p class="more">
      <a href="{{ '/tag/logsms/' | relative_url }}">All LOGSMS news →</a>
    </p>
  {% endif %}
{% else %}
  <p>No LOGSMS news yet. Stay tuned!</p>
{% endif %}


