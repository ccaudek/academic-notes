---
type: Zettel
title: Freeze
description: null
modificationDate: 2024-11-27 22:43
tags: [R, quarto]
coverImage: null
---

The `freeze: auto` option in a Quarto notebook's YAML header controls how the code cells in the notebook are executed when you build the document or book. Here's a detailed explanation:

### Purpose of `freeze: auto`

The `freeze` option allows you to control whether the computational results (e.g., tables, plots, outputs) in your Quarto document are recalculated during rendering or preserved from previous runs. Specifically:

- `freeze: auto` means:

    - **Preserve existing outputs**: If the notebook already has outputs (e.g., plots, tables), Quarto will not re-run the code cells. Instead, it will use the outputs saved from the last execution.

    - **Recalculate missing outputs**: If a code cell has no existing output, Quarto will run the cell during the rendering process to generate the missing output.

This behavior strikes a balance between saving time (by not re-running everything) and ensuring completeness (by filling in missing results).

---

### Why Use `freeze: auto`?

1. **Efficiency**:

    - Avoids re-running computationally expensive code if the outputs are already available and up-to-date.

    - Reduces the time required to build large projects, especially for books with multiple computationally intensive notebooks.

2. **Reproducibility**:

    - Ensures outputs are preserved in the document, preventing unnecessary changes or discrepancies during rendering.

3. **Flexibility**:

    - Automatically handles missing outputs, making it easier to integrate new or modified code without manually re-executing the entire notebook.

---

### Other `freeze` Options

1. `freeze: never`

    - Forces Quarto to re-run all code cells every time you render the document.

    - Use this when you want to ensure that all outputs are freshly computed and consistent with the current code.

2. `freeze: true`

    - Completely locks the notebook's execution. Quarto will never re-run any code cells, even if outputs are missing or outdated.

    - Use this for finalized documents where you want to preserve the current state and prevent any unintentional changes.

3. `freeze: false`

    - Opposite of `freeze: true`. Forces all cells to be re-run, like `freeze: never`.

    - This is less commonly used but may be useful if you explicitly want to override a global `freeze: true` setting in a specific notebook.

---

### Example Workflow

- When writing a Quarto book, you might use:

    - `freeze: auto` for most notebooks, allowing Quarto to only re-run necessary cells.

    - `freeze: true` for notebooks containing finalized results or outputs that should not change.

    - `freeze: never` during development when you want to ensure all code is freshly executed.

---

### In Summary

The `freeze: auto` option in your notebook header ensures that Quarto:

1. Re-uses existing outputs where available.

2. Recalculates only the missing ones.

This is especially helpful in books or projects with many notebooks, as it provides a balance between efficiency and ensuring complete outputs.

