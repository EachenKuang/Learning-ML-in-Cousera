# Overfitting and Regularization

## The Problem of Overfitting

Consider the problem of predicting y from x ∈ R. The leftmost figure below shows the result of fitting a y = θ0+θ1x to a dataset. We see that the data doesn’t really lie on straight line, and so the fit is not very good.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/0cOOdKsMEeaCrQqTpeD5ng_2a806eb8d988461f716f4799915ab779_Screenshot-2016-11-15-00.23.30.png?expiry=1503705600000&amp;hmac=InQcmwxJz7rmYzHGDd6gIww5GndZUESIUHwUejHe_1A" alt="" data-asset-id="0cOOdKsMEeaCrQqTpeD5ng">

Instead, if we had added an extra feature x2 , and fit y=θ0+θ1x+θ2x2 , then we obtain a slightly better fit to the data (See middle figure). Naively, it might seem that the more features we add, the better. However, there is also a danger in adding too many features: The rightmost figure is the result of fitting a 5th order polynomial y=∑5j=0θjxj. We see that even though the fitted curve passes through the data perfectly, we would not expect this to be a very good predictor of, say, housing prices (y) for different living areas (x). Without formally defining what these terms mean, we’ll say the figure on the left shows an instance of **underfitting**—in which the data clearly shows structure not captured by the model—and the figure on the right is an example of **overfitting**.

Underfitting, or high bias, is when the form of our hypothesis function h maps poorly to the trend of the data. It is usually caused by a function that is too simple or uses too few features. At the other extreme, overfitting, or high variance, is caused by a hypothesis function that fits the available data but does not generalize well to predict new data. It is usually caused by a complicated function that creates a lot of unnecessary curves and angles unrelated to the data.

This terminology is applied to both linear and logistic regression. There are two main options to address the issue of overfitting:

1) Reduce the number of features:

- Manually select which features to keep.
- Use a model selection algorithm (studied later in the course).
2) Regularization

- Keep all the features, but reduce the magnitude of parameters θj.
- Regularization works well when we have a lot of slightly useful features.

## Cost Function

If we have overfitting from our hypothesis function, we can reduce the weight that some of the terms in our function carry by increasing their cost.

Say we wanted to make the following function more quadratic:

> <img src="https://latex.codecogs.com/gif.latex?\theta_0&plus;\theta_1x&plus;\theta_2x^2&plus;\theta_3x^3&plus;\theta_4x^4"  />

We'll want to eliminate the influence of θ3x3 and θ4x4 . Without actually getting rid of these features or changing the form of our hypothesis, we can instead modify our **cost function**:

> <img src="https://latex.codecogs.com/gif.latex?min_\theta\frac{1}{2m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})^2+1000\dot\theta^2_3+1000\dot\theta^2_4"  />

We've added two extra terms at the end to inflate the cost of θ3 and θ4. Now, in order for the cost function to get close to zero, we will have to reduce the values of θ3 and θ4 to near zero. This will in turn greatly reduce the values of θ_3x^3 and θ_4x^4 in our hypothesis function. As a result, we see that the new hypothesis (depicted by the pink curve) looks like a quadratic function but fits the data better due to the extra small terms θ_3x^3 and θ_4x^4.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/j0X9h6tUEeawbAp5ByfpEg_ea3e85af4056c56fa704547770da65a6_Screenshot-2016-11-15-08.53.32.png?expiry=1503705600000&amp;hmac=S2Sfv2ihqAGAIhHA4FyCLjc-Kjt2qDUsQNSrqZx65ZQ" alt="" data-asset-id="j0X9h6tUEeawbAp5ByfpEg">

We could also regularize all of our theta parameters in a single summation as:

> <img src="https://latex.codecogs.com/gif.latex?min_\theta\frac{1}{2m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})^2+\lambda\sum_{j=1}^n\theta^2_j"  />

The λ, or lambda, is the **regularization parameter**. It determines how much the costs of our theta parameters are inflated.

Using the above cost function with the extra summation, we can smooth the output of our hypothesis function to reduce overfitting. If lambda is chosen to be too large, it may smooth out the function too much and cause underfitting. Hence, what would happen if **λ=0** or is too small ?