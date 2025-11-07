# 🧩 Curve-Fitting Assignment

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Tanish06122004/curve-fitting-assignment/blob/main/Untitled0.ipynb)

---

### 🎯 Assignment Overview
Assignment for **RandD / AI Internship**

Estimate the unknown parameters **θ**, **M**, and **X** in the following **parametric equations**:

$$
x(t) = t \cos(\theta) - e^{M|t|} \sin(0.3t)\sin(\theta) + X
$$

$$
y(t) = 42 + t \sin(\theta) + e^{M|t|} \sin(0.3t)\cos(\theta)
$$

for

$$
6 \le t \le 60
$$

---

### 🧮 Goal
Find parameters \( \theta, M, X \) that minimize the **L1 distance** between observed and predicted points.

---

### 🧾 Initial Estimate

If we ignore the sinusoidal term (set it ≈ 0), then:

$$
x \approx t \cos(\theta) + X, \quad y \approx 42 + t \sin(\theta)
$$

Therefore:

$$
y - 42 \approx t \sin(\theta), \quad x - X \approx t \cos(\theta)
$$

Dividing one by the other gives:

$$
\frac{y - 42}{x - X} \approx \tan(\theta)
$$

Thus, \( \theta \) can be estimated by fitting a **linear model** \( y = s x + b \) (ordinary least squares), and setting:

$$
s = \tan(\theta), \quad \theta = \arctan(s)
$$

From the intercept relation:

$$
b = 42 - \tan(\theta) \cdot X \quad \Rightarrow \quad X = \frac{42 - b}{\tan(\theta)}
$$

---

### ⚙️ Optimization Procedure

Given current global parameters \( \theta, M, X \):

- For each observed point, find the best-fitting \( t_i \) (bounded to [6, 60]) that minimizes the distance between the observed point and the parametric curve at \( t_i \).  
- Given those \( t_i \), optimize \( \theta, M, X \) to reduce the total L1/L2 residual.  
- Repeat until convergence.

Alternative: run a **global optimizer** (e.g. Differential Evolution) over \( \theta, M, X \), where the inner step estimates \( t_i \) for each candidate parameter set.

---

### 🧠 Optimization Objective (L1 Metric)

The assignment’s scoring is based on the **L1 distance** between uniformly sampled points of expected (observed) and predicted curves:

$$
L_1 = \sum_i \sqrt{(x_{obs,i} - x_{pred,i})^2 + (y_{obs,i} - y_{pred,i})^2}
$$

If the mapping between \( t \) and observed points is unknown, compute for each observed point the minimal distance to the predicted curve — or recover \( t \) for each point.

---

### 🧾 Final Results

| Parameter | Estimated Value |
|------------|-----------------|
| θ (degrees) | **29.9183°** |
| M | **0.029925** |
| X | **54.8704** |
| L1 Score | **98.97** |

---

### ✍️ Final Equation (LaTeX Format)

$$
x(t) = t \cos(0.52307)
- e^{0.029925|t|} \sin(0.3t)\sin(0.52307)
+ 54.8704
$$

$$
y(t) = 42 + t \sin(0.52307)
+ e^{0.029925|t|} \sin(0.3t)\cos(0.52307)
$$

---

### 📈 Visualization 
The fitted curve closely follows the observed data points, confirming accurate parameter estimation.

### 🧩 Implementation Details

- **Language:** Python 3  
- **Libraries:** `numpy`, `pandas`, `scipy`, `matplotlib`
- **Environment:** Google Colab  
- **Optimization Method:** L-BFGS-B (bounded minimization)  

---

### 📘 Key Equations Summary

1️⃣ Linear model:
$$
y = s x + b
$$

2️⃣ Angle and offset:
$$
\theta = \arctan(s), \quad X = \frac{42 - b}{\tan(\theta)}
$$

3️⃣ L1 Objective:
$$
L_1 = \sum_i |(x_{obs,i} - x_{pred,i})| + |(y_{obs,i} - y_{pred,i})|
$$

---




