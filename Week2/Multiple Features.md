Linear regression with multiple variables is also known as "multivariate linear regression".

We now introduce notation for equations where we can have any number of input variables.

> <p><img src="https://latex.codecogs.com/gif.latex?{x^{(i)}_j}="/> value of feature j in the ith training example</p>
> <p><img src="https://latex.codecogs.com/gif.latex?{x^{(i)}}="/> the input (features) of the ith training example</p>
> m = the number of training examples 
>
> n = the number of features

The multivariable form of the hypothesis function accommodating these multiple features is as follows:
> <p><img src="https://latex.codecogs.com/gif.latex?h_\theta(x)=\theta_0+\theta_1x_1+\theta_2x_2+\theta_3x_3+...+\theta_nx_n"/></p>

In order to develop intuition about this function, we can think about θ0 as the basic price of a house, θ1 as the price per square meter, θ2 as the price per floor, etc. x1 will be the number of square meters in the house, x2 the number of floors, etc.

Using the definition of matrix multiplication, our multivariable hypothesis function can be concisely represented as:

> <img src="https://latex.codecogs.com/gif.latex?h_\theta(x)&space;=&space;\begin{bmatrix}\theta_0&\theta_2&...&\theta_n\end{bmatrix}\begin{bmatrix}x_0\\x_1\\...\\x_n\end{bmatrix}&space;=&space;\theta^Tx"/>

This is a vectorization of our hypothesis function for one training example; see the lessons on vectorization to learn more.

Remark: Note that for convenience reasons in this course we assume x(i)0=1 for (i∈1,…,m). This allows us to do matrix operations with theta and x. Hence making the two vectors 'θ' and x(i) match each other element-wise (that is, have the same number of elements: n+1).]
