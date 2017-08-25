# Model Representation I

Let's examine how we will represent a hypothesis function using neural networks. At a very simple level, neurons are basically computational units that take inputs (**dendrites**) as electrical inputs (called "spikes") that are channeled to outputs (**axons**). In our model, our dendrites are like the input features x1⋯xn, and the output is the result of our hypothesis function. In this model our x0 input node is sometimes called the "bias unit." It is always equal to 1. In neural networks, we use the same logistic function as in classification, 11+e−θTx, yet we sometimes call it a sigmoid (logistic) activation function. In this situation, our "theta" parameters are sometimes called "weights".

Visually, a simplistic representation looks like:

> <img src="https://latex.codecogs.com/gif.latex?\begin{bmatrix}&space;x_0\\&space;x_1\\&space;x_2&space;\end{bmatrix}\rightarrow&space;[\:&space;\:&space;\:&space;]\rightarrow&space;h_\theta(x)" />

Our input nodes (layer 1), also known as the "input layer", go into another node (layer 2), which finally outputs the hypothesis function, known as the "output layer".

We can have intermediate layers of nodes between the input and output layers called the "hidden layers."

In this example, we label these intermediate or "hidden" layer nodes a20⋯a2n and call them "activation units."

> <img src="https://latex.codecogs.com/gif.latex?a_i^{(j)}='activation'\;of\;unit\;i\;in\;layer\;j" />
> 
> Θ(j)=matrix of weights controlling function mapping from layer j to layer j+1

If we had one hidden layer, it would look like:

> <img src="https://latex.codecogs.com/gif.latex?a_i^{(j)}='activation'\;of\;unit\;i\;in\;layer\;j" />

The +1 comes from the addition in Θ(j) of the "bias nodes," x0 and Θ(j)0. In other words the output nodes will not include the bias nodes while the inputs will. The following image summarizes our model representation:

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/0rgjYLDeEeajLxLfjQiSjg_0c07c56839f8d6e8d7b0d09acedc88fd_Screenshot-2016-11-22-10.08.51.png?expiry=1503792000000&amp;hmac=VyBq2uTNaMWu4gp4m3I8Maoh6itVy-7e8y0f04aHz3k" alt="" data-asset-id="0rgjYLDeEeajLxLfjQiSjg">
