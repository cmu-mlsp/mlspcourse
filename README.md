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

## Schedule and staff

The public `/schedule/` page is driven by `_data/lectures_fall2026.yml` and
shows dates, lecture numbers, titles, quizzes, and combined homework /
project checkpoints. Set an optional `slides:` URL on a lecture row to publish
a Slides chip; other slide and homework *file* links stay as YAML comments.

Search the repository for `TODO: restore` to find disabled blocks (room, Piazza,
Canvas, office hours, recordings, project nav). Staff for Fall 2026: Bhiksha Raj,
Siddhartha Vanjari, Gabrial Zencha Ashungafac.
