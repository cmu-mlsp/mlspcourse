---
layout: schedule
permalink: /schedule/
title: Schedule
description: Fall 2026 lecture calendar
nav: true
---

<p class="lede">Lecture dates, quizzes, homeworks and project checkpoints for
{{ site.course_term }}. Meeting times and the room remain TBD until the university
timetable is posted. The order of topics can still shift with class discussion.</p>

<div class="schedule-legend" role="note">
  <span class="schedule-legend__item"><span class="schedule-swatch schedule-swatch--holiday" aria-hidden="true"></span> Holiday / break</span>
  <span class="schedule-legend__item"><span class="schedule-swatch schedule-swatch--noclass" aria-hidden="true"></span> No class</span>
  <span class="schedule-legend__item"><span class="schedule-swatch schedule-swatch--exam" aria-hidden="true"></span> Exam week</span>
</div>

<div class="schedule-table-wrap">
<table class="table table-hover schedule-table">
  <caption class="sr-only">{{ site.course_term }} lecture calendar</caption>
  <thead>
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Lecture</th>
      <th scope="col">Topic</th>
      <th scope="col">Quiz</th>
      <th scope="col">Homework &amp; project</th>
    </tr>
  </thead>
  <tbody>
    {% for item in site.data.lectures_fall2026 %}
    <tr class="schedule-row schedule-row--{{ item.type | default: 'lecture' }}">
      <th scope="row" data-label="Date">{{ item.date | date: "%a, %b %d" }}</th>
      <td data-label="Lecture">{% if item.lecture %}{{ item.lecture }}{% else %}&mdash;{% endif %}</td>
      <td data-label="Topic">
        {% if item.type == 'lecture' %}
          <strong>{{ item.title }}</strong>
        {% else %}
          <span class="schedule-event">{{ item.title }}</span>
        {% endif %}
        {% comment %} TODO: restore slides, lecture files, and homework handouts when they are approved for the public site. Matching Fall 2025 Drive links stay as YAML comments in _data/lectures_fall2026.yml. Do not add those URLs to this table. {% endcomment %}
      </td>
      <td data-label="Quiz">{% if item.quiz %}Quiz {{ item.quiz }}{% else %}&mdash;{% endif %}</td>
      <td data-label="Homework &amp; project">
        {% if item.work and item.work.size > 0 %}
          <ul class="schedule-work">
            {% for task in item.work %}
            <li>{{ task }}</li>
            {% endfor %}
          </ul>
        {% else %}
          &mdash;
        {% endif %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>
</div>

<p class="schedule-footnote">Quizzes follow the numbering on the course calendar (there is no Quiz 13).
HW 4 is released on Nov 17; its due date is not on the source calendar. Exam week is not listed.</p>

<section class="section" id="coursework">
  <div class="section__head">
    <h2>Coursework dates</h2>
    <p class="section__note">Weights are on the <a href="{{ site.baseurl }}/syllabus/">syllabus</a>. Handouts stay on Canvas, not this page.</p>
  </div>

  <ul class="info-grid">
    <li class="info-card">
      <span class="info-card__label">Homeworks</span>
      <span class="info-card__value">Four assignments</span>
      <span class="info-card__hint">HW 1: Sep 1–17. HW 2: Sep 22–Oct 8. HW 3: Oct 20–Nov 17. HW 4 released Nov 17 (due date TBD).</span>
    </li>
    <li class="info-card">
      <span class="info-card__label">Quizzes</span>
      <span class="info-card__value">Weekly (see table)</span>
      <span class="info-card__hint">Short multiple-choice quizzes on the previous week's material. Numbered 1–12 and 14.</span>
    </li>
    <li class="info-card">
      <span class="info-card__label">Group project</span>
      <span class="info-card__value">Document, teams, proposal, checkpoint, report</span>
      <span class="info-card__hint">Document out Sep 17. Teams Oct 6. Proposal Oct 29. Mid-term checkpoint Nov 17. Final report Dec 7. Presentation date TBD.</span>
    </li>
  </ul>
</section>

<section class="section" id="topics">
  <div class="section__head">
    <h2>What the course covers</h2>
    <p class="section__note">Grouped by theme &mdash; the table above is the dated order.</p>
  </div>

  <ul class="topic-modules">
    {% for module in site.data.topics %}
    <li class="topic-module">
      <p class="topic-module__index">Module {{ forloop.index }}</p>
      <h3 class="topic-module__title">{{ module.module }}</h3>
      <ul class="topic-list">
        {% for topic in module.topics %}
        <li>{{ topic }}</li>
        {% endfor %}
      </ul>
    </li>
    {% endfor %}
  </ul>
</section>
