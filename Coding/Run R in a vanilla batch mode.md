---
type: Zettel
title: Run R in a vanilla batch mode
description: null
modificationDate: 2024-11-27 19:22
tags: [R, coding]
coverImage: null
---

For any kind of analysis that you want to be reproducible, you'll need to stop using R as a live interpreter, and instead write all code to be run in a vanilla batch mode.

Running code "live" often leads to you having objects floating around in your live environment that aren't actually in your code. This leads to bugs and a lack of reproducibility.

Instead you should have a structure where you always batch call a "main.R" file which then, conditionally, sources sub files. Something like

```r
# start by loading in raw data and getting it clean for analysis 
do_clean_data <- TRUE
# now run the main statistical model
do_estimate <- TRUE
# now plot the analysis
do_plot <- TRUE

if (do_clean_data) source("clean_data.R", echo = TRUE)

if (do_estimate) source("estimate.R", echo = TRUE)

if (do_plot) source("plot.R", echo = TRUE)
```

The "clean_data.R" file cleans the data, and saves a copy, which is then loaded FROM DISK by "estimate.R", which saves the estimates from a model which may take a long time to run to be loaded FROM DISK by "plot.R" which then plots data/estimates.

The point here is that you can run each time consuming piece once, save it's results to be loaded by the next piece, so you don't re run stuff all the time. Coding like this makes it much easier for collaborators to understand, less likely for you to send code around with fatal bugs (everything sounds run from scratch from top to bottom)


