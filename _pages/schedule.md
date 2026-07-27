---
layout: schedule
permalink: /schedule/
title: Schedule
description: Fall 2026 calendar to be announced
nav: true
---

<div class="notice notice--tbd">
  <span class="notice__bar" aria-hidden="true"></span>
  <span class="chip chip--tbd">TBA</span>
  <h3>The {{ site.course_term }} schedule has not been released yet</h3>
  <p>Lecture dates, slides, recordings and homework releases will be published here once the university timetable is
    confirmed. The outline below shows the material we expect to cover; the order and the exact set of topics are
    subject to change based on student interests and course discussions.</p>
  <p>Lecture slides from previous editions are not linked while the calendar is being rebuilt. Registered students
    will find everything on Canvas and Piazza once the term begins.</p>
</div>

<section class="section" id="topics">
  <div class="section__head">
    <h2>What the course covers</h2>
    <p class="section__note">Grouped by theme &mdash; not the lecture order.</p>
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

<section class="section" id="coursework">
  <div class="section__head">
    <h2>Coursework</h2>
    <p class="section__note">Weights are described in the <a href="{{ site.baseurl }}/syllabus/">syllabus</a>.</p>
  </div>

  <ul class="info-grid">
    <li class="info-card">
      <span class="info-card__label">Homeworks</span>
      <span class="info-card__value">Four assignments <span class="chip chip--tbd">Dates TBD</span></span>
      <span class="info-card__hint">Released across the semester as mini-projects. Handouts are posted on Canvas.</span>
    </li>
    <li class="info-card">
      <span class="info-card__label">Quizzes</span>
      <span class="info-card__value">Weekly <span class="chip chip--tbd">Dates TBD</span></span>
      <span class="info-card__hint">Short multiple-choice quizzes on the previous week's material.</span>
    </li>
    <li class="info-card">
      <span class="info-card__label">Group project</span>
      <span class="info-card__value">Team project <span class="chip chip--tbd">Dates TBD</span></span>
      <span class="info-card__hint">Proposal, midway report and final presentation, scheduled once the term calendar is set.</span>
    </li>
  </ul>
</section>

{% comment %}
===============================================================================
 TODO: RESTORE FOR FALL 2026 — dated lecture table (slides + homework links)
===============================================================================

 Everything below is intentionally disabled while the calendar is TBA. Nothing
 in this block reaches the built page.

 To bring the schedule back:
   1. Copy _data/lectures_fall2025.yml to _data/lectures_fall2026.yml and update
      the dates, titles, `lectures:` (slide/recording links) and `Homeworks:`
      entries. The Fall 2025 file is kept intact so links can be reused.
   2. Delete the `{% raw %}{% comment %}{% endraw %}` / `{% raw %}{% endcomment %}{% endraw %}`
      wrapper around the markup below.
   3. Optionally drop the "What the course covers" and "Coursework" sections
      above, or keep them as an overview alongside the table.

-------------------------------------------------------------------------------

<div class="schedule-table-wrap">
<table class="table table-hover">
  <colgroup>
    <col style="width:12%">
    <col style="width:48%">
    <col style="width:18%">
    <col style="width:22%">
  </colgroup>
  <thead class="thead-light">
    <tr>
      <th scope="col">Date</th>
      <th scope="col">Topics</th>
      <th scope="col">Lectures</th>
      <th scope="col">Homeworks</th>
    </tr>
  </thead>
  <tbody>
    {% assign current_module = 0 %}
    {% assign skip_classes = 0 %}
    {% assign prev_date = 0 %}

    {% for item in site.data.lectures_fall2026 %}
      {% if item.date %}
        {% assign lecture = item %}
        {% assign event_type = "upcoming" %}
        {% assign today_date = "now" | date: "%s" | divided_by: 86400 %}
        {% assign lecture_date = lecture.date | date: "%s" | divided_by: 86400 %}
        {% if today_date > lecture_date %}
          {% assign event_type = "past" %}
        {% elsif today_date <= lecture_date and today_date > prev_date %}
          {% assign event_type = "warning" %}
        {% endif %}
        {% assign prev_date = lecture_date %}

        <tr class="{{ event_type }}">
          <th scope="row">{{ lecture.date }}</th>
          {% if lecture.title contains 'lectures' %}
            {% assign skip_classes = skip_classes | plus: 1 %}
            <td colspan="4">{{ lecture.title }}</td>
          {% else %}
            <td>
              {{ lecture.title }}
              <ul>
                {% for topic in lecture.topics %}
                  <li style="font-size:12px;">{{ topic }}</li>
                {% endfor %}
              </ul>
            </td>
            <td>{{ lecture.lectures }}</td>
            <td>{{ lecture.Homeworks }}</td>
          {% endif %}
        </tr>
      {% else %}
        {% assign current_module = current_module | plus: 1 %}
        {% assign module = item %}
        <tr class="info">
          <td colspan="5" align="center"><strong>{{ module.title }}</strong></td>
        </tr>
      {% endif %}
    {% endfor %}
  </tbody>
</table>
</div>

===============================================================================
{% endcomment %}
