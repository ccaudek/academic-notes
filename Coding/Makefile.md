---
type: Zettel
title: Makefile
description: null
modificationDate: 2024-11-14 22:39
tags: [coding]
coverImage: null
---

## Targets

A Makefile is a collection of build **targets**, each of which is defined using syntax that looks something like this:

```bash
targets: prerequisites
    command
    command
    command
```

The top level command provides the name of the target. In the simplest case, a target is a specific file that `make` needs to build, and the name of the target is the path to that file.

Optionally, a target can have a set of **prerequisites** associated with that target. Prerequisites provide a method for specifying the dependencies for a build target. If the files listed as prerequisites have changed more recently than the output target, the build target is deemed to be “out of date”, and the **commands** listed beneath it will be executed in order to rebuild that target.

```bash
output/fig_1.png: data/input_1.csv scripts/gen_hist.R
	Rscript scripts/gen_hist.R -i data/input_1.csv -o output/fig_1.png
```

You must use tabs for indentations in your Makefile, or it won’t work.

Targets and their prerequisites provide a mechanism by which a Makefile can be used to track the dependencies among the various files in your project. It’s worth noting a few special cases:

- If a target has no prerequisites it is always deemed out of date, so the commands will be executed every time.

- If the name of the target doesn’t correspond to an actual output file, it’s considered to be a “phony” target and is always considered out of date, and hence the commands will always be executed.

- A target can be explicitly labelled as “phony” even if the target name happens to be the same as a file in the project using the `.PHONY` keyword.

## Makefile

Traditionally a Makefile is simply named `Makefile` or `makefile`. It doesn’t have to be, but if you call it something else you need to explicitly tell `make` where to find the file using the `-f` flag. A command like `make -f my_make_file`, for example, specifies that the Makefile is called `my_make_file`.

If the Makefile contains, let say, three targets, to build each of these I could type this sequence of commands at the terminal:

```text
make bin/collatz
make bin/species
make bin/swap
```

To accommodate the need of the dead things like myself, `make` makes it possible to group multiple targets together. You can put this statement at the top of the Makefile:

```text
# the "all" target is a set of other targets 
all: dir bin/collatz bin/species bin/sw
```

Then executing all targets can be achieved with

```text
make all
```

In fact, even this can be shortened, because “all” happens to be the first target listed in the Makefile. If you don’t specify a target to build, `make` will use the first target in the file. It is conventional, then, to call the first target “all”, and have that target consist of a list of all the *other* targets needed to build the whole project. Consequently, I can do this:

```text
make
```

## Clean

If you want to burn it all down and revert to the initial (unbuilt) state of the project? `make` doesn’t provide that functionality automatically, but it is traditional for writers of Makefiles to include a target called `clean` that includes commands that will perform this clean up job for you.

```text
clean:
	rm -f $(OUTPUT_DIR)/report.pdf
	rm -f $(OUTPUT_DIR)/figure_*.png
```

Because we have this target in the Makefile, all we have to do is type `make clean`:

```text
make clean
```

