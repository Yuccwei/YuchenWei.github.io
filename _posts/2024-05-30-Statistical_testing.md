---
title: 'How to test a normal distribution'
date: 2024-05-30
permalink: /_posts/2024-05-30-statistical-testing-post
tags:
  - cool posts
  - category1
  - category2
  - statistics
---

Jarque–Bera test
======

We can use Jarque-Bera test to test whether a distribution is normal or not. To begin, we first generate a normal distribution and do the test:

```python
import numpy as np
from scipy import stats

import matplotlib.pyplot as plt

# Parameters for the normal distribution
mean = 0  # Mean of the distribution
std_dev = 1  # Standard deviation of the distribution
size = 1000  # Number of samples to generate

# Generate random samples from a normal distribution
samples = np.random.normal(mean, std_dev, size)

# Calculate skewness and kurtosis
skewness = stats.skew(samples)
kurtosis = stats.kurtosis(samples)

# Perform the Jarque-Bera test
jb_stat, p_value = stats.jarque_bera(samples)

print("Skewness:", skewness)
print("Kurtosis:", kurtosis)
print("Jarque-Bera test statistic:", jb_stat)
print("p-value:", p_value)
```

The result is:

Skewness: 0.09205775651647653

Kurtosis: -0.051353492317578464

Jarque-Bera test statistic: 1.522320971358296

p-value: 0.46712402160647026

For comparison, we do the test for Beta distribution \\( \text{Beta}(2, 2) \\). The code is attched below:

```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats

# Generate random data from a beta distribution
np.random.seed(0)
data = np.random.beta(2, 2, 1000)  # Parameters shape1=2, shape2=2

# Calculate skewness and kurtosis
skewness = stats.skew(data)
kurtosis = stats.kurtosis(data)

# Perform the Jarque-Bera test
jb_stat, p_value = stats.jarque_bera(data)

# Print statistics
print("Skewness:", skewness)
print("Kurtosis:", kurtosis)
print("Jarque-Bera test statistic:", jb_stat)
print("p-value:", p_value)
```

The output is:

Skewness: -0.06877155720899528

Kurtosis: -0.8898416028853444

Jarque-Bera test statistic: 33.780674439556655

p-value: 4.619763550202317e-08