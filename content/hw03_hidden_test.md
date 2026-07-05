---
title: HW 3 Hidden Tests
---

## Question 1

### Q1a

- `q1a` should be exactly the first 200 characters of `data/nyt_articles.txt`:

```text
{"web_url":{"0":"https:\/\/www.nytimes.com\/2020\/01\/01\/well\/move\/exercise-physical-activity-workout-time.html","1":"https:\/\/www.nytimes.com\/2020\/01\/01\/world\/europe\/pope-francis-slap-video
```

### Q1b

- The answer is B.

## Question 2

### Q2a

- The index of `dates` should match the index of `news_df`.
- `dates` should have exactly the columns `Year`, `Month`, and `Minute`.
- `dates["Year"].loc[291]` should be `2020`.
- `dates["Month"].loc[593]` should be `2`.
- `dates["Minute"].value_counts()[45]` should be `96`.

### Q2bi

- The answer is B.

### Q2bii

- The answer is A.

### Q2c

- `modified_pattern` should match only the first quote in:
  ```python
  '"A quote within marks should be captured."But not this part, which is inside another pair of quotes."'
  ```
  The expected output is:
  ```python
  ['"A quote within marks should be captured."']
  ```

- `modified_pattern` should not match a quote that does not end with one of the required punctuation marks:
  ```python
  '"A quote within marks but without punctuation shouldnt be matched"'
  ```
  The expected output is:
  ```python
  []
  ```

- `modified_pattern` should not match text without quotation marks:
  ```python
  'Your sentence should involve a quote.'
  ```
  The expected output is:
  ```python
  []
  ```

- `modified_pattern` should match a quote ending in a question mark:
  ```python
  '"TESTING FOR QUESTION MARK?"'
  ```
  The expected output is:
  ```python
  ['"TESTING FOR QUESTION MARK?"']
  ```

- `modified_pattern` should match a quote ending in an exclamation mark:
  ```python
  '"TESTING FOR EXCLAMATION MARK!"'
  ```
  The expected output is:
  ```python
  ['"TESTING FOR EXCLAMATION MARK!"']
  ```

### Q2d

- The total number of `New Year` mentions should be `447`.
- The total number of `GPT Model` mentions should be `189`.

## Question 3

### Q3ci

- The first row of `top_negative["lead_paragraph"]` should start with:
  ```text
  The day after Labor Day has got to be one of the worst days in the American
  ```

- The first row of `top_positive["lead_paragraph"]` should be:
  ```text
  Happy New Year, audiophiles!
  ```