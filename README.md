# Debugging Guide

Website link: https://ds100.org/debugging-guide/

## Quarto Set-Up

Begin by [installing Quarto](https://quarto.org/docs/get-started/).

Texts can be authored in Quarto using VSCode, JupyterLab, or classic Jupyter Notebook. We suggest using [VSCode](https://quarto.org/docs/get-started/hello/vscode.html)

## Repo Organization
This website uses Quarto to render pages. The main index can be found in `_quarto.yml`, and subpages are organized under the `chapters` section. Each subpage has it's own folder and `.md` (markdown) file. Note that unlike the [Course Notes repo](https://github.com/DS-100/course-notes), the debugging guide rarely runs any code, so we rely on `.md` files rather than `.qmd`, saving us the trouble of converting from `.qmd` to `.ipynb` for editing, then back to `.qmd` to render the website. Instead we can make edits directly to the `.md` file. 

## Creating a new section
To start a new document, create an empty folder `topic_name` and create an empty markdown file `topic_name.md`. Start each document like so: 

```
---
title: INSERT_TOPIC_TITLE
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
```

Now, the notebook is ready for writing content.  In VSCode, you can activate a live preview of markdown files by clicking the button on the upper right-hand corner.

![](md_preview.png)

Note that clicking on the quarto `Preview` button does not generate a *live* preview but rather a static one. 

## Document Formatting

A pdf view of how this notebook renders in Quarto can be found [here](https://drive.google.com/file/d/17ga5wvfcmvAzQ1rbnCP4kEf5bckST3--/view?usp=sharing).

#### Formatting Images

To give you the most control when inserting images, we use html with the following format to center images/figs and control their size: 

```<center><img src = "IMAGE_NAME" width = "IMAGE_WIDTH_IN_PIXELS"></img></a></center>```

## Generating Output + Rendering Website
After making edits to the `.md` files, ensure that the right documents are un-commented under `_quarto.yml`'s `chapter` section. Then, run `quarto render` to render the entire website. Push your changes to Github, and you should see the changes reflected in the [website](https://ds100.org/debugging-guide/) after a few minutes. 

* Publish notes to GitHub pages:
  * `quarto render` everything
  * `git add`, `git commit`, `git push`
  * Can view website compilation on GitHub (look for yellow-to-green button next to commit number)

## Other Quarto Resources

[Quick Start Guide](https://quarto.org/docs/get-started/)

[Comprehensive Guide](https://quarto.org/docs/guide/)

[Markdown in Quarto](https://quarto.org/docs/authoring/markdown-basics.html)
