---
type: Zettel
title: VS Code
description: null
modificationDate: 2024-11-14 22:55
tags: [research]
coverImage: null
---

[Visual Studio Code](https://code.visualstudio.com/) is a lightweight code editor with support for many programming languages through [extensions](https://code.visualstudio.com/docs/editor/extension-gallery)

## Installation

Installation instructionsare provided by the [MacOS set-up guide](./MacOS%20set-up%20guide.md).

---

To install the latest version, use **Homebrew**:

```bash
brew install --cask visual-studio-code
```

### macOS integration

Launch VS Code from the [command line](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line).

After that, you can launch VS Code from your terminal:

- `code .` will open VS Code in the current directory

- `code myfile.txt` will open `myfile.txt` in VS Code

# Enable slashed zero on VS Code for MonoLisa

To choose the modified zero (slashed) in vscode, change the `editor.fontLigatures` setting (JSON settings) as follows:

```bash
"editor.fontLigatures": "'zero'",
```

In VS Code example below, we enable `calt` glyphs (space alterations), disable ligatures (`liga`), enable the alternate zero (`zero`) and the script variant (`ss02`) at **settings.json**: #fonts

```bash
{
  "editor.fontLigatures": "'calt' on, 'liga' off, 'zero' on, 'ss02' on"
}
```

