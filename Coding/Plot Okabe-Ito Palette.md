---
type: Zettel
title: Plot Okabe-Ito Palette
description: null
modificationDate: 2025-10-13 11:52
tags: [R, coding]
coverImage: null
---

```shell
okabe_ito_palette <- c("#E69F00", "#56B4E9", "#009E73", "#F0E442", "#0072B2", 
                       "#D55E00", "#CC79A7", "#999999", "#000000")

# Creare un barplot orizzontale
barplot(rep(1, 9), col = okabe_ito_palette, 
        names.arg = 1:9, horiz = TRUE,
        main = "Okabe-Ito Color Palette")
```

