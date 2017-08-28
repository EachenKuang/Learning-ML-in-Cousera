## Implementation Note: Unrolling Parameters

With neural networks, we are working with sets of matrices:
* * *
<img src="https://latex.codecogs.com/gif.latex?\Theta^{(1)},\Theta^{(2)},\Theta^{(3)},..."/>

<img src="https://latex.codecogs.com/gif.latex?D^{(1)},D^{(2)},D^{(3)},..." />
* * *
In order to use optimizing functions such as "fminunc()", we will want to "unroll" all the elements and put them into one long vector:
```
thetaVector = [ Theta1(:); Theta2(:); Theta3(:); ]
deltaVector = [ D1(:); D2(:); D3(:) ]
```
If the dimensions of Theta1 is 10x11, Theta2 is 10x11 and Theta3 is 1x11, then we can get back our original matrices from the "unrolled" versions as follows:
```
Theta1 = reshape(thetaVector(1:110),10,11)
Theta2 = reshape(thetaVector(111:220),10,11)
Theta3 = reshape(thetaVector(221:231),1,11)
```
To summarize:

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/kdK7ubT2EeajLxLfjQiSjg_d35545b8d6b6940e8577b5a8d75c8657_Screenshot-2016-11-27-15.09.24.png?expiry=1504051200000&amp;hmac=AuNS4q_Z8aD3-FzeDeWpELcXFwiYmKuqGN9s5blFaeE" alt="" data-asset-id="kdK7ubT2EeajLxLfjQiSjg">

## Gradient Checking
Gradient checking will assure that our backpropagation works as intended. We can approximate the derivative of our cost function with:
* * *
<img src="https://latex.codecogs.com/gif.latex?\frac{\partial }{\partial \Theta}J(\Theta)\approx\frac{J(\Theta+\epsilon)-J(\Theta-\epsilon)}{2\epsilon} "/> 
* * *
With multiple theta matrices, we can approximate the derivative **with respect to <img src="https://latex.codecogs.com/gif.latex?\Theta_j "/> ** as follows:
* * *
<img src="https://latex.codecogs.com/gif.latex?\frac{\partial }{\partial \Theta}J(\Theta)\approx\frac{J(\Theta_1,...,\Theta_j+\epsilon,...,\Theta_n)-J(\Theta_1,...,\Theta_j-\epsilon,...,\Theta_n)}{2\epsilon} "/> 
* * *
A small value for ** ϵ ** (epsilon) such as <img src="https://latex.codecogs.com/gif.latex?\mathbf{\epsilon^{-4}} "/> , guarantees that the math works out properly. If the value for **ϵ** is too small, we can end up with numerical problems.

Hence, we are only adding or subtracting epsilon to the <img src="https://latex.codecogs.com/gif.latex?\mathbf{\Theta_j} "/> matrix. In octave we can do it as follows:
```
epsilon = 1e-4;
for i = 1:n,
  thetaPlus = theta;
  thetaPlus(i) += epsilon;
  thetaMinus = theta;
  thetaMinus(i) -= epsilon;
  gradApprox(i) = (J(thetaPlus) - J(thetaMinus))/(2*epsilon)
end;
```
We previously saw how to calculate the deltaVector. So once we compute our gradApprox vector, we can check that gradApprox ≈ deltaVector.

Once you have verified **once** that your backpropagation algorithm is correct, you don't need to compute gradApprox again. The code to compute gradApprox can be very slow.

## Random Initialization

Initializing all theta weights to zero does not work with neural networks. When we backpropagate, all nodes will update to the same value repeatedly. Instead we can randomly initialize our weights for our Θ matrices using the following method:

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/y7gaS7pXEeaCrQqTpeD5ng_8868ccda2c387f5d481d0c54ab78a86e_Screen-Shot-2016-12-04-at-11.27.28-AM.png?expiry=1504051200000&amp;hmac=VYp-Mp499X4CL3jtRaTG3BcqyMVhuY9nAcsdHMZ-_fs" alt="" data-asset-id="y7gaS7pXEeaCrQqTpeD5ng">

Hence, we initialize each Θ(l)ij to a random value between[−ϵ,ϵ]. Using the above formula guarantees that we get the desired bound. The same procedure applies to all the Θ's. Below is some working code you could use to experiment.
```
If the dimensions of Theta1 is 10x11, Theta2 is 10x11 and Theta3 is 1x11.

Theta1 = rand(10,11) * (2 * INIT_EPSILON) - INIT_EPSILON;
Theta2 = rand(10,11) * (2 * INIT_EPSILON) - INIT_EPSILON;
Theta3 = rand(1,11) * (2 * INIT_EPSILON) - INIT_EPSILON;
```
rand(x,y) is just a function in octave that will initialize a matrix of random real numbers between 0 and 1.

(Note: the epsilon used above is unrelated to the epsilon from Gradient Checking)

