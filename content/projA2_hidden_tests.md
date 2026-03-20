---
title: Project A2 Hidden Tests
---

## Question 1

### Q1c

Regressive taxation overvalues inexpensive properties. In other words, these homes may be assessed at a higher price than they may actually be worth.

## Question 3

### Q3a

As the 2nd model has a higher complexity, we expect its training loss to be no worse than the training loss of the 1st model.

### Q3b

The following code should return True

```python
np.random.seed(1337)
tr_m2, te_m2 = train_val_split(full_data)
X_tr_m2, Y_tr_m2 = feature_engine_pipe(tr_m2, m2_pipelines, 'Log Sale Price')
X_te_m2, Y_te_m2 = feature_engine_pipe(te_m2, m2_pipelines, 'Log Sale Price')
# Test 1
bool(np.isclose(Y_tr_m2.sum(), 1643505.2095877344) and np.isclose(Y_te_m2.sum(), 412085.5255227775))
# Test 2
bool(np.isclose(Y_train_m1.sum(), Y_tr_m2.sum()) and np.isclose(Y_valid_m1.sum(), Y_te_m2.sum()))
```

## Question 4

### Q4b

We see that properties with a lower sale price typically have negative residuals, which means their predicted worth/sale price is overvalued.
