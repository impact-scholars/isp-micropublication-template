---
title: A feature-complete reference micropublication for Impact Scholars
# subtitle: Everything an author needs, in one place

# Abstract — required. Prefer plain language with NO inline math: the abstract appears in
# listings before any symbols are defined. ~500 words max.
abstract: |
    This template is a working micropublication that exercises the features an Impact Scholars
    author is likely to need: a multi-panel figure, cross-referenced tables and equations,
    citations, a plain-language summary, an abbreviations list, and a wired-in supplement.
    Replace the prose, figures, and metadata with your own and keep the structure — every
    directive below is here to be copied.

# Document parts (rendered by the template, not as body headings):
parts:
  # Plain-language summary — shown next to the abstract on the cover page. Write for a general
  # audience. If the abstract + summary overflow page 1, set options.full_width_body: false.
  summary: |
    In one short paragraph, and without jargon: what question did you ask, what did you find,
    and why should someone outside your field care?
  # Optional note injected into the Zenodo deposit description (not shown in the paper):
  # zenodo_extra_description: |
  #   Ada Lovelace and Alan Turing contributed equally and share first authorship.

# Acknowledgments and data availability go in frontmatter, NOT as body headings.
acknowledgments: |
    We thank the Impact Scholars Program and our mentors. List people, institutions, and any
    AI-assistance disclosure here.
data_availability: |
    Published via [Impact Scholars](https://github.com/impact-scholars/isp-micropublication-template); original [development repository](https://github.com/your-username/your-repo).

# NOTE: abbreviations and the PDF template options (render_abbreviations, breakable_figures,
# full_width_body) live in myst.yml. In a multi-article export (this template merges a
# supplement) they must be set at the project / exports level — page frontmatter here would
# silently no-op.
---

This reference paper is its own documentation: each paragraph and directive below demonstrates
something you can reuse. Delete this guidance and write your study. The usual micropublication
shape works well — a brief introduction, methods, results, and a short discussion.

## Introduction

Cite a work textually with `@key` (e.g. @lovelace1843) or parenthetically with brackets
(e.g. [@turing1936]). Group several keys with semicolons
[@lovelace1843; @turing1936; @hopper1952]. Abbreviations defined in the frontmatter, such as
ISP, are linked automatically the first time they appear.

(sec-methods)=
## Methods

Cross-reference figures, tables, equations, and sections with the **label-only** form
`[](#label)` — the renderer fills in "Figure 1", "Table 1", etc., and it stays correct in both
the web and PDF builds. Do not hardcode numbers or add display text like `[Figure 1](#...)`.

Numbered, cross-referenceable equations use a `{math}` block with a `:label:`:

```{math}
:label: eq-snr
\mathrm{SNR} = \frac{\mu_\text{signal}}{\sigma_\text{noise}}
```

Then refer to it as [](#eq-snr). Inline math uses single dollars, e.g. $\mathrm{SNR} > 5$. If
you need angle brackets in math, prefer the Unicode characters ⟨ ⟩ over `\langle`/`\rangle`,
which raise a Typst deprecation warning.

## Results

A figure can hold one image or several. There are two ways to build a multi-panel figure, and
the choice changes how you cross-reference the panels — both are shown below.

### Let MyST arrange the panels

Put each panel in its own `![](…)` inside a single `{figure}`. MyST numbers them as one figure
and adds the sub-labels — **A**, **B**, … — automatically, laying the panels side by side in
the PDF. Each panel also gets its own cross-reference: the whole figure is [](#fig-panels), and
the individual panels are [](#fig-panels-a) and [](#fig-panels-b) — you never type the letters
yourself, so they stay correct if you reorder the panels.

:::{figure}
:label: fig-panels
:alt: Effective timescales summarized across brain divisions, and the coupling between fast and slow timescales.

![Effective timescale by brain division.](figures/figure1a.png)

![Coupling between fast and slow timescales.](figures/figure1b.png)

Panels composed by MyST. Write the shared caption here; the **A** and **B** labels are added
for you. The bracket text on each image is its alt text (and a per-panel caption on the web).
:::

### Or supply one composite image

If you arranged the panels yourself — in your plotting code or a vector editor — drop in the
single image and describe each panel in the caption. There are no sub-labels to reference here,
so append the panel letter as plain text right after the reference, e.g. [](#fig-composite)a. A
bare backslash on its own line forces a line break between panel descriptions.

```{figure} figures/figure2.png
:label: fig-composite
:width: 70%
:alt: Describe the figure here for screen readers and accessibility.

**(a)** Describe the first panel. Write one paragraph per panel.
\
**(b)** Reference figures, tables, and equations by label so numbering survives reordering.
\
**(c)** Tip: put a vector pair (`figure2.svg` + `figure2.pdf`) in `figures/` and reference
`figures/figure2.*` — the build picks SVG for the web and PDF for print. A single `.png` works
too.
```

Tables use a `{table}` directive with the caption as the directive argument and a `:label:`
for cross-references ([](#tbl-results)). Fold any footnotes into the caption rather than
placing them below the table:

```{table} Summary of results. Values are mean ± SD; p from a two-sided t-test.
:label: tbl-results
:align: center

| Condition | N | Score | p |
|---|---:|---:|---:|
| Control | 32 | 0.41 ± 0.08 | — |
| Treatment | 30 | 0.63 ± 0.09 | < 0.001 |
```

:::{note}
Use a note admonition for asides, caveats, or table footnotes — it renders as a callout box.
:::

## Discussion

Say what the result means and what it does not. Keep it short; this is a micropublication.

Additional analyses appear in the supplement ([](#supp-fig-1) and [](#supp-tbl-1)) — note that
cross-references work across files in the merged PDF.

<!--
No "## References" section: the template renders the bibliography automatically from the
`bibliography:` file declared in myst.yml.

Prefer a SEPARATE supplement (supplementary.md, already wired in myst.yml). To inline it
instead, delete supplementary.md and add, at the end of this file:

    ```{raw:typst}
    #set heading(numbering: none)
    ```

    # Supplementary material

    ...your supplementary figures/tables...

…and remove supplementary.md from the toc and the exports block in myst.yml.
-->
