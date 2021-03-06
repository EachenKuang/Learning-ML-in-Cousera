So we have our hypothesis function and we have a way of measuring how well it fits into the data. Now we need to estimate the parameters in the hypothesis function. That's where gradient descent comes in.

Imagine that we graph our hypothesis function based on its fields θ0 and θ1 (actually we are graphing the cost function as a function of the parameter estimates). We are not graphing x and y itself, but the parameter range of our hypothesis function and the cost resulting from selecting a particular set of parameters.

We put θ0 on the x axis and θ1 on the y axis, with the cost function on the vertical z axis. The points on our graph will be the result of the cost function using our hypothesis with those specific theta parameters. The graph below depicts such a setup.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/bn9SyaDIEeav5QpTGIv-Pg_0d06dca3d225f3de8b5a4a7e92254153_Screenshot-2016-11-01-23.48.26.png?expiry=1503446400000&amp;hmac=ulYCCp5ZmEeRNFTJNZFH9tqSBkqKCU0CXqnOyXhS4EQ" alt="" data-asset-id="bn9SyaDIEeav5QpTGIv-Pg">

We will know that we have succeeded when our cost function is at the very bottom of the pits in our graph, i.e. when its value is the minimum. The red arrows show the minimum points in the graph.

The way we do this is by taking the derivative (the tangential line to a function) of our cost function. The slope of the tangent is the derivative at that point and it will give us a direction to move towards. We make steps down the cost function in the direction with the steepest descent. The size of each step is determined by the parameter α, which is called the learning rate.

For example, the distance between each 'star' in the graph above represents a step determined by our parameter α. A smaller α would result in a smaller step and a larger α results in a larger step. The direction in which the step is taken is determined by the partial derivative of J(θ0,θ1). Depending on where one starts on the graph, one could end up at different points. The image above shows us two different starting points that end up in two different places.

The gradient descent algorithm is:

repeat until convergence:

<a href="https://www.codecogs.com/eqnedit.php?latex=\theta_j:=\theta_j-\alpha\frac{\partial&space;}{\partial&space;\theta_j}J(\theta_0,\theta_1)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\theta_j:=\theta_j-\alpha\frac{\partial&space;}{\partial&space;\theta_j}J(\theta_0,\theta_1)" title="\theta_j:=\theta_j-\alpha\frac{\partial }{\partial \theta_j}J(\theta_0,\theta_1)" /></a>

where

j=0,1 represents the feature index number.

At each iteration j, one should simultaneously update the parameters θ1,θ2,...,θn. Updating a specific parameter prior to calculating another one on the j(th) iteration would yield to a wrong implementation.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/yr-D1aDMEeai9RKvXdDYag_627e5ab52d5ff941c0fcc741c2b162a0_Screenshot-2016-11-02-00.19.56.png?expiry=1503446400000&amp;hmac=nHWAcCcSNAEycRvNLLoOe3DtrlR8Mt2qkuUCS5pwPpY" alt="" data-asset-id="yr-D1aDMEeai9RKvXdDYag">

