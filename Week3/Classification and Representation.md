# Classification

To attempt classification, one method is to use linear regression and map all predictions greater than 0.5 as a 1 and all less than 0.5 as a 0. However, this method doesn't work well because classification is not actually a linear function.

The classification problem is just like the regression problem, except that the values we now want to predict take on only a small number of discrete values. For now, we will focus on the **binary classification problem** in which y can take on only two values, 0 and 1. (Most of what we say here will also generalize to the multiple-class case.) For instance, if we are trying to build a spam classifier for email, then x(i) may be some features of a piece of email, and y may be 1 if it is a piece of spam mail, and 0 otherwise. Hence, y∈{0,1}. 0 is also called the negative class, and 1 the positive class, and they are sometimes also denoted by the symbols “-” and “+.” Given x(i), the corresponding y(i) is also called the label for the training example.

## Hypothesis Representation

We could approach the classification problem ignoring the fact that y is discrete-valued, and use our old linear regression algorithm to try to predict y given x. However, it is easy to construct examples where this method performs very poorly. Intuitively, it also doesn’t make sense for hθ(x) to take values larger than 1 or smaller than 0 when we know that y ∈ {0, 1}. To fix this, let’s change the form for our hypotheses hθ(x) to satisfy 0≤hθ(x)≤1. This is accomplished by plugging θTx into the Logistic Function.

Our new form uses the "Sigmoid Function," also called the "Logistic Function":
*****************************************************************************************

<img src="https://latex.codecogs.com/gif.latex?h_\theta(x)&space;=&space;g(\theta^Tx)" />  
<img src="https://latex.codecogs.com/gif.latex?z=\theta^Tx" />   
<img src="https://latex.codecogs.com/gif.latex?g(z)=\frac{1}{1+e{^-z}}" />

*****************************************************************************************
The following image shows us what the sigmoid function looks like:  

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/1WFqZHntEead-BJkoDOYOw_2413fbec8ff9fa1f19aaf78265b8a33b_Logistic_function.png?expiry=1503619200000&amp;hmac=zhts0YGvhNwdaGHuD-t1aUV8QWYRPIZFjBrxla83ikI" alt="" data-asset-id="1WFqZHntEead-BJkoDOYOw">

The function g(z), shown here, maps any real number to the (0, 1) interval, making it useful for transforming an arbitrary-valued function into a function better suited for classification.

hθ(x) will give us the probability that our output is 1. For example, hθ(x)=0.7 gives us a probability of 70% that our output is 1. Our probability that our prediction is 0 is just the complement of our probability that it is 1 (e.g. if probability that it is 1 is 70%, then the probability that it is 0 is 30%).
  
*****************************************************************************************

<img src="https://latex.codecogs.com/gif.latex?h_\theta(x)=P(y=1|x;\theta)=1-P(y=0|x;\theta)" />  
<img src="https://latex.codecogs.com/gif.latex?P(y=1|x;\theta)+P(y=0|x;\theta)=1" />   

*****************************************************************************************

