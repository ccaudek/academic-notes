---
type: Zettel
title: How to use R in Colab
description: null
modificationDate: 2024-11-08 12:02
tags: [teaching]
coverImage: null
---

Start `rmagic` by executing the following command:

```python
%load_ext rpy2.ipython
```

In subsequent cells use `%%R` to run R code:

```python
%%R
x <- seq(0, 2*pi, length.out=50)
x
```

# Caltech course on Bayes inference

[BE/Bi 103 b](https://bebi103b.github.io/index.html): Statistical Inference in the Biological Sciences

