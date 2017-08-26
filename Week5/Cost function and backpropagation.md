# Cost Function

Let's first define a few variables that we will need to use:

* L = total number of layers in the network
* s_l = number of units (not counting bias unit) in layer l
* K = number of output units/classes

Recall that in neural networks, we may have many output nodes. We denote hΘ(x)k as being a hypothesis that results in the k^th output. Our cost function for neural networks is going to be a generalization of the one we used for logistic regression. Recall that the cost function for regularized logistic regression was:

> <img src="https://latex.codecogs.com/gif.latex?J(\theta)=-\frac{1}{m}\sum_{i=1}^m[y^{(i)}log(h_\theta(x^{(i)}))+(1-y^{(i)})log(1-h_\theta(x^{(i)}))]+\frac{\lambda}{2m}\sum_{j=1}^n\theta_j^2" />

For neural networks, it is going to be slightly more complicated:

> <img src="https://latex.codecogs.com/gif.latex?J(\Theta)=-\frac{1}{m}\sum_{i=1}^m\sum_{k=1}^K[y_k^{(i)}log(h_\Theta(x^{(i)}))_k+(1-y^{(i)}_k)log(1-h_\Theta(x^{(i)})_k_)]+\frac{\lambda}{2m}\sum_{l=1}^{L-1}\sum_{i=1}^{s_l}\sum_{j=1}^{s_l+1}(\Theta_{j,i}^{(l)})^2" />

We have added a few nested summations to account for our multiple output nodes. In the first part of the equation, before the square brackets, we have an additional nested summation that loops through the number of output nodes.

In the regularization part, after the square brackets, we must account for multiple theta matrices. The number of columns in our current theta matrix is equal to the number of nodes in our current layer (including the bias unit). The number of rows in our current theta matrix is equal to the number of nodes in the next layer (excluding the bias unit). As before with logistic regression, we square every term.

Note:

* the double sum simply adds up the logistic regression costs calculated for each cell in the output layer
* the triple sum simply adds up the squares of all the individual Θs in the entire network.
* the i in the triple sum does **not** refer to training example i

# Backpropagation Algorithm

"Backpropagation" is neural-network terminology for minimizing our cost function, just like what we were doing with gradient descent in logistic and linear regression. Our goal is to compute:

<img src="https://latex.codecogs.com/gif.latex?min_{\Theta}J(\Theta)" />

That is, we want to minimize our cost function J using an optimal set of parameters in theta. In this section we'll look at the equations we use to compute the partial derivative of J(Θ):

<img src="https://latex.codecogs.com/gif.latex?min_{\Theta}J(\Theta)" />

To do so, we use the following algorithm:

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/Ul6i5teoEea1UArqXEX_3g_a36fb24a11c744d7552f0fecf2fdd752_Screenshot-2017-01-10-17.13.27.png?expiry=1503878400000&amp;hmac=rCTKhoClpSPo1kMaycNY9SZAFTHdgkKByH5mda0Z5Ww" alt="" data-asset-id="Ul6i5teoEea1UArqXEX_3g">

### Back propagation Algorithm

Given training set **{(x(1),y(1))...(x(m),y(m))}**
Set Δ(l)i,j := 0 for all (l,i,j), (hence you end up having a matrix full of zeros)
For training example t =1 to m:

1. Set a(1):=x(t)
2. Perform forward propagation to compute a(l) for l=2,3,…,L 
<p>
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/bYLgwteoEeaX9Qr89uJd1A_73f280ff78695f84ae512f19acfa29a3_Screenshot-2017-01-10-18.16.50.png?expiry=1503878400000&amp;hmac=yIF-PA96aZBR_MXIj2QSD_P1IFDQLbSmjEjv4y73VZM" alt="" data-asset-id="bYLgwteoEeaX9Qr89uJd1A">

3. Using y(t), compute δ(L)=a(L)−y(t)<p>
Where L is our total number of layers and a(L) is the vector of outputs of the activation units for the last layer. So our "error values" for the last layer are simply the differences of our actual results in the last layer and the correct outputs in y. To get the delta values of the layers before the last layer, we can use an equation that steps us back from right to left:

4. Compute δ(L−1),δ(L−2),…,δ(2) using δ(l)=((Θ(l))Tδ(l+1)) .∗ a(l) .∗ (1−a(l))
The delta values of layer l are calculated by multiplying the delta values in the next layer with the theta matrix of layer l. We then element-wise multiply that with a function called g', or g-prime, which is the derivative of the activation function g evaluated with the input values given by z(l).

5. Δ(l)i,j:=Δ(l)i,j+a(l)jδ(l+1)i or with vectorization, Δ(l):=Δ(l)+δ(l+1)(a(l))T
Hence we update our new Δ matrix.


The g-prime derivative terms can also be written out as:
