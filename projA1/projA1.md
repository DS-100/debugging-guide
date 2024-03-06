---
title: Project A1 Common Questions
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

## Question 6

### `TypeError: could not convert string to float: 'SF'`

Type errors like these usually stem from applying a numeric aggregation function to a non-numeric column as described in the [Pandas section](https://ds100.org/debugging-guide/pandas/pandas.html#typeerror-could-not-convert-string-to-numeric) of the debugging guide.

Aggregation functions like `np.median` and `np.mean` are only well-defined for columns with numeric types. CIt is likely that your code is attempting to aggregate across all columns in training_data, including those of type `str`. Instead of aggregating across the entire DataFrame, try selecting the relevant columns upon which to aggregate.

### `TypeError: unhashable type: 'Series'

This error can occur if you try and use Python's `in` to check whether values in a `Series` are contained in a list. If you're trying to perform boolean filtering in this manner, you should look into the `isin` function as introduced in HW 2.

## Question 7

### I'm not sure how to use `sklearn` to do One Hot Encoding

A good starting point is to revisit the One Hot Encoding question in Lab 7. It's recommended you look through this portion of [the walkthrough](https://youtu.be/LohVOmiulHQ?feature=shared&t=442), so you have a good understanding of how to use the `OneHotEncoder` object. Looking through each line of code, be sure you know whether you understand what each variable represents, the output of the functions used, and what the similarities and differences are between the question in the lab and project are.

### My OHE columns contain a lot of `NaN` values

This may happen if you try and merge the OHE columns with the `training_data` DataFrame without making sure both dataframes have the same index values. Look into the [`pd.merge` documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.merge.html) for ways to resolve this.

