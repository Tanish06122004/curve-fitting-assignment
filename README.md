# curve-fitting-assignment

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Tanish06122004/curve-fitting-assignment/blob/main/Untitled0.ipynb)
Assignment for RandD / AI internship
estimate the unknowns theta, M, X
x(t)=tcosθ−eM∣t∣sin(0.3t)sinθ+X,
y(t)​=42+tsinθ+eM∣t∣sin(0.3t)cosθ,​
6<=t<=60
Goal: find 𝜃,𝑀,𝑋 that minimize L1 distance between observed and predicted points.
Initial estimate : If we ignore the sinusoidal term (set it ≈ 0), then:
x≈tcosθ+X, y≈42+tsinθ
y−42≈tsinθ, x−X≈tcosθ
(y−42​)/ (x−X)≈tanθ
Thus θ can be estimated by fitting a single linear model 𝑦=𝑠𝑥+𝑏 (ordinary least squares) and setting
s=tanθ, θ=arctan(s),
b=42−tanθ⋅X, X=(42-b)/tanθ
Given current global params θ,M,X, find for each observed point the best-fitting ti (1D minimization bounded to [6,60]) that minimizes distance between observed point and param curve at ti
Given those ti optimize θ,M,X to reduce total L1/L2 residual.
Repeat until convergence (or run a global optimizer like differential evolution over θ,M,X where inner step estimates ti for each candidate param set).
Optimization objective (L1 metric required)
Assignment scoring: L1 distance between uniformly sampled points of expected (observed) and predicted curves. Practical plan:
Use the observed points directly as the sampling set (if they are uniformly sampled in t, OK).
Or sample predicted curve at uniform t values (e.g. 1000 samples between 6 and 60) and compute L1 sum of Euclidean distances between corresponding points if you have a matching mapping of t to observed points.
If matching is unknown, compute for each observed point the minimal distance to the predicted curve — but better to recover t for each point.

 Final Results

Parameter Estimated Value 
θ (degrees) 29.9183°
M           0.029925
X           54.8704
L1 Score    98.97


Final Equation (LaTeX Format)

\[
(x, y) =
\left(
t\cos(0.52307)
- e^{0.029925|t|}\sin(0.3t)\sin(0.52307)
+ 54.8704,\;
42 + t\sin(0.52307)
+ e^{0.029925|t|}\sin(0.3t)\cos(0.52307)
\right)
\]

---

Visualization

The fitted curve closely follows the observed data points, confirming accurate parameter estimation.

