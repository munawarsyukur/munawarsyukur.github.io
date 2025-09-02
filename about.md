---
layout: page
title: "Tentang"
permalink: /about/
---

<link rel="stylesheet" href="/assets/css/resume.css">

{% assign r = site.data.resume %}

<div class="cv">
  <header class="cv__header">
    <h1 class="cv__name">{{ r.name }}</h1>
    <p class="cv__headline">{{ r.headline }}</p>
    <ul class="cv__meta">
      <li>📍 {{ r.location }}</li>
      <li>📧 <a href="mailto:{{ r.email }}">{{ r.email }}</a></li>
      {% for l in r.links %}
        <li>🔗 <a href="{{ l.url }}" rel="me">{{ l.text }}</a></li>
      {% endfor %}
    </ul>
    <button class="cv__print" onclick="window.print()">Unduh PDF</button>
  </header>

  <section class="cv__section">
    <h2>Ringkasan</h2>
    <p>{{ r.summary }}</p>
  </section>

  <section class="cv__section">
    <h2>Keahlian</h2>
    <ul class="cv__tags">
      {% for s in r.skills %}<li>{{ s }}</li>{% endfor %}
    </ul>
  </section>

  <section class="cv__section">
    <h2>Pengalaman</h2>
    {% for e in r.experience %}
    <div class="cv__item">
      <div class="cv__item-head">
        <strong>{{ e.role }}</strong> · {{ e.company }}
        <span class="cv__time">{{ e.time }}</span>
      </div>
      <ul class="cv__bullets">
        {% for b in e.bullets %}<li>{{ b }}</li>{% endfor %}
      </ul>
      {% if e.stack %}<div class="cv__stack">Stack: {{ e.stack }}</div>{% endif %}
    </div>
    {% endfor %}
  </section>

  <section class="cv__section">
    <h2>Proyek Terpilih</h2>
    {% for p in r.projects %}
    <div class="cv__item">
      <div class="cv__item-head">
        <strong>{{ p.name }}</strong><span class="cv__time">{{ p.time }}</span>
      </div>
      <p>{{ p.desc }}</p>
      {% if p.links %}
        <p>
          {% for link in p.links %}
            🔗 <a href="{{ link.url }}">{{ link.text }}</a>{% unless forloop.last %} · {% endunless %}
          {% endfor %}
        </p>
      {% endif %}
    </div>
    {% endfor %}
  </section>

  <section class="cv__section">
    <h2>Pendidikan</h2>
    {% for ed in r.education %}
    <div class="cv__item">
      <div class="cv__item-head"><strong>{{ ed.title }}</strong> · {{ ed.org }}</div>
      <div class="cv__time">{{ ed.time }}</div>
    </div>
    {% endfor %}
  </section>

  {% if r.certs %}
  <section class="cv__section">
    <h2>Sertifikasi</h2>
    <ul>{% for c in r.certs %}<li>{{ c }}</li>{% endfor %}</ul>
  </section>
  {% endif %}

  {% if r.languages %}
  <section class="cv__section">
    <h2>Bahasa</h2>
    <ul class="cv__tags">{% for l in r.languages %}<li>{{ l }}</li>{% endfor %}</ul>
  </section>
  {% endif %}

  <footer class="cv__footer">
    <p>Terakhir diperbarui: {{ site.time | date: "%-d %B %Y" }}</p>
  </footer>
</div>
