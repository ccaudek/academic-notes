---
tags:
  - quarto
  - R
  - teaching
---
```markdown
---
title: "Esercitazione: La verosimiglianza in R"
subtitle: "Segmento 2 — Dati continui e combinazione di evidenze"
version: 3.0
author:
  - name: Corrado Caudek
    orcid: 0000-0002-1404-0420
    email: corrado.caudek@unifi.it
    affiliations: Università degli Studi di Firenze
date: today
date-format: long
toc: false
lang: it
execute:
  echo: true
format:
  revealjs:
    theme: [default, ../revealjs.scss]
    title-slide-attributes:
      data-background-color: "#0072bc"
    slide-number: c
    show-slide-number: print
    highlight-style: github
    embed-resources: true
    self-contained-math: true
html-math-method:
  method: mathjax
  url: "https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js"
include-in-header:
  text: |
    <script>
    MathJax = {
      svg: { scale: 0.85, mathmlSpacing: true },
      options: { skipHtmlTags: ['script','noscript','style','textarea','pre'] }
    };
    </script>
bibliography: ../references.bib
csl: ../apa.csl
---
```