---
title: Supplementary Material
short_title: Supplementary Material

# Number supplementary figures as their own "Supplementary Figure" series. Any figure tagged
# `:kind: supplementary` below becomes "Supplementary Figure 1", "2", … independent of the
# main figures. (To instead CONTINUE the main figure numbers, use `figure: {continue: true}`.)
numbering:
  supplementary:
    enabled: true
    template: Supplementary Figure %s
---

```{raw:typst}
#set heading(numbering: none)
```

# Supplementary material

## Supplementary figures

```{figure} figures/figureS1.*
:label: supp-fig-1
:kind: supplementary
:alt: Describe the supplementary figure here.

A supplementary figure. Because it is tagged `:kind: supplementary`, it is numbered in its own
"Supplementary Figure" series. Reference it from anywhere with [](#supp-fig-1).
```

## Supplementary tables

Set a supplementary table's displayed number explicitly with `:enumerator:` (the supplementary
*figure* counter does not apply to tables). Reference it as usual with [](#supp-tbl-1):

```{table} A supplementary table.
:label: supp-tbl-1
:enumerator: S1
:align: center

| Parameter | Value |
|---|---|
| Learning rate | 0.01 |
| Epochs | 100 |
```
