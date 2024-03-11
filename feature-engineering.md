# Feature engineering

You may still have a number of questions:

* what if the data is not linear ?
* what features do I use, and which ones should I abandon ?
* how do I choose a value of alpha (learning rate) ?

These questions are partially answered by the activity called **feature engineering.**



### Non linear data

One aspect of feature engineering is using a function that is non-linear. We can for example use quadratic curves instead of lines.

$$
y = 1+x^2
$$

Your choice of curve can be based on your intuition and what you may observe when plotting the data.



### Feature engineering and scaling

Sometimes, depending on our knowlegde of the domain, we may need to modify our data to better represent reality.

For example, imagine we only had the length and width of a property, and not its value in square meters. We would "engineer" the data to create a new column "square meters" before feeding it to the algorithm, as we know there is a more direct correlation between area and price.

It is also a good idea to modify the data so that all the features are more or less in the same scale. In our example, we divided the value of the houses by 1000 to bring the values in line with the area. Otherwise our cost-function would have produced huge results, and the gradient descent may have produced overflow errors, or take much longer to converge.



## Learning rate

Play around with the value of alpha in your implementations, you may find that the algorithm converged faster, or, not at all !

This is because sometimes in an iteration we can move too much, and overshoot the minimum, and actually start climbing back up the other side of the curve ! This is not great. So the alpha needs to be chosen with care.

