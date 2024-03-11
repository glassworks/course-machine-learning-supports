# Multiple variables

Up until now we have used only a single feature, the size of the apartment, to determine its price.

But we know in reality there are a number of factors that influence the price:

* size
* number of bedrooms
* number of floors
* age

How can we use linear regression to predict the price, by taking into account all of these factors ?

In our case, each row of our training set has 4 data points.

We can express our linear function using a these 4 variables:

$$
f(x_1, x_2, x_3,x_4)^{(i)} = m_1x_1^{(i)} + m_2x_2^{(i)} + m_3x_3^{(i)} + m_4x_4^{(i)} + c
$$

Note that each feature will have its own coefficient **m** that measures how much of an impact it has on house prices.

We can generalise our function as the following (for j features):

$$
f({\textbf{x}^{(i)}}) =m\cdot x^{(i)} + c
$$

Here we use the dot product between m and x, which are both now two arrays. The dot product multiplies each corresponding pair of values from the two arrays, and adds up the result.

In python, the numpy library is able to perform this operation using the dot product operator:



```python
c = 100

# Instead of expressing m as a scalar, it is now an array
m = np.array([1, 1, 1, 1])

# X is still the training set, with j features per sample
X = np.array([
   [3., 2., 7.],
   [4., 5., 1.],
   [5., 0., 0.]
])

# For the i'th sample we can calculate the estimate 
i = 0
y_estimate = np.dot(X[i], m) + c

```



### Exercise : cost

Copy your previous implementation of the cost function, and adapt it to use multiple features.

The cost should be:

```
Average cost is : 21555.95076014
```

### Exercise : gradient

Copy your previous implementation of the gradient (partial derivatives), and adapt it to use multiple features.

Careful, when calculating dj\_dm, we now calculate the sum of gradients across all features:

```python

def calculate_gradient(X, y_real, m, c):
  # n = number of samples
  # f = number of features
  n,f = X.shape

  ...
  # iterate over each sample
  for i in range(n):
    ...
    # iterate over each feature for dj_dm
    for j in range(f):
      dj_dm[j] += cost * X[i][j]
```

### Exercise : gradient descent

Copy your previous implementation of gradient descent, and make it work over multiple variables. Do you get the same result as I do ?

```
Optimisation result: m=[  8.80200001 -26.42170944 -63.20090996  -1.34650381], c=186.4533393777293
Optimal cost: 243.62977476473606
```
