---
title: Project A1 Common Questions
---

## Question 6

### `TypeError: could not convert string to float: 'SF'`

Type errors like these usually stem from applying a numeric aggregation function to a non-numeric column as described in the `pandas` [çsection](#convert-str-float) of the debugging guide.

Aggregation functions like `np.median` and `np.mean` are only well-defined for columns with numeric types like `int` and `float`. Your code is likely trying to aggregate across all columns in `training_data`, including those of type `str`. Instead of aggregating across the entire `DataFrame`, try just selecting the relevant columns.

### `TypeError: unhashable type: 'Series'`

This error can occur if you try and use Python's `in` to check whether values in a `Series` are contained in a list. If you're trying to perform boolean filtering in this manner, you should look into the `.isin` ([documentation](https://pandas.pydata.org/docs/reference/api/pandas.Series.isin.html)) function as introduced in HW 2.

## Question 7

### I'm not sure how to use `sklearn` to do One Hot Encoding

A good starting point is to revisit the One Hot Encoding question in Lab 7. It's recommended you look through this portion of [the walkthrough](https://youtu.be/LohVOmiulHQ?feature=shared&t=442), so you have a good understanding of how to use the `OneHotEncoder` object. Pay attention to what each variable represents and the expected outputs of the functions used. Can you map the logic from the lab to this project? A nice way to start is to make a new cell and experiment with examples from [the documentation](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.OneHotEncoder.html).

### My OHE columns contain a lot of `NaN` values

This may happen if you try and merge the OHE columns with the `training_data` table without making sure both `DataFrame` have the *same index values*. Look into the `pd.merge` [documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.merge.html) for ways to resolve this.

