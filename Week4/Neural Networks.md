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

# Model Representation II

In this section we'll do a vectorized implementation of the above functions. We're going to define a new variable z(j)k that encompasses the parameters inside our g function. In our previous example if we replaced by the variable z for all the parameters we would get:

> <img src="https://latex.codecogs.com/gif.latex?a_1^{(2)}=g(z_1^{(2)})" />
> <p>
> <img src="https://latex.codecogs.com/gif.latex?a_2^{(2)}=g(z_2^{(2)})" />
> <p>
> <img src="https://latex.codecogs.com/gif.latex?a_3^{(2)}=g(z_3^{(2)})" />

In other words, for layer j=2 and node k, the variable z will be:

> <img src="https://latex.codecogs.com/gif.latex?z_k^{(2)}=\Theta_{k,0}^{(1)}x_0+\Theta_{k,1}^{(1)}x_1+...+\Theta_{k,n}^{(1)}x_n" /> 

The vector representation of x and zj is:

> <a href="https://www.codecogs.com/eqnedit.php?latex=x&space;=&space;\begin{bmatrix}x_0\\x_1\\...\\x_n\end{bmatrix}&space;z^{(j)}=\begin{bmatrix}z_1^{(j)}\\&space;z_2^{(j)}\\&space;...\\&space;z_n^{(j)}\end{bmatrix}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?x&space;=&space;\begin{bmatrix}x_0\\x_1\\...\\x_n\end{bmatrix}&space;z^{(j)}=\begin{bmatrix}z_1^{(j)}\\&space;z_2^{(j)}\\&space;...\\&space;z_n^{(j)}\end{bmatrix}" title="x = \begin{bmatrix}x_0\\x_1\\...\\x_n\end{bmatrix} z^{(j)}=\begin{bmatrix}z_1^{(j)}\\ z_2^{(j)}\\ ...\\ z_n^{(j)}\end{bmatrix}" /></a>

Setting x=a^(1), we can rewrite the equation as:

> <img src="https://latex.codecogs.com/gif.latex?z^{(j)}=\Theta^{(j-1)}a^{(j-1)}" />
 
We are multiplying our matrix Θ(j−1) with dimensions sj×(n+1) (where sj is the number of our activation nodes) by our vector a(j−1) with height (n+1). This gives us our vector z(j) with height sj. Now we can get a vector of our activation nodes for layer j as follows:

<img src="https://latex.codecogs.com/gif.latex?a^{(j)}=g(z^{(j)})" />

Where our function g can be applied element-wise to our vector <img src="https://latex.codecogs.com/gif.latex?z^{(j)}" />.

We can then add a bias unit (equal to 1) to layer j after we have computed <img src="https://latex.codecogs.com/gif.latex?a^{(j)}" />. This will be element <img src="https://latex.codecogs.com/gif.latex?a_0^{(j)}" /> and will be equal to 1. To compute our final hypothesis, let's first compute another z vector:

<img src="https://latex.codecogs.com/gif.latex?z^{(j+1)}=\Theta^{(j)}a^{(j)}" />

We get this final z vector by multiplying the next theta matrix after Θ(j−1) with the values of all the activation nodes we just got. This last theta matrix Θ(j) will have only one row which is multiplied by one column a(j) so that our result is a single number. We then get our final result with:

<img src="https://latex.codecogs.com/gif.latex?h_\Theta(x)=a^{(j+1)}=g(z^{(j+1)})" />

Notice that in this **last step**, between layer j and layer j+1, we are doing **exactly the same thing** as we did in logistic regression. Adding all these intermediate layers in neural networks allows us to more elegantly produce interesting and more complex non-linear hypotheses.






 
