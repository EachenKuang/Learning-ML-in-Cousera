# Logistic Regression Model
## Cost Function
We cannot use the same cost function that we use for linear regression because the Logistic Function will cause the output to be wavy, causing many local optima. In other words, it will not be a convex function.  

Instead, our cost function for logistic regression looks like:  

* * *

<img src="https://latex.codecogs.com/gif.latex?J(\theta)=\frac{1}{m}\sum^m_{i=1}Cost(h_\theta(x^{(i)}),y^{(i)})" />
<img src="https://latex.codecogs.com/gif.latex?Cost(h_\theta(x),y)=-log(h_\theta(x))\:\:\:\:\:\:\:\:\:\:if\:y=1" />
<img src="https://latex.codecogs.com/gif.latex?Cost(h_\theta(x),y)=-log(1-h_\theta(x))\:\:\:if\:y=0" />

* * *
When y = 1, we get the following plot for J(θ) vs hθ(x):

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Q9sX8nnxEeamDApmnD43Fw_1cb67ecfac77b134606532f5caf98ee4_Logistic_regression_cost_function_positive_class.png?expiry=1503619200000&amp;hmac=TUNAdL29O_uM96rNz-D_G6MihktOpDM82k39zn55v_U" alt="" data-asset-id="Q9sX8nnxEeamDApmnD43Fw">

Similarly, when y = 0, we get the following plot for J(θ) vs hθ(x):

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Ut7vvXnxEead-BJkoDOYOw_f719f2858d78dd66d80c5ec0d8e6b3fa_Logistic_regression_cost_function_negative_class.png?expiry=1503619200000&amp;hmac=HAB4anGYs5mG1V6eT0InKbqx3394G9ir8kWRdmmYZaw" alt="" data-asset-id="Ut7vvXnxEead-BJkoDOYOw">

* * *

<img src="https://latex.codecogs.com/gif.latex?Cost(h_\theta(x),y)=0:\if\:h_\theta(x)=y" />
<img src="https://latex.codecogs.com/gif.latex?Cost(h_\theta(x),y){\rightarrow}\infty\:if\:y=0{\:}and{\:}h_\theta(x){\rightarrow}1" />
<img src="https://latex.codecogs.com/gif.latex?Cost(h_\theta(x),y){\rightarrow}\infty\:if\:y=1{\:}and{\:}h_\theta(x){\rightarrow}0" />

* * *

If our correct answer 'y' is 0, then the cost function will be 0 if our hypothesis function also outputs 0. If our hypothesis approaches 1, then the cost function will approach infinity.

If our correct answer 'y' is 1, then the cost function will be 0 if our hypothesis function outputs 1. If our hypothesis approaches 0, then the cost function will approach infinity.

Note that writing the cost function in this way guarantees that J(θ) is convex for logistic regression.

## Simplified Cost Function and Gradient Descent

We can compress our cost function's two conditional cases into one case:

> <img src="https://latex.codecogs.com/gif.latex?Cost(h_\theta(x),y)=-ylog(h_\theta(x))-(1-y)log(1-h_\theta(x))" />

Notice that when y is equal to 1, then the second term (1−y)log(1−hθ(x)) will be zero and will not affect the result. If y is equal to 0, then the first term −ylog(hθ(x)) will be zero and will not affect the result.

We can fully write out our entire cost function as follows:

>

A vectorized implementation is:

> <img src="https://latex.codecogs.com/gif.latex?h=g(X\theta)" />  
> <p>
> <img src="https://latex.codecogs.com/gif.latex?J(\theta)=\frac{1}{m}\dot(-y^Tlog(h)-(1-y)^Tlog(1-h))" />

### Gradient Descent
Remember that the general form of gradient descent is:

> Repeat{
> 
> <img src="https://latex.codecogs.com/gif.latex?\theta_j:=\theta_j-\frac{\alpha}{m}\sum_{i=1}^m(h_\theta(x^{(i)})-y^{(i)})x_j^{(i)}" />
> 
> }

Notice that this algorithm is identical to the one we used in linear regression. We still have to simultaneously update all values in theta.

A vectorized implementation is:

<img src="https://latex.codecogs.com/gif.latex?\theta:=\theta-\frac{\alpha}{m}X^T(g(X\theta)-\vec{y})" />
