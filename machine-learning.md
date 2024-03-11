# Machine learning

## What is machine learning ?

When we code, we give a computer a strict set of instructions in order to accomplish a task.

However, sometimes, we do not have all the information at the time of coding, and most importantly, we **do not have all of the information**, in order to foresee future decision making.

Sometimes, the logic used to formulate a decision is not easy to construct.

#### Example : how much is my apartment worth ?

I wish to sell my apartment, but have no idea what it is worth.

I know there may be a number of factors that may influence its price.

* The size of the apartment
* The location
* Number of bedrooms
* Floor
* ...

How do we factor in all of these criteria and formulate a conclusion ?

We could try to write a set of conditions (or create a **decision tree**) that would try to reason out the final price of my apartment. However, this solution may not be sufficient :&#x20;

* Perhaps in my reasoning I have missed a subtle element that impacts the price and cause the estimation to be way off
* Markets evolve, prices go up, or go down, and the aspects that effect the house value change over time

Our algorithm would have to somehow be adaptable, and be able to update itself over time.

Enter **machine learning**, a way of constructing an algorithms to be able to look at evolving data and arrive at a decision for us, without explicitly giving a set of instructions.

Generally speaking, we can divide machine learning into two categories:&#x20;

* Supervised learning : given a training set of existing data with the **correct answers**, derive a function that can predict new answers that follow the same pattern
  * Value prediction
  * Classification
* Unsupervised learning : Find something interesting in **unlabled data**
  * Clustering
  * Anomaly detection
  * Dimensionality reduction



{% hint style="success" %}
For our apartment, we can gather a history of sale prices, that span many years. We can therefore consider our problem a case for **supervised learning** :&#x20;

* We have a set of **correct answers**
* We want to derive a new value (our sale price) that follows the same trends&#x20;
{% endhint %}

### Supervised Learning

Generally speaking, we would look at other apartments that have sold with similar criteria, and try and match our price with those ones. We could consider this survey of prices our **training data**.

Lets start with just one criteria : **the size of the appartment**

The chart below shows a plot of housing price data: size (in square metere) vs sale price :

<figure><img src=".gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

We can see that there seems to be a relation between the **feature** "size in square meters" and the sale price. Notably, as the size increases, so the sale price _tends to increase too._

Intuitively we can roughly deduce the value of our apartment given this graph.

If our apartment is 55 square meters, we can deduce a price our roughly 450k€, according to this graph.

This is a rough "guestimate", we want our algorithm to be able to make this deduction automatically (that is, without our intuition).

### A linear relationship

Looking at the data, we can see that the data is **roughly linear**, and maybe we can find a function that transforms the size into the price via a linear relationship.

We learned at school that the formula for a line is:

$$
y = mx + c
$$

That is given a value `x`, we can transform that value into `y`, by multiplying it by some coefficient `m` and then adding some value `c`

That is, we define a **function** that transforms **x** into **y**

In our case, we want to find a function that transforms an apartment size (x) into the sale price (y).

Since we think that this function might be linear, can we find the values for **m** and **c** that best predict the training data ?

Let's try some values manually. For `m = 1` and `c = 0`:

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

Not a great fit.

How about, for `m = 5` and `c = 100`:

<figure><img src=".gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

Better ! But still not great.



### Exercise&#x20;

See if you can find a line that best matches the data.

Download the sample project [https://dev.glassworks.tech:18081/courses/machine-learning-examples](https://dev.glassworks.tech:18081/courses/machine-learning-examples).

* Look at the sample data under `data/house_prices.csv`
* Run the first script that plots this data with a fitted line:

```
python3 001_plot.py
```

Try different versions of the the formula for a line (line 31):

```python
graph('5*x + 100', range(20, 100), 'm')
```

Can you find one that fits ?

How do you evaluate if the fit is good ?
