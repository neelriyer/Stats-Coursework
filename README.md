# Stats-Coursework

Code from Bayesian Statistical Inference Courses. Mostly done in R.

Output and explanations added inline. [Sample notebook](gelman_bayesian_data_analysis.ipynb) 

Code excerpt:
```
n = 1000

alpha = 0.05
sd = 1
S = 1e4
upper_accuracy_vec = NULL
lower_accuracy_vec = NULL

for (i in 1:S) {

  x = rnorm(n, 0, sd)

  quantiles = quantile(x, c(alpha/2, 1-alpha/2), names = F)
  lower_quantile_est = quantiles[1]
  upper_quantile_est = quantiles[2]

  lower_quantile_true = qnorm(alpha/2, 0, 1)
  upper_quantile_true = qnorm(1 - alpha/2, 0, 1)

  lower_accuracy = abs(lower_quantile_true - lower_quantile_est)
  upper_accuracy = abs(upper_quantile_true - upper_quantile_est)


  upper_accuracy_vec = c(upper_accuracy_vec, upper_accuracy)
  lower_accuracy_vec = c(lower_accuracy_vec, upper_accuracy)
  lower_accuracy_vec

}


mean(upper_accuracy_vec)
mean(lower_accuracy_vec)
```

