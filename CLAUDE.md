# CLAUDE.md

Static study-guide website for two students (Azra & Destan). Plain HTML + inline CSS, no build step, no dependencies. Open `index.html` in a browser to view.

## Structure

```
index.html              Landing page with tabbed navigation (Azra: Wiskunde/Geschiedenis/Chemie/Fysica · Destan: Wiskunde)
math/                   Math study guides (Dutch)
  number_systems.html       Les 1
  logarithms.html           Les 2
  rational_functions.html   Les 3
  derivatives.html          Les 4
  studieplan-wiskunde.html  Exam study plan (5 Biotech, juni 2026)
  analytische_meetkunde.html Destan, Hoofdstuk 9 (incl. corrections to his §9 exercises)
  ruimtemeetkunde.html      Destan, Hoofdstuk 10
chemie/                 Chemistry (Dutch)
  studieplan-chemie.html    Exam study plan (juni 2026) — no content pages yet
fysica/                 Physics (Dutch)
  studieplan-fysica.html    Exam study plan (juni 2026) — no content pages yet
history/                History study guides (Dutch) — interbellum
  index.html, russische_revolutie.html, stalin.html, roaring_twenties.html, mussolini.html
derivatives/            Source photos (WhatsApp .jpeg of handwritten notes) used to build derivatives.html
*.pdf / *.docx          Exam syllabi (leerstofoverzicht) for math, chemistry, physics — source for the study plans
```

## Study plans

Each subject has a `studieplan-*.html` page: an exam-syllabus checklist (which topics already have a study page vs. study-from-notes) plus a session-by-session plan. They're built from the `leerstofoverzicht` PDFs/docx in the repo root. **Missing math content pages** (no study guide yet): H3 Veeltermfuncties, H5 Machten & n-de machtswortelfuncties, H6 Rijen, H7.1 Exponentiële functies; and `derivatives.html` is missing 2.3 product/quotient rule. Chemistry and physics have no content pages yet — only study plans.

## Conventions

- **Each lesson is one self-contained HTML file** — all CSS lives in a `<style>` block in `<head>`. No shared stylesheet, no JS frameworks. Copy the structure of an existing file (e.g. `math/logarithms.html`) when adding a new lesson.
- **Language:** lesson content is in **Dutch** (Belgian curriculum). UI labels and `index.html` are Dutch too. `logarithms.html` is the one older English page.
- **Math card styling** uses a purple theme; the shared CSS classes are: `.card` + a colour (`.purple .blue .green .orange .red .teal .yellow`), `.card-title`, `.formula-box`, `.rule`, `.example` + `.step`/`.answer`, and `table.tekentabel` for sign/variation tables.
- **Lesson navigation:** each math page has a sticky `.lesson-nav` at the top with a previous link, a `🏠 Home` link to `../index.html`, and a next link (or `.nav-disabled` span if it's the last lesson). When adding a lesson, update the previous lesson's "next" link to point to the new page.
- **Registering a lesson on the home page:** add an `<a class="card math-card">` (or `hist-card` / `dest-card`) inside the matching `.cards` panel in `index.html`, with a `Les N` label.

## Adding a lesson from source notes

The workflow used for `derivatives.html`: read the photo notes (e.g. in `derivatives/`), then write a single Dutch HTML file in `math/` reusing the card/formula/tekentabel CSS, wire up `.lesson-nav` both directions, and add a card to `index.html`.

## Git

Work directly on `main` (no feature branches / PRs).
