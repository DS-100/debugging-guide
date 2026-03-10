---
title: Project A1 Hidden Tests
---

## Question 2

### Q2a

- Ensure the final answer has a length of 4
- The third element in the final answer should be 10

## Question 4

### Q4a

- Make sure the values in `training_data` haven't been altered
- For example, check that the values in `"Building Square Feet"` haven't been changed
- If we remove outliers for `"Log Sale Price"` with a lower bound of 8 and higher bound of 10, the sum of the resulting `"Building Square Feet"` should be close to 5,791,106

### Q4b

Hint: consider the x-axis and that most of the data is distributed to the left from $0.5 \times 10^6 = \$500,000$.

### Q4c

After removing outliers, `training_data` should have 153,776 rows remaining.

## Question 5

### Q5a

A good representative of `"Description"` column value in `training_data` is shown below:

> "This property, sold on 06/10/2016, is a one-story household located at 104 SAUK TRL. It has a total of 5 rooms, 2 of which are bedrooms, and 1.0 of which are bathrooms."

Consider what features of houses are specified here.

### Q5b

- The values of the `"Bathrooms"` column should sum up to 288,922
- `training_data` should contain 167,797 entries with fewer than 5 bathrooms

## Question 6

### Q6a

There are many ways to approach this question. Using `.unique()` pandas function is one of the ways to solve it.

### Q6b

- Make sure your final answer only contains 10 unique neighborhood codes
- The sum of the `"Neighborhood Code"`(s) should equal 3,824,060

### Q6c

The three most expensive neighborhood codes (using the median) are neighborhood 44, 94, and 93.

### Q6d

Using the three most expensive neighborhood codes from Q6c, there should be 1,290 rows belonging to those neighborhoods.

## Question 7

### Q7a

`training_data` should have 4 unique wall materials with `value_counts()` = [70303, 59125, 35717, 3786]

### Q7b

The sum of the one-hot encoded columns should equal the number of rows in `training_data`.
