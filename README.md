# 11-755 - Machine Learning for Signal Processing

The course webpage for CMU course 11-755, Machine Learning for Signal Processing, Fall 2026.

https://cmu-mlsp.github.io/mlspcourse

## Editing the site

Jekyll site published by GitHub Pages from the default branch. Term-wide values
(course number, term, year) live in `_config.yml` and are used by the layouts,
the header and the footer, so bumping the term is a one-place change.

Pages: `index.html` (landing), `_pages/schedule.md`, `_pages/syllabus.md`.
Styles are in `_sass/`; design tokens (colours, fonts, shadows, radii, for both
light and dark themes) are all in `_sass/_tokens.scss`.

## Restoring the schedule and staff

While the Fall 2026 calendar is unknown, dated content is disabled rather than
deleted. Search the repository for `TODO: restore` to find every disabled block;
each one carries a note about what to put back. The main ones:

- `_pages/schedule.md` — the dated lecture table with slide and homework links is
  wrapped in a `{% comment %}` block near the bottom of the file, together with
  step-by-step instructions. The date-free topic outline that is shown instead
  comes from `_data/topics.yml`.
- `_data/lectures_fall2025.yml` — last term's dates, slide links and homework
  links, kept intact. Copy it to `_data/lectures_fall2026.yml` and edit.
- `_data/people.yml` — teaching assistants beyond the first are commented out;
  uncomment or replace as staff are confirmed.
- `index.html` — meeting time, room, Zoom, Piazza, Canvas, office hours and
  announcements each have a commented-out previous version next to the current
  `TBD` card.
- `_includes/social.html` — the lecture recordings channel link.
- `_includes/header.html` — the `projects` nav link.

Anything inside `{% comment %}` never reaches the built HTML, so disabled links
are not merely hidden with CSS.
