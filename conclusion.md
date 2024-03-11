# Conclusion

Congratulations, you have constructed your first machine learning algorithm !

This is one of the bases of many more types of learning including deep learning, neural networks and so on.

### Next steps

Linear regression is just one form of machine learning.&#x20;

The next logical step in your AI journey would be **logistic regression**, which is an adaptation of what we just saw (different cost function), that allows us to **classify** items. That is, answer the question:&#x20;

> Is my element type A or type B ?

... where use cases include:&#x20;

* is this email spam ?
* is this cancer A or cancer B ?
* ...

From there, the next steps would be to study unsupervised learning and more advanced techniques like neural networks.

### Vector base databases

Also, remember our Vectorial Databases ? You may start to notice a similarity !

Remember our trained model ?

```
Optimisation result: m=[  8.80200001 -26.42170944 -63.20090996  -1.34650381], c=186.4533393777293
Optimal cost: 243.62977476473606
```

We have 4 coefficients for our model, which could be stored as an entry in our vector based database.

We would thus populate this database by training N different models using N different datasets, and storing the results in the database. For example, one for each arrondissement in Paris. We could then find out which sectors of paris have the most similar sets of selling features !



