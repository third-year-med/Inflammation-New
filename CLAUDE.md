# CLAUDE.md — a module of the Interactive Pathology Teaching Platform

This repository is one module (a single `index.html`): **Inflammation (New)** (module key `inflnew`, storage prefix `in_`).
It was built on 2026-10-29 from the user's syllabus file "Chapter (Inflammation)" — the syllabus text as it is (NOT condensed,
the user's explicit request for this module), with the app code of `third-year-med/inflammation-healing`. It reuses only the
questions, pictures, links and terms of the earlier inflammation modules that the syllabus covers (edited to its wording),
plus new questions, cases and glossary terms written from the syllabus. The user will add a **Healing** syllabus later:
it becomes new topics after t12 (keep t01–t12 and their section IDs).

The platform's decisions, the checklist for modules, the deployment steps, the testing workflow and the lessons learned are
in the platform repository: `third-year-med/Interactive-pathology-platform` → `CLAUDE.md` and `docs/HANDBOOK.md`
(rebuilds: `docs/REBUILD.md`).

- The course data in `index.html` is encrypted with this module's OWN content key, which lives only in the user's Code.gs
  (`CONTENT_KEYS.inflnew`). Never commit a key or an unencrypted copy of the course.
- Figures 1–6 are the user's own syllabus figures (embedded in the encrypted course, credit "Figure from the course
  syllabus"). Robbins pictures are never committed — they come as a picture-import file the user imports.
- The `<script id="platform-nav">` block is maintained in the platform repo (`modules/platform-nav.js`) and written here
  with `tools/module-release.js refresh` — do not edit it by hand.
- A new build goes through the preview / compatibility check / go-live procedure (`docs/REBUILD.md`) and must keep the
  IDs of continuing topics, sections, questions, cases and images.
- Test changes on the real page with the platform repo's e2e tests (`IN_CONTENT_KEY` in the environment) before pushing.
