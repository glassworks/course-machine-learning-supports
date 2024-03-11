# Using your model

Congratulations, you have now trained your model using **multiple linear regression** with a **squared error cost function.**

We have calculate the values of m and c that minimise the cost function.

```
Optimisation result: m=[  8.80200001 -26.42170944 -63.20090996  -1.34650381], c=186.4533393777293
Optimal cost: 243.62977476473606
```

Now we want to predict the value of our apartment:

* size : 38 square meters
* rooms: 2
* floors: 1
* age: 20



```python
import numpy as np

m = np.array([  8.80200001, -26.42170944, -63.20090996,  -1.34650381])
c = 186.4533393777293

features = np.array([
  38,   # size
  2,    # rooms
  1,    # floors
  20    # age
])

predicted_price = np.dot(m, features) + c
print(f"The predicted value of your apartment is {predicted_price:8.2f}k €")

```
