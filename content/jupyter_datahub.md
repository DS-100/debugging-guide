---
title: Jupyter / Datahub
---

## My kernel died, restarted, or is very slow

Jupyterhub connects you to an external container to run your code. That connection could be slow/severed because:

1. you haven't made any changes to the notebook for a while
2. a cell took too much time to run
3. a cell took up too many resources to compute

When you see a message like this:

```{image} images/kernel_die.png
:width: 500
:alt: Screenshot of dead kernel messaging
```

1. Either press the "Ok" button or reload the page
2. [Restart your kernel](#restarting-kernel)
3. [Rerun your cells](#running-cells)

Note that you may lose some recent work if your kernel restarted when you were in the middle of editing a cell. As such, we recommend [saving your work](#saving-your-notebook) as often as possible.

If this does not fix the issue, it could be a problem with your code, usually the last cell that executed before your kernel crashed. Double check your logic, and feel free to make a private post on Ed if you're stuck!

## I can’t edit a cell

We set some cells to read-only mode prevent accidental modification. That said, do not modify the given cells unless instructed to do so. If instructed, to make the cell writeable,

1. Click the cell
2. Click setting on the top right corner
3. Under "Common Tools", you can toggle between "Editable" (can edit the cell) and "Read-Only" (cannot edit the cell)

```{image} images/toggle_edit.gif
:width: 500
:alt: Gif showing how to toggle between 'Editable' and 'Read-Only' for a cell
```

## My text cell looks like code

If you double-click on a text (markdown) cell, it'll appear in its raw format. To fix this, simply run the cell. If this doesn't fix the problem, check out the commonly asked question below.

(cell-type-change)=
## My text cell changed to a code cell / My code cell changed to a text cell

Sometimes, a text (markdown) cell was changed to a code cell, or a code cell can't be run because it's been changed to a text (markdown) or raw cell. To fix this, toggle the desired cell type in the top bar.

```{image} images/toggle_cell_type.gif
:width: 700
:alt: Gif showing how to toggle the cell type from code to text and back again.
```

## Why does running a particular cell cause my kernel to die?

If one particular cell seems to cause your kernel to die, this is likely because the computer is trying to use more memory than it has available. For instance: your code is trying to create a gigantic array. To prevent the entire server from crashing, the kernel will “die”. This is an indication that there is a mistake in your code that you need to fix.

## I accidentally deleted something in a cell that was provided to me – how do I get it back?

Suppose you’re working on Lab 5. One solution is to go directly to DataHub and rename your lab05 folder to something else, like lab05-old. Then, click the Lab 5 link on the course website again, and it’ll bring you to a brand-new version of Lab 5. You can then copy your work from your old Lab 5 to this new one, which should have the original version of the assignment.

Alternatively, you can access this [public repo](https://github.com/DS-100/sp26-student) and navigate to a blank copy of the assignment you were working on. In the case of Lab 5 for example, the notebook would be located at `lab/lab05/lab05.ipynb`. You can then check and copy over the contents of the deleted cell into a new cell in your existing notebook.

## "Click <u>here</u> to download zip file" is not working

When this happens, you can download the zip file through the menu on the left.

```{image} images/zip_left_menu.png
:width: 400
:alt: Left menu showing files with the zip file highlighted by a red box.
```

Right click on the generated zip file and click "Download".

```{image} images/zip_download.png
:width: 500
:alt: After right/force clicking on the zip file, click 'Download' which is highlighted in this screenshot with a red box.
```

## Autograder could not locate my PDF

Sometimes when running the `grader.export(run_tests=True)` cell at the end of the notebook, you run into an error where the autograder could not locate the PDF:

```{image} images/pdf_not_located.png
:width: 700
:alt: Screenshot showing 'UserWarning: Could not locate a PDF to include'
```

To fix this, make sure you have not accidentally converted any cells to `raw` type. All cells should either be `markdown` or `code` cells. You can easily convert cells by following [these instructions](#cell-type-change) earlier in the debugging guide.

## I can’t export my assignment as a PDF due to a `LatexFailed` error

Occasionally when running the `grader.export(run_tests=True)` cell at the end of the notebook, you run into an error where the PDF failed to generate:

```{image} images/LatexError.png
:width: 500
:alt: Screenshot of a latex error that begins with 'LatexFailed: PDF creating failed, captured latex output:...'
```

Converting a Jupyter notebook to a PDF involves formatting some of the markdown text in [LaTeX](https://www.latex-project.org/). However, this process will fail if your free response answers have (unresolved) LaTeX characters like `\n`, `$`, or `$$`. There are several ways to resolve this:

1. **Export the notebook as a PDF**: In the upper left hand menu, go to `File` -> `Save and Export Notebook As` -> `PDF`. Upload this file to Gradescope under the "Submit PDF" option.
2. **Print the notebook from HTML**: In the upper left hand menu, go to `File` -> `Save and Export Notebook As` -> `HTML`. In the new tab that will open up, print the website by typing `ctrl` + `p` (Windows) or `cmd` + `p` (Mac).
3. **Take screenshots**: If you're short on time, your best bet is to take screenshots of your free response answers. When submitting to Gradescope, choose the "Submit Images" options instead of the "Submit PDF" option.
4. **Removing special LaTeX characters**: If you have more time and would like the Datahub-generated PDF, please remove any special LaTeX characters from your free response answers.

If you use an alternate form of submission listed above, you don't need to worry if you can't select pages or if the selection doesn't align. We'll manually look through your submission when grading, and will account for that.

## I can't open Jupyter: `HTTP ERROR 431`

If this happens, try [clearing your browser cache](https://support.google.com/accounts/answer/32050?hl=en&co=GENIE.Platform%3DDesktop) or opening Datahub in an incognito window.

## Datahub is not loading

If your link to Datahub is not loading, go to [https://data100.datahub.berkeley.edu/hub/home](https://data100.datahub.berkeley.edu/hub/home) and restart your server.
