# Gradient Descent in Practice
## Feature Scaling
We can speed up gradient descent by having each of our input values in roughly the same range. This is because θ will descend quickly on small ranges and slowly on large ranges, and so will oscillate inefficiently down to the optimum when the variables are very uneven.

The way to prevent this is to modify the ranges of our input variables so that they are all roughly the same. Ideally:  
```
−1 ≤ x(i) ≤ 1  
or  
−0.5 ≤ x(i) ≤ 0.5  
```
These aren't exact requirements; we are only trying to speed things up. The goal is to get all input variables into roughly one of these ranges, give or take a few.

Two techniques to help with this are **feature scaling** and **mean normalizationZ**. Feature scaling involves dividing the input values by the range (i.e. the maximum value minus the minimum value) of the input variable, resulting in a new range of just 1. Mean normalization involves subtracting the average value for an input variable from the values for that input variable resulting in a new average value for the input variable of just zero. To implement both of these techniques, adjust your input values as shown in this formula:  
```
xi:=(xi−μi)/si
```
Where `μi` is the **average** of all the values for feature (i) and si is the range of values (max - min), or `si` is the standard deviation.

Note that dividing by the range, or dividing by the standard deviation, give different results. The quizzes in this course use range - the programming exercises use standard deviation.

For example, if `xi` represents housing prices with a range of 100 to 2000 and a mean value of 1000, then,  
```
xi:=(price−1000)/1900.
```
## Learning Rate
**Debugging gradient descent**. Make a plot with number of iterations on the x-axis. Now plot the cost function, J(θ) over the number of iterations of gradient descent. If J(θ) ever increases, then you probably need to decrease α.

**Automatic convergence test**. Declare convergence if J(θ) decreases by less than E in one iteration, where E is some small value such as 10−3. However in practice it's difficult to choose this threshold value.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/FEfS3aajEea3qApInhZCFg_6be025f7ad145eb0974b244a7f5b3f59_Screenshot-2016-11-09-09.35.59.png?expiry=1503532800000&amp;hmac=duAew6v6jKD-6TrmHlBFftuLq_cuyfpOsADcTh_iExU" alt="" data-asset-id="FEfS3aajEea3qApInhZCFg">

It has been proven that if learning rate α is sufficiently small, then J(θ) will decrease on every iteration.

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/rC2jGKgvEeamBAoLccicqA_ec9e40a58588382f5b6df60637b69470_Screenshot-2016-11-11-08.55.21.png?expiry=1503532800000&amp;hmac=GUI5N5wmW1SATy9DNcT2YA-HBK52JjfDIm0AwmeAJf4" alt="" data-asset-id="rC2jGKgvEeamBAoLccicqA">

To summarize:
- If `α` is too small: slow convergence.
- If `α` is too large: ￼may not decrease on every iteration and thus may not converge.
