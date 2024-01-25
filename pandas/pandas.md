---
title: Pandas
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
jupyter: python3
---

## Understanding `pandas` errors
`pandas` errors can look red, scary, and very long. Fortunately, we don't need to understand the entire thing! The most important parts of an error message are at the **top**, which tells you which line of code is causing the issue, and at the **bottom**, which tells you exactly what the error message is. 

<center><img src = "pandas_error.png" width = "700"></img></a></center>

This note is (mostly) structured around the error messages that show up at the bottom. 

## My code is taking a really long time to run
It is normal for a cell to take a few seconds -- sometimes a few minutes -- to run. If it's is taking too long, however, you have several options: 

1. Try restarting the kernel. Sometimes, Datahub glitches or lags, causing the code to run slower than expected. Restarting the kernel should fix this problem, but if the cell is still taking a while to run, it is likely a problem with your code.
2. Scrutinize your code. Am I using too many for loops? Is there a repeated operation that I can substitute with a `pandas` function? 

## `KeyError: 'column_name'`
This error usually happens when we have a `DataFame` called `df`, and we're trying to do an operation on the column `'column_name'`. This `KeyError` means that `df` does not have a column called `'column_name'`. 

If you encounter this error, double check that you're operating on the right column. It might be a good idea to add a cell to display your `DataFrame`. You could also call `df.columns` to list all the columns in `df`.

## `TypeError: '___' object is not callable`
This often happens when you use a default keyword (like `str`, `list`, `sum`, or `max`) as a variable name, for instance 

    sum = 1 + 2 + 3

These errors can be tricky because they don’t error on their own but cause problems when we try to use the name `sum` (for example) later on in the notebook.

To fix the issue, identify any such lines of code, change your variable names to be something more informative, and restart your notebook.

Python keywords like `str` and `list` appear in green text, so be on the lookout if any of your variable names appear in green!

## `IndexError: index _ is out of bounds for axis _ with size _`
This error usually happens when you try to index a value that's greater than the size of the array/list/`DataFrame`/`Series`. For example 

    some_list = [2, 4, 6, 8]

`some_list` has a length of 4. If I try `some_list[6]`, this will error because index 6 is greater than the length of the array. Note that `some_list[4]` will also cause an `IndexError` because Python and `pandas` uses zero indexing, which means that the first element has index 0, the second element has index 1, etc. `some_list[4]` would grab the fifth element, which is impossible when the list only has 4 elements. 

## `TypeError: could not convert string to a float`
This error often occurs when we try to do math operations (ie. `sum`, `average`, `min`, `max`) on a `DataFrame` column or `Series` that contains strings instead of numbers (note that we can do math operations with booleans; Python treats `True` as 1 and `False` as 0). Double check that the column you're interested in is a numerical type (`int`, `float`, or `double`). If it looks like a number, but you're still getting this error, you can use `.astype(...)` ([documentation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.astype.html)) to change the datatype of a `DataFrame` or `Series`.
