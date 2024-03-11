# Gradient descent

For our housing example, it turns our that our cost function is actually a n-dimensional paraboloid, that always has a global minimum. All we have to do is follow the steepest curve downwards until we find the minimum cost.&#x20;

Up until now we have calculate the cost between the actual price of an apartment, and the one estimated by our line:

$$
cost^{(i)} = (f(x^{(i)}) - y^{(i)})^2
$$

We looped over all the training samples, calculated the sum, then calculated the average. In mathematics, we can actually write all this down as one formula:

$$
J(m,c) = \dfrac{1}{2n}\sum_{i=0}^{n-1}(f(x^{(i)}) - y^{(i)})^2
$$



In the above formula:

* **n** is the number of samples in our training set
* `f(x)` is the formular for our line, expressed in terms of **m** and **c** :  `f(x) = mx + c`
* We divided the result by 2 to make the math work a bit better later. This has no effect on the **relative costs** between the different lines.

It turns our that J(m,c) is a paraboloid:

<figure><img src=".gitbook/assets/pu19nClCwOXSvtWCIFfWrTMnR1554842664_kc (1).png" alt=""><figcaption></figcaption></figure>

If we follow the gradient in the negative direction, we will end up at the minimum, and will have found the values for m and c that have the least cost.

But what is that gradient ?

Well, basic knowledge of calculus tells as that the derivative of a function gives us the formula for the gradient at a specific point.

So this means we can actually create the formula for the gradient. Note that the gradient is is two dimensions, so we use to formulae (as partial derivatives).

The partial derivative for the m dimension is :

$$
\dfrac{\delta{J(m,c)}}{\delta{m}}=\dfrac{1}{n}\sum_{i=0}^{n-1}(f(x^{(i)}) - y^{(i)})x^{(i)}
$$

The partial derivative for the c dimension is:

$$
\dfrac{\delta{J(m,c)}}{\delta{c}}=\dfrac{1}{n}\sum_{i=0}^{n-1}(f(x^{(i)}) - y^{(i)})
$$

What does this all mean ?

Using our training data, and the current values of m and c, we can calculate the gradient of the cost function at that specific point.&#x20;



### Exercise : calculate the gradient

Duplicate and modify your previous python script, and make the following changes:

*   Write a function `cost` that takes in 4 parameters:

    * A 1 dimensional array containing the apartment size samples
    * A 1 dimensional array containing the apartment prices
    * The current value of **m**
    * The current value of **c**

    The function should return the total cost **J(mc)**
*   Write a function  `calculate_gradient` that takes in 4 parameters:

    * A 1 dimensional array containing the apartment size samples
    * A 1 dimensional array containing the apartment prices
    * The current value of **m**
    * The current value of **c**

    The function should return two values : **dj\_dm** and **dj\_dc** according to the above formulas.\


Test your functions.&#x20;

Over the small test data set:&#x20;

```
Average cost is : 123.
Gradient dj_dm : 15.
Gradient dj_dc : 5.
```

Over the housing prices data-set:

```
Average cost is : 1519.84451404
Gradient dj_dm : -141.39677682
Gradient dj_dc : 0.43652
```



### Gradient descent

Now that we can calculate the gradient of our cost function, we just need to follow the negative gradient down to the global minimum.

This is done in an iterative manner:

```
repeat until convergence {
    m = m - (alpha * dj_dm)
    c = c - (alpha * dj_dc)
}
```

There are two new principles here:

* **convergence** : the point at which the cost function no longer varies between iterations OR until we have exceeded the amount of time or number of iterations allowed
* **alpha :** the learning rate. In effect, a multiplier of the gradient. It specified how far to move in the direction of the gradient. A low number will make for a slower, more reliable descent. A high number will be faster, but may risk overshooting.

### Exercise : gradient descent

Can you implement the above algorithm in python ?

Test using `alpha = 0.0005` and with a maximum of `100000` iterations.
