# curve-fitting-assignment
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
