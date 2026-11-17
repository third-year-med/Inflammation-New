# CLAUDE.md — a module of the Interactive Pathology Teaching Platform

This repository is one module (a single `index.html`): **Inflammation (New)** (module key `inflnew`, storage prefix `in_`).
It was built on 2026-10-29 from the user's syllabus file "Chapter (Inflammation)" — the syllabus text as it is (NOT condensed,
the user's explicit request for this module), with the app code of `third-year-med/inflammation-healing`. It reuses only the
questions, pictures, links and terms of the earlier inflammation modules that the syllabus covers (edited to its wording),
plus new questions, cases and glossary terms written from the syllabus. Topic t13 = Practical Pathology (the 19 practical
cases, build new-1.1). The **Healing** syllabus ("Chapter 4: Tissue Repair", 2026-10-30, also NOT condensed) is topics **t14–t19**
(build new-1.2), placed before t13 so the practical topic stays last: display numbers differ from IDs from t14 on (t14 = Topic 13,
t13 = Topic 19) — refer to topics by name in course text. Keep all topic, section, question and case IDs.

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
- **Practical rebuild (2026-11-14, builds new-1.4 / new-1.5):** t13 = 12 practical cases (old Cases 12–18 removed; the keloid
  case is Case 12), 97 departmental pictures (`in-prac2-01…97`, picture-import file), questions p001–p031. Spotter: 138
  questions, 38 hardest in 🧪 Practice (`inflnew-spotter-questions-4.json`); 🔒 practical bank (129, `aqb_inp_*`, `pic:` refs);
  OSPE 23 stations (`in-os2-*`). Students do not see the Learn practical topic (patch `prac-clean`). Served at
  `https://third-year-med.github.io/Inflammation-New/` since GitHub renamed the repository. Standard: platform HANDBOOK §4.4.
- **Open (2026-11-16, platform rule HANDBOOK §4.4):** every practical picture also into its Learn topic, then ONE picture per finding
  (repeats out with a `neo-picture-remove` file — 🗑 Remove pictures in Teacher Portal → 💾 Backup). Done for Granulomatous; here it
  waits for the user's picture files (topic + practical) or a master backup and the content key.
- Test changes on the real page with the platform repo's e2e tests (`IN_CONTENT_KEY` in the environment) before pushing.
