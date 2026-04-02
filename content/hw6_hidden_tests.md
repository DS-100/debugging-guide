---
title: Homework 6 Coding Hidden Tests
---

## Q2a

Your train_rmse_cpc should be should be close to 1.311759
Your test_rmse_cpc should be close to 2.143703

## Q3a

The following code should return True

```python
np.random.seed(100)
_peer_assessments_0 = bootstrap_sample(cleaned_college_data, 1)[0]["Peer Assessment Score (1-5)"]
_six_yr_grad_rate_2 = bootstrap_sample(cleaned_college_data, 1)[0]["Actual 6yr graduation rate"]
_test_3a_result = (
    np.isclose(_peer_assessments_0.mean(), 3.2508982035928145, atol = 8e-3) and
    np.isclose(_six_yr_grad_rate_2.std(), 11.846683695468434, atol = 8e-3)
)
bool(_test_3a_result)
```

## Q3b

All models in full_feature_models should have 20 coefficients and nonzero intercept
All coefficients from the 0th and 1st model in full_feature_models should be different

## Q3c

The first 3 confidence intervals in full_feature_cis should equal [(22.639177006206683, 51.68195293847012), (6.924953731706237, 9.602527303316572), (-0.1038285044940231, -0.054630807210654865)]
