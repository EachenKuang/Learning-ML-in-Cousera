In this video we explored the scenario where we used one parameter θ1 and plotted its cost function to implement a gradient descent. Our formula for a single parameter was :

Repeat until convergence:

<img src="https://latex.codecogs.com/gif.latex?\theta_1:=\theta_1-\alpha\frac{\mathrm{d}}{\mathrm{d}&space;\theta_1}J(\theta_1)" >

Regardless of the slope's sign for 
<img src="https://latex.codecogs.com/gif.latex?\frac{\mathrm{d}&space;}{\mathrm{d}&space;\theta_1}J(\theta_1)"/>
, θ1 eventually converges to its minimum value. The following graph shows that when the slope is negative, the value of θ1 increases and when it is positive, the value of θ1 decreases.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/SMSIxKGUEeav5QpTGIv-Pg_ad3404010579ac16068105cfdc8e950a_Screenshot-2016-11-03-00.05.06.png?expiry=1503446400000&amp;hmac=ty_J_wjlCcIeIcWvvEMCanowngwneBCNx7l4mWJGQ5c" alt="" data-asset-id="SMSIxKGUEeav5QpTGIv-Pg">

On a side note, we should adjust our parameter α to ensure that the gradient descent algorithm converges in a reasonable time. Failure to converge or too much time to obtain the minimum value imply that our step size is wrong.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/UJpiD6GWEeai9RKvXdDYag_3c3ad6625a2a4ec8456f421a2f4daf2e_Screenshot-2016-11-03-00.05.27.png?expiry=1503446400000&amp;hmac=47gZBM7oM0fD_XdiTNXBHHq6juvzHnNNna6v1RwO9GY" alt="" data-asset-id="UJpiD6GWEeai9RKvXdDYag">

How does gradient descent converge with a fixed step size α?

The intuition behind the convergence is that 
<img src="https://latex.codecogs.com/gif.latex?\frac{\mathrm{d}&space;}{\mathrm{d}&space;\theta_1}J(\theta_1)"/>
approaches 0 as we approach the bottom of our convex function. At the minimum, the derivative will always be 0 and thus we get:  
> <img src="https://latex.codecogs.com/gif.latex?\theta_1:=\theta_1-\alpha*0"/>

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/RDcJ-KGXEeaVChLw2Vaaug_cb782d34d272321e88f202940c36afe9_Screenshot-2016-11-03-00.06.00.png?expiry=1503446400000&amp;hmac=F2TwQJHTHIWZVGBtWH3DkxZyVgJKao_revomj2t6Afk" alt="" data-asset-id="RDcJ-KGXEeaVChLw2Vaaug">
