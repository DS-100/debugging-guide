---
title: Jupyter 101
format:
  html:
    toc: true
    toc-depth: 5
    toc-location: right
    code-fold: false
    theme:
      - cosmo
      - cerulean
    callout-icon: false
jupyter:
  jupytext:
    text_representation:
      extension: .qmd
      format_name: quarto
      format_version: '1.0'
      jupytext_version: 1.16.1
  kernelspec:
    display_name: Python 3 (ipykernel)
    language: python
    name: python3
---

::: {.callout-note collapse="false"}
If you're using a MacBook, replace `ctrl` with `cmd`.
:::

## Shortcuts for Cells

For the following commands, make sure you're in command mode. You can enter this mode by pressing `esc`.

- `a`: create a cell above
- `b`: create a cell below
- `dd`: delete current cell
- `m`: convert a cell to markdown (text cell)
- `y`: convert a cell to code 

## Running Cells

For individual cells, 

- `ctrl` + `return`: run the current cell
- `shift` + `return`: run the current cell and move to the next cell

To run all cells in a notebook: 

- In the menu bar on the left, click `Run`. From here, you have several options. The ones we use most commonly are:

    - `Run All Above Selected Cell`: this runs every cell above the selected cell 
    - `Run Selected Cell and All Below`: this runs the selected cell and all cells below
    - `Run All`: this runs every cell in the notebook from top-to-bottom
 
<center><img src = "run_all.gif" width = "500"></img></a></center>

## Saving your notebook
Jupyter autosaves your work, but there can be a delay. As such, it's a good idea to save your work as often as you remember and especially before submitting assignments. To do so, press `ctrl` + `s`. 

## Restarting Kernel
In the menu bar on the left, click `Kernel`. From here, you have several options. The ones we use most commonly are: 

- `Restart Kernel...`
- `Restart Kernel and Run up to Selected Cell`
- `Restart Kernel and Run All Cells` 

<center><img src = "kernel.gif" width = "500"></img></a></center>
