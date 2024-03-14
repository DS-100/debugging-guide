---
title: Project A2 Common Questions
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

## Question 5f

### General Debugging Tips
Question 5 is a difficult and time-consuming question that's mirrors a lot of data science work in the real world: clean data, explore data, transform data, fit a model, and work within a pre-set pipeline. Here are some general debugging tips to make the process easier: 

1. Separate small tasks into helper functions, especially if you will execute it multiple times. For example, one-hot-encoding is a good helper function to make because you'll likely perform it on multiple categorical columns. If you're parsing a column with RegEx, it also might be a good idea to separate it out to a helper function. This allows you to verify that you're not making errors in these small tasks and prevents unknown bugs from appearing. 
2. Feel free to make new cells to play with the data! As long as you delete them afterwards, it will not affect the autograder. 
3. The `feature_engine_final` looks daunting at first, TODO 

### `ValueError: Per-column arrays must each be 1-dimensional`
If you're passing the tests for q5d but getting this error in q5f, then you're `Y` is likely a `DataFrame` instead of a `Series`. `sklearn` models like `LinearRegression` expect `X` to be a 2D datatype (ie. `DataFrame`, 2D `numpy` array) and `Y` to be a 1D datatype (ie. `Series`, 1D `numpy` array). 

### `KeyError: ‘Sale Price’`/`KeyError: ‘Log Sale Price’`
`KeyError`s are raised when a column name does not exist in your `DataFrame`. You're likely getting this error because the test set does not contain a `"(Log) Sale Price"` as that's what we're trying to predict. Make sure you only reference the `"(Log) Sale Price"` column when working with training data (`is_test_set=False`).

### `Input X contains infinity or a value too large for dtype(‘float64’)` 
The reason why you're `X` data contains infinity is likely because you take the log of 0 somewhere in your code. To prevent this, check out the solution to [Discussion 4: Logarithmic Transformations, part e](https://drive.google.com/file/d/1Ms_sTgBIfftd0lfYge7wWubII4-vtPYD/view)

### `Input X contains NaN`
The reason why you're `X` data contains `NaN` values is likely because you take the log of a negative number somewhere in your code. To prevent this, check out the solution to [Discussion 4: Logarithmic Transformations, part e](https://drive.google.com/file/d/1Ms_sTgBIfftd0lfYge7wWubII4-vtPYD/view)

### `ValueError: The feature names should match those that were passed during fit`
TODO