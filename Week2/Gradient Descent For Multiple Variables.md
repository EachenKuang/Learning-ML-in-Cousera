# Gradient Descent For Multiple Variables
## Gradient Descent for Multiple Variables
The gradient descent equation itself is generally the same form; we just have to repeat it for our 'n' features:
******************************
repeat until convergence:{  
<img src="https://latex.codecogs.com/gif.latex?\theta_0:=\theta_0-\alpha{\frac{1}{m}}{\sum_{i=1}^{m}}(h_\theta(x^{(i)})-h^{(i)})\cdot&space;x_0^{(i)}"/>  
<img src="https://latex.codecogs.com/gif.latex?\theta_1:=\theta_1-\alpha{\frac{1}{m}}{\sum_{i=1}^{m}}(h_\theta(x^{(i)})-h^{(i)})\cdot&space;x_1^{(i)}"/>  
<img src="https://latex.codecogs.com/gif.latex?\theta_2:=\theta_2-\alpha{\frac{1}{m}}{\sum_{i=1}^{m}}(h_\theta(x^{(i)})-h^{(i)})\cdot&space;x_2^{(i)}"/>  
...  
}
******************************
In other words:
******************************  
repeat until convergence:{  
<img src="https://latex.codecogs.com/gif.latex?\theta_j:=\theta_j-\alpha{\frac{1}{m}}{\sum_{i=1}^{m}}(h_\theta(x^{(i)})-h^{(i)})\cdot&space;x_j^{(i)}"/>  
for j:=0...n  
}
******************************  
The following image compares gradient descent with one variable to gradient descent with multiple variables:
<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/MYm8uqafEeaZoQ7hPZtKqg_c974c2e2953662e9578b38c7b04591ed_Screenshot-2016-11-09-09.07.04.png?expiry=1503532800000&amp;hmac=BEaCGL2SCAEWf8J3mS--02ibXYURJ6DlNsxwQqdjcAY" alt="" data-asset-id="MYm8uqafEeaZoQ7hPZtKqg">
