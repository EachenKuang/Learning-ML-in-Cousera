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
