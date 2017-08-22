# Normal Equation

Gradient descent gives one way of minimizing J. Let’s discuss a second way of doing so, this time performing the minimization explicitly and without resorting to an iterative algorithm. In the "Normal Equation" method, we will minimize J by explicitly taking its derivatives with respect to the θj ’s, and setting them to zero. This allows us to find the optimum theta without iteration. The normal equation formula is given below:  

<img src="https://latex.codecogs.com/gif.latex?\theta&space;=&space;(X^TX)^{-1}X^Ty" title="\theta = (X^TX)^{-1}X^Ty" />

<img src="https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/dykma6dwEea3qApInhZCFg_333df5f11086fee19c4fb81bc34d5125_Screenshot-2016-11-10-10.06.16.png?expiry=1503532800000&amp;hmac=BiFDAQDA8kYcAl_7L1ISnL3zqWwqIjXhpMfBjBnUKgc" alt="" data-asset-id="dykma6dwEea3qApInhZCFg">

There is **no need** to do feature scaling with the normal equation.

The following is a comparison of gradient descent and the normal equation:
<table>
	<tbody>
		<tr>
			<th>Gradient Descent</th>
			<th>Normal Equation</th>
		</tr>
		<tr>
			<td>Need to choose alpha</td>
			<td>No need to choose alpha</td>
		</tr>
		<tr>
			<td>Needs many iterations</td>
			<td>No need to iterate</td>
		</tr>
		<tr>
			<td><img src="https://latex.codecogs.com/gif.latex?O(kn^2)" /></td>
			<td><img src="https://latex.codecogs.com/gif.latex?O(n^3)" />,need to calculate inverse of<img src="https://latex.codecogs.com/gif.latex?X^TX" /></td>
		</tr>
		<tr>
			<td>Works well when n is large</td>
			<td>Slow if n is very large</td>
		</tr>
	</tbody>
</table>

With the normal equation, computing the inversion has complexity O(n3). So if we have a very large number of features, the normal equation will be slow. In practice, when n exceeds 10,000 it might be a good time to go from a normal solution to an iterative process.
