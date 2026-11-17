# CLAUDE.md — a module of the Interactive Pathology Teaching Platform

This repository is one module (a single `index.html`): **Hematology** (module key `hematology`, storage prefix `hm_`, build `1.0`). Built
2026-11-17 from the user's syllabus "Fundamentals of Pathology" Ch. 5 Red Blood Cell Disorders and Ch. 6 White Blood Cell Disorders (pp. 41–64)
**as it is — NOT condensed** (like Inflammation (New), Neoplasia (New) and Granulomatous), with the app code of
`third-year-med/Granulomatous-and-parasitic-diseases`. Served at `https://third-year-med.github.io/third-year-med-hematology/`.

The platform's decisions, the checklist for modules, the deployment steps, the testing workflow and the lessons learned are in the platform
repository: `third-year-med/Interactive-pathology-platform` → `CLAUDE.md` and `docs/HANDBOOK.md` (§4.2.6; rebuilds: `docs/REBUILD.md`).

- The course data in `index.html` is encrypted with this module's OWN content key, which lives only in the user's Code.gs
  (`CONTENT_KEYS.hematology`; env `HM_CONTENT_KEY` in a session). Never commit a key or an unencrypted copy of the course.
- The `<script id="platform-nav">` block is maintained in the platform repo (`modules/platform-nav.js`) and written here with
  `tools/module-release.js refresh` — do not edit it by hand. Platform features: `bash modules/patches/apply.sh --check index.html` must say ✅.
- Stable IDs: topics t01–t16 in the syllabus order (anemia; microcytic; macrocytic; normocytic; extravascular hemolysis; intravascular hemolysis;
  underproduction; leukopenia/leukocytosis; acute leukemia; chronic leukemia; myeloproliferative disorders; lymphadenopathy; lymphoma (NHL);
  Hodgkin lymphoma; plasma cell disorders; Langerhans cell histiocytosis) + **t17 Practical** (s1701–s1703); sections sNNMM; own questions
  q001–q150; the course MCQ book's in-syllabus questions `qb<NN>` (NN = book number); cases c01–c12; syllabus figures `fig5_N` / `fig6_N`
  (credit "Course syllabus … p. N"), MCQ-book pictures `mcq_q<N>`, Commons atlas pictures `hm-img-NNN`. The practical topic is **t17**.
- Delivered to the user directly, never committed: `hematology-viva-bank.json` (91 questions `viva_hm_tNN_NN`, 5 marks each, ≥ 5 per topic,
  34 picture questions) — imported in ✏️ Edit master draft → 🎓 Viva → ⬆ Import viva bank.
  Teachers can present it in class with ▶ Present (platform patch `viva-present`, 2026-11-17).
- Practical material (pictures, cases, Spotter, OSPE, 🔒 bank) follows HANDBOOK §4.4 when the user sends it.
- Test changes on the real page with the platform repo's e2e tests "Hematology module (hematology)" and "🎓 Viva Examination (hematology)"
  (`HM_CONTENT_KEY` in the environment) and `node test/module-smoke/smoke.js` before pushing.
