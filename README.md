# Impact Scholars Micropublication — author template

This repository is a **feature-complete reference micropublication**. The manuscript
(`index.md`) is written to double as documentation: every directive in it demonstrates a
feature you can copy. Replace the content with your own and keep the structure.

Published via the [Impact Scholars Program](https://neuromatch.io/impact-scholars-program/),
an initiative by [Neuromatch](https://neuromatch.io).

## Layout

```
myst.yml           Project metadata, authors, table of contents, PDF export config
index.md           The manuscript (frontmatter + body)
supplementary.md   Optional supplement (delete if unused — see myst.yml)
bib.bib            References (one file; declare it in myst.yml)
figures/           figure1a/1b.png (multi-panel Fig 1), figure2.png (composite Fig 2), figureS1.png (supplement)
thumbnails/        thumbnail.png — gallery image (keep this path/name)
environment.yml    Build environment (mystmd + typst)
```

## Build locally

```bash
myst start          # live web preview at http://localhost:3000
myst build --pdf    # PDF written to _build/exports/
```

## Author checklist

- [ ] `myst.yml`: set `id: isp-<repo-name>`, `title`, `keywords`, and `github` (the
      `impact-scholars/<repo>` URL, not your personal fork).
- [ ] Authors: full names (keep diacritics), `orcid`, and CRediT `roles`. Mark corresponding
      authors with `email:` + `corresponding: true`; co-first authors with
      `equal_contributor: true`.
- [ ] `index.md`: write the `abstract` and the plain-language `summary`; fill in
      `acknowledgments` and `data_availability`.
- [ ] Figures live in `figures/` and are cross-referenced with `[](#label)` — never hardcode
      "Figure 1" or add display text.
- [ ] Supplement: if you have none, delete `supplementary.md`, remove it from `toc:`, and
      delete the `exports:` block in `myst.yml` (the inherited single-article export takes over).
- [ ] Bibliography: keep a single `bib.bib`; delete any unused `.bib` files.
- [ ] Keep the repo tidy: no committed build outputs, unused figures, or stray `.pdf`/`.docx`
      deliverables. Put analysis code in a subfolder (e.g. `code/`).

You get for free from the shared config: a PDF download button, a CC-BY licence, "Impact
Scholars Program" funding, and the ISP theme. The editor fills in `doi:` and `date:` at
publication.
