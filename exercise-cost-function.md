# Exercise : cost function

In the previous example you tried multiple values of **m** and **c** to find a line that best fits the training data.

But there must be a better, more reliable way to measure if the line is good or not.

Or more specifically, whether one line is **better** or **worse** than another line.

Can you write some python that is able to **calculate an overall score** for a line, given the training data ?



{% hint style="success" %}
Actually, this is quite easy to calculate. We already know what the real answer is for each sample **(i)** in our training set:

$$
y^{(i)}
$$

For each answer, we also know what the size in square meters was that produced that price:

$$
x^{(i)}
$$

If we plug this value of **x** into the current formula for our line, we should get an **estimation** of **y** produced by our formula :



$$
\hat{y}^{(i)} = mx^{(i)} + c
$$



To calculate how good our current line is, we just calculate the squared difference between the real answer and the estimated answer:



$$
cost^{(i)} = (\hat{y}^{(i)} - y^{(i)})^2
$$



Do this for every data sample in the training set, and calculate the **average cost** over all the data samples.
{% endhint %}

Do you know why we calculate the squared difference, and not just the difference ?

Now its up to you to implement this in python !

First, start with a small set of simple data that is easy to verify:



```python
# Feature set
X_train = np.array([
  [3., 0., 0.],
  [4., 0., 0.],
  [5., 0., 0.]
])

# Result set
y_train = np.array([100., 130., 127.])

```

You should get the following results:

| m | c   | cost     |
| - | --- | -------- |
| 1 | 0   | 13389.66 |
| 5 | 100 | 109.66   |
| 6 | 100 | 123      |

Now use the training set:&#x20;

```python
X_train, y_train = load_data()

# X_train = np.array([
#   [3., 0., 0.],
#   [4., 0., 0.],
#   [5., 0., 0.]
# ])

# y_train = np.array([100., 130., 127.])

```



| m | c   | cost      |
| - | --- | --------- |
| 1 | 0   | 110134.46 |
| 5 | 100 | 5402.03   |
| 6 | 100 | 3039.68   |

As you can see, on our training set, the last configuration of our line actually has a lower cost than on the simple training set!



<details>

<summary>Solution</summary>

```python
import numpy as np
import matplotlib.pyplot as plt
from utils import load_data
  
X_train, y_train = load_data()
# X_train = np.array([
#   [3., 0., 0.],
#   [4., 0., 0.],
#   [5., 0., 0.]
# ])

# y_train = np.array([100., 130., 127.])

def cost(x_sample, y_real, m, c):
  y_estimate = x_sample * m + c
  print(f"\t Estimate : { x_sample } * { m } + { c } = { y_estimate }")
  cost = (y_estimate - y_real)
  print(f"\t Cost : { y_estimate } - { y_real } = { cost }")
  return cost**2

m = 6
c = 100
  
cost_sum = 0
for i in range(len(y_train)):
  print(f"Sample {i} :")

  cost_i = cost(X_train[i, 0], y_train[i], m, c)
  cost_sum += cost_i
  
cost_sum /= len(y_train)
print(f"Average cost is : {cost_sum}")

```

</details>
