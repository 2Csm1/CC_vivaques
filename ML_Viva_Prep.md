# 🤖 Machine Learning — Complete Viva Preparation Guide
### Mumbai University | T.E. Sem VI | IA-1 + IA-2 + Experiments

> **Language is kept simple and easy to remember.**
> All numericals are solved step-by-step. Formulas are clearly boxed.
> 🔴 = Very likely to be asked in viva.

---

## TABLE OF CONTENTS

### IA-1
1. [Steps to Develop an ML Application](#ml-steps)
2. [Overfitting, Underfitting, Good Fit](#overfit)
3. [Diagonalization — Numerical](#diag)
4. [Singular Value Decomposition (SVD) — Numerical](#svd)
5. [Least Squares Line — Numerical](#least-sq)
6. [Support Vector Machine (SVM)](#svm)
7. [Confusion Matrix — Numericals](#confusion)
8. [Math Definitions — Norm, Trace, Determinant, etc.](#math-defs)
9. [Perpendicular Distance from Hyperplane — Numerical](#perp-dist)

### IA-2
10. [Biological vs Artificial Neural Network](#bio-ann)
11. [Expectation Maximization (EM) Algorithm](#em-algo)
12. [Hebbian Learning — OR Gate Solved](#hebb-or)
13. [Hebbian Learning — AND Gate Solved](#hebb-and)
14. [Activation Functions](#activation)
15. [McCulloch-Pitts Model — AND, NOT Solved](#mp-model)
16. [Single Layer Perceptron — OR Gate Solved (2 Epochs)](#perceptron)
17. [Backpropagation — Explanation + Equations](#backprop)
18. [Curse of Dimensionality & PCA](#pca-theory)
19. [PCA Numerical — Solved Step by Step](#pca-num)
20. [Feature Selection Methods](#feature-sel)

### Experiments
21. [All 9 Experiments Summary](#experiments)

### Quick Revision
22. [Formula Cheat Sheet](#formulas)

---

# ═══════════════════════════════
# IA-1 TOPICS
# ═══════════════════════════════

---

## 1. Steps to Develop an ML Application {#ml-steps}

### 🔴 Q. Explain the steps for developing a Machine Learning application.

Think of it as: **Problem → Data → Model → Evaluate → Deploy**

```
Step 1: Define the Problem
     ↓
Step 2: Collect Data
     ↓
Step 3: Prepare / Clean Data
     ↓
Step 4: Choose a Model
     ↓
Step 5: Train the Model
     ↓
Step 6: Evaluate the Model
     ↓
Step 7: Tune (Improve) the Model
     ↓
Step 8: Deploy & Monitor
```

**Step 1 — Define the Problem:**
- What are you trying to predict or classify?
- Is it regression (number) or classification (category)?
- Example: "Predict house price" or "Spam or Not Spam?"

**Step 2 — Collect Data:**
- Gather data from databases, APIs, web scraping, surveys
- The more relevant data, the better the model

**Step 3 — Prepare / Clean Data:**
- Remove missing values
- Remove duplicates
- Fix wrong data types
- Feature Engineering (create new useful columns)
- Normalize/Standardize values

**Step 4 — Exploratory Data Analysis (EDA):**
- Plot histograms, boxplots, scatter plots
- Understand distributions and relationships
- Find correlations between features

**Step 5 — Choose a Model:**
- Regression → Linear Regression, SVR
- Classification → Logistic Regression, SVM, Decision Tree
- Clustering → K-Means

**Step 6 — Train the Model:**
- Split data: 80% train, 20% test
- Fit the model on training data

**Step 7 — Evaluate the Model:**
- Regression: RMSE, MAE, R²
- Classification: Accuracy, Precision, Recall, F1, Confusion Matrix

**Step 8 — Tune / Improve:**
- Cross-validation (k-fold)
- Hyperparameter tuning (GridSearchCV)
- Try different algorithms

**Step 9 — Deploy & Monitor:**
- Save model (pickle/joblib in Python)
- Deploy as API (Flask/FastAPI)
- Monitor for data drift over time

---

## 2. Overfitting, Underfitting, Good Fit {#overfit}

### 🔴 Q. A model performs poorly on both training and test data. Another performs well on training but poorly on test. Identify overfitting, underfitting, and good fit.

**Answer:**

| Scenario | Training Error | Test Error | Problem | Cause |
|---|---|---|---|---|
| Poor on BOTH | High | High | **Underfitting** | Model too simple |
| Good train, poor test | Low | High | **Overfitting** | Model too complex |
| Good on BOTH | Low | Low | **Good Fit** | Just right! |

**Underfitting (High Bias):**
- Model is too simple to learn patterns
- Like using a straight line to fit curved data
- Fix: Use a more complex model, add more features

**Overfitting (High Variance):**
- Model memorizes training data including noise
- Performs great on training, fails on new data
- Fix: Get more data, apply regularization (L1/L2), use simpler model, dropout

**Good Fit:**
- Model learns the pattern, not the noise
- Generalizes well to new data

```
Think of it like studying for exams:
- Underfitting = didn't study at all → fail both mock and real exam
- Overfitting = memorized mock exam answers → ace mock but fail real exam
- Good Fit = understood concepts → do well everywhere
```

---

## 3. Diagonalization — Numerical {#diag}

### 🔴 Q. Diagonalize A = [[2, 2], [1, 3]]

**What is Diagonalization?**
Finding matrices P and D such that: **A = P × D × P⁻¹**
Where D is a diagonal matrix with eigenvalues, and P contains eigenvectors.

**Step 1: Find Eigenvalues**
Solve: det(A − λI) = 0

```
A - λI = | 2-λ  2  |
         | 1    3-λ |
```

det = (2−λ)(3−λ) − (2×1) = 0
= 6 − 2λ − 3λ + λ² − 2 = 0
= **λ² − 5λ + 4 = 0**
= (λ−1)(λ−4) = 0

**λ₁ = 1, λ₂ = 4**

---

**Step 2: Find Eigenvectors**

**For λ₁ = 1:** Solve (A − I)v = 0
```
| 1  2 | |v₁|   |0|
| 1  2 | |v₂| = |0|
```
v₁ + 2v₂ = 0 → v₁ = −2v₂
Let v₂ = 1 → **v₁ = [−2, 1]ᵀ**

**For λ₂ = 4:** Solve (A − 4I)v = 0
```
| -2  2 | |v₁|   |0|
|  1 -1 | |v₂| = |0|
```
−2v₁ + 2v₂ = 0 → v₁ = v₂
Let v₂ = 1 → **v₂ = [1, 1]ᵀ**

---

**Step 3: Write P and D**

```
P = | -2  1 |    D = | 1  0 |
    |  1  1 |        | 0  4 |
```

**Result: A = P × D × P⁻¹**

The diagonal matrix D has eigenvalues on the diagonal.

---

## 4. Singular Value Decomposition (SVD) {#svd}

### 🔴 Q. For A = [[1, 1], [7, 7]], find: a) Singular values, b) Right singular matrix, c) Left singular matrix

**SVD: A = U × Σ × Vᵀ**
- **U** = Left singular matrix (eigenvectors of AAᵀ)
- **Σ** = Diagonal matrix of singular values (σ = √eigenvalue)
- **V** = Right singular matrix (eigenvectors of AᵀA)

---

**Step 1: Calculate AᵀA**

```
Aᵀ = | 1  7 |    AᵀA = | 1  7 | × | 1  1 | = | 50  50 |
     | 1  7 |           | 1  7 |   | 7  7 |   | 50  50 |
```

---

**Step 2: Find Eigenvalues of AᵀA(singular values)**

det(AᵀA − λI) = 0
(50−λ)² − 50² = 0
(50−λ)² = 2500
50−λ = ±50

**λ₁ = 100, λ₂ = 0**

**a) Singular Values:**
```
σ₁ = √100 = 10
σ₂ = √0   = 0

Σ = | 10  0 |
    |  0  0 |
```

---

**Step 3: b) Right Singular Matrix V (eigenvectors of AᵀA)**

**For λ₁ = 100:** (AᵀA − 100I)v = 0
```
| -50  50 | v = 0
|  50 -50 |
```
−50v₁ + 50v₂ = 0 → v₁ = v₂
Normalized: **v₁ = [1/√2, 1/√2]ᵀ**

**For λ₂ = 0:** (AᵀA)v = 0
```
| 50  50 | v = 0
| 50  50 |
```
50v₁ + 50v₂ = 0 → v₁ = −v₂
Normalized: **v₂ = [1/√2, −1/√2]ᵀ**

```
          | 1/√2   1/√2 |
b) V =    | 1/√2  -1/√2 |
```

---

**Step 4: c) Left Singular Matrix U (eigenvectors of AAᵀ)**

```
AAᵀ = | 1  1 | × | 1  7 | = |  2   14 |
      | 7  7 |   | 1  7 |   | 14   98 |
```

Eigenvalues of AAᵀ: same non-zero eigenvalues as AᵀA → **λ₁=100, λ₂=0**

**For λ₁ = 100:** (AAᵀ − 100I)v = 0
```
| -98  14 | v = 0
|  14  -2 |
```
14v₂ − 98v₁ = 0*  → v₂ = 7v₁
Normalized: v₁ = 1/√50, v₂ = 7/√50 → **u₁ = [1/√50, 7/√50]ᵀ**

**For λ₂ = 0:** AAᵀ v = 0
v₁ = −7v₂ → **u₂ = [−7/√50, 1/√50]ᵀ**

```
            | 1/√50   -7/√50 |
c) U =      | 7/√50    1/√50 |
```

---

## 5. Least Squares Straight Line — Numerical {#least-sq}

### 🔴 Q. Find the least square straight line for: x: 1,2,3,4,5,6 | y: 6,4,3,5,4,2. Estimate y at x=4.

**Formula for least squares line: y = a + bx**

```
b = (n·Σxy − Σx·Σy) / (n·Σx² − (Σx)²)

a = (Σy − b·Σx) / n
```

**Step 1: Calculate required sums (n=6)**

| x | y | x²| xy |
|---|---|---|---|
| 1 | 6 | 1 | 6 |
| 2 | 4 | 4 | 8 |
| 3 | 3 | 9 | 9 |
| 4 | 5 | 16| 20|
| 5 | 4 | 25| 20|
| 6 | 2 | 36| 12|
|**Σx=21**|**Σy=24**|**Σx²=91**|**Σxy=75**|

**Step 2: Calculate b (slope)**

```
b = (6×75 − 21×24) / (6×91 − 21²)
b = (450 − 504) / (546 − 441)
b = −54 / 105
b = −0.514
```

**Step 3: Calculate a (intercept)**

```
a = (24 − (−0.514)×21) / 6
a = (24 + 10.8) / 6
a = 34.8 / 6
a = 5.8
```

**Least Squares Line: y = 5.8 − 0.514x**

**Step 4: Estimate y at x = 4**

```
y = 5.8 − 0.514 × 4
y = 5.8 − 2.057
y ≈ 3.74
```

---

## 6. Support Vector Machine (SVM) {#svm}

### 🔴 Q. Write a short note on SVM.

**What is SVM?**
SVM is a classification algorithm that finds the **best hyperplane** (boundary line) that separates two classes with the **maximum margin**.

```
Think of two groups of points on a paper.
SVM draws the line that is:
- Furthest away from BOTH groups
- Has equal distance from the closest points of each group
```

**Key Terms:**

| Term | Meaning |
|---|---|
| **Hyperplane** | The decision boundary (line in 2D, plane in 3D) |
| **Support Vectors** | The data points closest to the hyperplane — they "support" it |
| **Margin** | Distance between the hyperplane and the nearest support vectors |
| **Maximum Margin** | SVM maximizes this margin → better generalization |

**Equation of Hyperplane:**
```
w·x + b = 0
Where: w = weight vector, x = input, b = bias
```

**Classification Rule:**
```
If w·x + b ≥ +1 → Class +1
If w·x + b ≤ −1 → Class −1
```

**Margin:**
```
Margin = 2 / ||w||
SVM objective: Maximize margin = Minimize ||w||
```

**Kernel Trick:**
For non-linearly separable data, SVM uses a **kernel function** to map data to a higher dimension where it becomes linearly separable.

| Kernel | Use case |
|---|---|
| Linear | Data is linearly separable |
| Polynomial | Curved boundaries |
| RBF (Gaussian) | Most common — works for most cases |

**Types of SVM:**
- **Hard Margin SVM** — No misclassification allowed (only if data is perfectly separable)
- **Soft Margin SVM** — Allows some misclassifications (real-world data). Uses slack variable ξ

**Advantages:**
- Works well in high dimensions
- Effective when #features > #samples
- Memory efficient (only support vectors matter)

**Disadvantages:**
- Slow for large datasets
- Sensitive to feature scaling

---

## 7. Confusion Matrix — Numericals {#confusion}

### 🔴 Q. Numericals on Confusion Matrix.

**What is a Confusion Matrix?**
A table that shows how many predictions were correct/wrong for a classification model.

```
                      Predicted
                  Positive    Negative
Actual  Positive |    TP    |    FN   |
        Negative |    FP    |    TN   |

TP = True Positive  (predicted +, actual +)
TN = True Negative  (predicted −, actual −)
FP = False Positive (predicted +, actual −)  ← Type I Error
FN = False Negative (predicted −, actual +)  ← Type II Error
```

**All Formulas:**

```
Accuracy    = (TP + TN) / (TP + TN + FP + FN)

Precision   = TP / (TP + FP)   ← How many predicted + are actually +?

Recall      = TP / (TP + FN)   ← How many actual + did we catch?
(Sensitivity)

Specificity = TN / (TN + FP)   ← How many actual − did we correctly identify?

F1-Score    = 2 × (Precision × Recall) / (Precision + Recall)

Error Rate  = 1 − Accuracy = (FP + FN) / Total
```

---

**Solved Example:**
Confusion matrix for 100 patients (cancer detection):

```
                Predicted Cancer   Predicted No Cancer
Actual Cancer       |  40  |             10           |
Actual No Cancer    |  15  |             35           |
```

TP=40, FN=10, FP=15, TN=35, Total=100

```
Accuracy    = (40+35)/100 = 75/100 = 0.75 = 75%

Precision   = 40/(40+15) = 40/55 = 0.727 = 72.7%

Recall      = 40/(40+10) = 40/50 = 0.80 = 80%

F1-Score    = 2×(0.727×0.80)/(0.727+0.80) = 2×0.582/1.527 = 0.762 = 76.2%

Specificity = 35/(35+15) = 35/50 = 0.70 = 70%
```

---

## 8. Math Definitions {#math-defs}

### 🔴 Q. Define: Norm, Determinant, Length of Vector, Orthogonal Vectors, Trace of Matrix.

**1. Norm of a Vector**
The norm measures the **"size" or "length"** of a vector.

For vector v = [v₁, v₂, ..., vₙ]:
```
||v|| = √(v₁² + v₂² + v₃² + ... + vₙ²)
```

Example: v = [3, 4]
||v|| = √(9+16) = √25 = **5**

---

**2. Length of a Vector**
Same as norm: ||v|| = √(Σvᵢ²)
It's the Euclidean distance from the origin to the point v.

---

**3. Determinant of a Matrix**
For 2×2 matrix:
```
A = | a  b |     det(A) = ad − bc
    | c  d |
```

Example: A = [[2,3],[1,4]]
det(A) = 2×4 − 3×1 = 8 − 3 = **5**

**What it tells you:**
- det = 0 → Matrix is singular (no inverse)
- det ≠ 0 → Matrix is invertible

---

**4. Orthogonal Vectors**
Two vectors are **orthogonal** if their dot product = 0 (they are perpendicular to each other).

```
u · v = u₁v₁ + u₂v₂ + ... = 0  → orthogonal
```

Example: u = [1, 0], v = [0, 1]
u · v = 1×0 + 0×1 = **0** → orthogonal ✓

---

**5. Trace of a Matrix**
Trace = **sum of diagonal elements**

```
trace(A) = a₁₁ + a₂₂ + a₃₃ + ...
```

Example: A = [[2,3],[1,4]]
trace(A) = 2 + 4 = **6**

**Also:** trace(A) = sum of all eigenvalues

---

## 9. Perpendicular Distance from a Hyperplane {#perp-dist}

### 🔴 Q. For hyperplane 2x + 3y − 3 = 0 and point P(4, 2), find perpendicular distance.

**Formula:**
```
For hyperplane: ax + by + c = 0
Point: (x₀, y₀)

Distance = |a·x₀ + b·y₀ + c| / √(a² + b²)
```

**Step 1: Identify values**
```
Hyperplane: 2x + 3y − 3 = 0
  a=2, b=3, c=−3
Point P(4, 2):
  x₀=4, y₀=2
```

**Step 2: Apply formula**
```
Distance = |2×4 + 3×2 + (−3)| / √(2² + 3²)
         = |8 + 6 − 3| / √(4 + 9)
         = |11| / √13
         = 11 / 3.606
         = 3.05 units
```

**Answer: Distance = 11/√13 ≈ 3.05 units**

> In SVM, this is how we calculate the distance of a data point from the decision boundary. The support vectors are the points with the smallest such distance.

---

# ═══════════════════════════════
# IA-2 TOPICS
# ═══════════════════════════════

---

## 10. Biological vs Artificial Neural Network {#bio-ann}

### 🔴 Q. Draw and explain biological neural networks and compare with artificial neural networks.

**Biological Neural Network (BNN):**
The human brain has ~86 billion neurons connected by synapses.

```
Structure of a Biological Neuron:

Dendrites (receive signals)
     ↓
Cell Body / Soma (processes signals)
     ↓
Axon (transmits output signal)
     ↓
Synaptic Terminals (send to next neuron)
```

How it works:
- Dendrites receive electrical/chemical signals from other neurons
- Cell body sums up all incoming signals
- If the total exceeds a threshold → fires a signal down the axon
- Signal passes to next neuron through synapses

---

**Artificial Neural Network (ANN):**
A mathematical model inspired by the brain.

```
Structure of an Artificial Neuron:

Inputs (x₁, x₂, ..., xₙ)
     ↓  each multiplied by a weight (w₁, w₂, ...)
Summation: NET = Σ(wᵢ × xᵢ) + bias
     ↓
Activation Function f(NET)
     ↓
Output y
```

---

**Comparison Table: BNN vs ANN**

| Feature | Biological Neuron | Artificial Neuron |
|---|---|---|
| **Basic unit** | Neuron | Perceptron / Node |
| **Input** | Dendrites | Input features (x₁, x₂...) |
| **Processing** | Cell body | Weighted sum + activation |
| **Output** | Axon | Output y |
| **Connection** | Synapse | Weights (w) |
| **Learning** | Synaptic plasticity | Weight adjustment |
| **Speed** | Slow (ms) | Very fast (ns) |
| **Fault tolerance** | High | Low |
| **Power consumption** | Very low (~20W) | High (GPU = 300W+) |
| **Parallelism** | Massively parallel | Limited |
| **Memory** | Distributed in structure | Stored separately |

---

## 11. Expectation Maximization (EM) Algorithm {#em-algo}

### Q. Write a short note on the Expectation Maximization (EM) algorithm.

**What is EM?**
EM is an **iterative algorithm** used to find parameters when some data is **missing or hidden (latent)**. It alternates between two steps until convergence.

**When to use:**
- Gaussian Mixture Models (clustering)
- When you have incomplete data

**Two Steps:**

```
Step 1: E-Step (Expectation)
  → Estimate the missing/hidden data using current parameter guesses
  → Calculate the probability that each data point belongs to each cluster

Step 2: M-Step (Maximization)
  → Update the model parameters by maximizing
    the likelihood based on the E-step estimates
  → Recalculate means, variances, mixing coefficients

Repeat until parameters stop changing (convergence)
```

**Simple Example (GMM Clustering):**
Imagine you have heights of men and women mixed together (you don't know who is who).

- E-Step: For each height, estimate the probability it came from men's group or women's group
- M-Step: Update mean height and variance for men's group and women's group separately
- Repeat until stable

**Key Property:**
- EM **always converges** (never makes the likelihood worse)
- May converge to a **local maximum**, not global maximum

---

## 12. Hebbian Learning — OR Gate {#hebb-or}

### 🔴 Q. Explain Hebbian Learning Rule. Design a Hebb net to implement OR function (bipolar inputs and targets).

**Hebbian Learning Rule:**
"Neurons that fire together, wire together."

If input and output are both active at the same time → **strengthen the connection (increase weight)**.

**Formula:**
```
Δwᵢ = learning_rate × xᵢ × y
Δb  = learning_rate × 1 × y

New wᵢ = old wᵢ + Δwᵢ
```

For standard Hebbian Learning, learning rate = 1, so:
```
Δwᵢ = xᵢ × y
Δb  = y
```

**No threshold checking** in Hebbian — just update weights for every input.

---

**OR Gate — Bipolar Truth Table:**
(Binary 0 → replaced by Bipolar −1)

| x₁ | x₂ | Target y |
|---|---|---|
| −1 | −1 | −1 |
| −1 | +1 | +1 |
| +1 | −1 | +1 |
| +1 | +1 | +1 |

**Initial weights:** w₁=0, w₂=0, b=0

---

**Training (one pass through all inputs):**

**Input 1:** x₁=−1, x₂=−1, y=−1
```
Δw₁ = x₁×y = (−1)(−1) = +1  → w₁ = 0+1 = 1
Δw₂ = x₂×y = (−1)(−1) = +1  → w₂ = 0+1 = 1
Δb  =   1×y = (1)(−1)  = −1  → b  = 0−1 = −1
```

**Input 2:** x₁=−1, x₂=+1, y=+1
```
Δw₁ = (−1)(+1) = −1  → w₁ = 1−1 = 0
Δw₂ = (+1)(+1) = +1  → w₂ = 1+1 = 2
Δb  = (+1)     = +1  → b  = −1+1 = 0
```

**Input 3:** x₁=+1, x₂=−1, y=+1
```
Δw₁ = (+1)(+1) = +1  → w₁ = 0+1 = 1
Δw₂ = (−1)(+1) = −1  → w₂ = 2−1 = 1
Δb  = (+1)     = +1  → b  = 0+1 = 1
```

**Input 4:** x₁=+1, x₂=+1, y=+1
```
Δw₁ = (+1)(+1) = +1  → w₁ = 1+1 = 2
Δw₂ = (+1)(+1) = +1  → w₂ = 1+1 = 2
Δb  = (+1)     = +1  → b  = 1+1 = 2
```

**Final Weights: w₁ = 2, w₂ = 2, b = 2**

---

## 13. Hebbian Learning — AND Gate {#hebb-and}

### 🔴 Q. Design Hebb net for AND gate (bipolar inputs and targets).

**AND Gate — Bipolar Truth Table:**

| x₁ | x₂ | Target y |
|---|---|---|
| −1 | −1 | −1 |
| −1 | +1 | −1 |
| +1 | −1 | −1 |
| +1 | +1 | +1 |

**Initial weights:** w₁=0, w₂=0, b=0

**Training:**

**Input 1:** x₁=−1, x₂=−1, y=−1
```
Δw₁ = (−1)(−1) = +1  → w₁ = 1
Δw₂ = (−1)(−1) = +1  → w₂ = 1
Δb  = (1)(−1)  = −1  → b  = −1
```

**Input 2:** x₁=−1, x₂=+1, y=−1
```
Δw₁ = (−1)(−1) = +1  → w₁ = 2
Δw₂ = (+1)(−1) = −1  → w₂ = 0
Δb  = (1)(−1)  = −1  → b  = −2
```

**Input 3:** x₁=+1, x₂=−1, y=−1
```
Δw₁ = (+1)(−1) = −1  → w₁ = 1
Δw₂ = (−1)(−1) = +1  → w₂ = 1
Δb  = (1)(−1)  = −1  → b  = −3
```

**Input 4:** x₁=+1, x₂=+1, y=+1
```
Δw₁ = (+1)(+1) = +1  → w₁ = 2
Δw₂ = (+1)(+1) = +1  → w₂ = 2
Δb  = (1)(+1)  = +1  → b  = −2
```

**Final Weights: w₁ = 2, w₂ = 2, b = −2**

**Assumption:** Initial weights and bias = 0. Learning rate = 1.

---

## 14. Activation Functions {#activation}

### 🔴 Q. What are activation functions? Explain Binary, Bipolar, Continuous (Sigmoid) & Ramp (ReLU) activation functions.

**What is an Activation Function?**
It decides whether a neuron should "fire" (activate) or not based on the net input.

```
net input = Σ(wᵢ × xᵢ) + b
Output y = f(net)
```

---

**1. Binary Step Function (Hard Limiter)**
```
         ⎧  1  if net ≥ θ (threshold)
f(net) = ⎨
         ⎩  0  if net < θ
```

**Graph:**
```
y
1 |___________
  |
0 |___________
          θ    → net
```

**Range:** {0, 1}
**Use:** Basic threshold decisions

---

**2. Bipolar Step Function (Sign Function)**
```
         ⎧ +1  if net > 0
f(net) = ⎨  0  if net = 0
         ⎩ −1  if net < 0
```

**Graph:**
```
y
+1 |___________
   |
 0 |-----
   |
-1 |___________
         0      → net
```

**Range:** {−1, 0, +1}
**Use:** Hebbian learning, bipolar representations

---

**3. Sigmoid (Continuous / Logistic)**
```
f(net) = 1 / (1 + e^(−net))
```

**Graph:** S-shaped (smooth curve)
```
y
1 |         .....----
  |       .
0.5|------
  |     .
0 |-----.....
         0        → net
```

**Range:** (0, 1) — never exactly 0 or 1, smooth gradient
**Derivative:** f'(x) = f(x) × (1 − f(x)) ← used in backpropagation
**Use:** Hidden layers in neural networks, logistic regression

---

**4. ReLU / Ramp Function**
```
         ⎧  net  if net > 0
f(net) = ⎨
         ⎩   0   if net ≤ 0
```

**Graph:**
```
y
  |        /
  |       /
  |      /
  |     /
0 |------→ net
```

**Range:** [0, ∞)
**Use:** Hidden layers in deep neural networks (most popular today)
**Advantage over sigmoid:** No vanishing gradient for positive values, computationally simple

---

**Summary Table:**

| Function | Formula | Range | Graph |
|---|---|---|---|
| Binary Step | 1 if net≥θ, else 0 | {0, 1} | Step up at θ |
| Bipolar Step | +1/0/−1 | {−1, 0, +1} | Two steps |
| Sigmoid | 1/(1+e^−net) | (0, 1) | S-curve |
| ReLU | max(0, net) | [0, ∞) | Ramp from 0 |

---

## 15. McCulloch-Pitts Model {#mp-model}

### 🔴 Q. Implement AND and NOT functions using McCulloch-Pitts Algorithm.

**What is McCulloch-Pitts Model?**
It's the simplest artificial neuron (1943). Works on binary inputs (0 or 1).

**Rule:**
```
net = Σ(wᵢ × xᵢ)

         ⎧  1  if net ≥ θ (threshold)
Output = ⎨
         ⎩  0  if net < θ
```

- **Excitatory connection:** w = +1 (promotes firing)
- **Inhibitory connection:** w = −1 (prevents firing)
- Any inhibitory input active → output is always 0

---

**A) AND Gate — McCulloch Pitts**

**Setup:** 2 inputs x₁, x₂
Weights: w₁ = 1, w₂ = 1
Threshold: **θ = 2** (need BOTH inputs = 1 to fire)

**Truth Table Verification:**

| x₁ | x₂ | net = x₁+x₂ | net ≥ θ=2? | Output |
|---|---|---|---|---|
| 0 | 0 | 0 | No  | **0** ✓ |
| 0 | 1 | 1 | No  | **0** ✓ |
| 1 | 0 | 1 | No  | **0** ✓ |
| 1 | 1 | 2 | Yes | **1** ✓ |

**AND gate implemented correctly!**

---

**B) NOT Gate — McCulloch Pitts**

**Setup:** 1 input x (inhibitory)
Weight: **w = −1** (inhibitory)
Threshold: **θ = 0**

**Truth Table Verification:**

| x | net = −1×x | net ≥ θ=0? | Output |
|---|---|---|---|
| 0 | 0 | Yes | **1** ✓ |
| 1 | −1| No  | **0** ✓ |

**NOT gate implemented correctly!**

---

## 16. Single Layer Perceptron — OR Gate {#perceptron}

### 🔴 Q. Implement OR function (2 epochs). Assume: w₁=w₂=b=0, threshold=0.2, learning rate=1.

**Perceptron Learning Rule:**
```
Compute output: ŷ = 1 if net ≥ θ, else 0
               where net = w₁x₁ + w₂x₂ + b

If ŷ ≠ target → update weights:
  Δwᵢ = η × (target − ŷ) × xᵢ
  Δb   = η × (target − ŷ)
```

**OR Gate — Binary Truth Table:**

| x₁ | x₂ | Target |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 1 |

**Initial:** w₁=0, w₂=0, b=0, θ=0.2, η=1

---

**═ EPOCH 1 ═**

**Input 1:** x₁=0, x₂=0, Target=0
```
net = 0×0 + 0×0 + 0 = 0
ŷ = 0 (since 0 < 0.2)
Target=0, ŷ=0 → No error → NO UPDATE
w₁=0, w₂=0, b=0
```

**Input 2:** x₁=0, x₂=1, Target=1
```
net = 0×0 + 0×1 + 0 = 0
ŷ = 0 (since 0 < 0.2)
Target=1, ŷ=0 → Error! → UPDATE
  Δw₁ = 1×(1−0)×0 = 0   → w₁ = 0+0 = 0
  Δw₂ = 1×(1−0)×1 = 1   → w₂ = 0+1 = 1
  Δb  = 1×(1−0)   = 1   → b  = 0+1 = 1
```

**Input 3:** x₁=1, x₂=0, Target=1
```
net = 0×1 + 1×0 + 1 = 1
ŷ = 1 (since 1 ≥ 0.2)
Target=1, ŷ=1 → No error → NO UPDATE
w₁=0, w₂=1, b=1
```

**Input 4:** x₁=1, x₂=1, Target=1
```
net = 0×1 + 1×1 + 1 = 2
ŷ = 1 (since 2 ≥ 0.2)
Target=1, ŷ=1 → No error → NO UPDATE
w₁=0, w₂=1, b=1
```

**End of Epoch 1: w₁=0, w₂=1, b=1**

---

**═ EPOCH 2 ═**

**Input 1:** x₁=0, x₂=0, Target=0
```
net = 0×0 + 1×0 + 1 = 1
ŷ = 1 (since 1 ≥ 0.2)
Target=0, ŷ=1 → Error! → UPDATE
  Δw₁ = 1×(0−1)×0 = 0   → w₁ = 0
  Δw₂ = 1×(0−1)×0 = 0   → w₂ = 1
  Δb  = 1×(0−1)   = −1  → b  = 1−1 = 0
```

**Input 2:** x₁=0, x₂=1, Target=1
```
net = 0×0 + 1×1 + 0 = 1
ŷ = 1 (since 1 ≥ 0.2)
Target=1, ŷ=1 → No error → NO UPDATE
w₁=0, w₂=1, b=0
```

**Input 3:** x₁=1, x₂=0, Target=1
```
net = 0×1 + 1×0 + 0 = 0
ŷ = 0 (since 0 < 0.2)
Target=1, ŷ=0 → Error! → UPDATE
  Δw₁ = 1×(1−0)×1 = 1   → w₁ = 0+1 = 1
  Δw₂ = 1×(1−0)×0 = 0   → w₂ = 1
  Δb  = 1×(1−0)   = 1   → b  = 0+1 = 1
```

**Input 4:** x₁=1, x₂=1, Target=1
```
net = 1×1 + 1×1 + 1 = 3
ŷ = 1 (since 3 ≥ 0.2)
Target=1, ŷ=1 → No error → NO UPDATE
w₁=1, w₂=1, b=1
```

**End of Epoch 2: w₁=1, w₂=1, b=1**

---

## 17. Back Error Propagation {#backprop}

### 🔴 Q. Explain back error propagation with neat diagram and weight update equations.

**What is Backpropagation?**
It's the training algorithm for multi-layer neural networks. It calculates **how much each weight contributed to the error** and adjusts them accordingly.

**Two phases:**
```
1. Forward Pass → compute output
2. Backward Pass → compute error, update weights from output to input
```

**Diagram:**
```
         Input Layer      Hidden Layer     Output Layer
              x₁  ──w₁──→  h₁  ──v₁──→
         x₂  ──w₂──→  h₂  ──v₂──→  y  →  Error = (target − y)
              x₃  ──w₃──→  h₃  ──v₃──→
                    ↑               ↑
              Forward Pass          Backward Pass (error flows back)
```

---

**Step-by-Step Algorithm:**

**Step 1: Forward Pass**
```
For each layer, compute:
  net_j = Σ(wᵢⱼ × xᵢ) + bias
  out_j = f(net_j)    ← apply activation function
```

**Step 2: Compute Output Error**
```
δₖ (output neuron error) = (tₖ − yₖ) × f'(net_k)
Where f'(x) is derivative of activation function
For sigmoid: f'(x) = f(x) × (1 − f(x)) = yₖ × (1 − yₖ)
```

**Step 3: Backpropagate Error to Hidden Layer**
```
δⱼ (hidden neuron error) = f'(net_j) × Σ(δₖ × wⱼₖ)
```

**Step 4: Update Weights**
```
For output layer weights (v):
  Δvⱼₖ = η × δₖ × out_j
  new_vⱼₖ = old_vⱼₖ + Δvⱼₖ

For hidden layer weights (w):
  Δwᵢⱼ = η × δⱼ × xᵢ
  new_wᵢⱼ = old_wᵢⱼ + Δwᵢⱼ

Where η = learning rate
```

**Step 5: Repeat until error is below acceptable limit**

---

**Key Formulas Summary:**

```
Error (MSE) = (1/2) × Σ(tₖ − yₖ)²

Output delta: δₖ = (tₖ − yₖ) × yₖ(1 − yₖ)

Hidden delta: δⱼ = hⱼ(1 − hⱼ) × Σ(δₖ × vⱼₖ)

Weight update (output): Δv = η × δₖ × hⱼ

Weight update (hidden): Δw = η × δⱼ × xᵢ
```

**Why "Back" propagation?**
Error is calculated at the output, then propagated **backwards** through the network to update earlier weights. This is **gradient descent** on the error surface.

---

## 18. Curse of Dimensionality & PCA Theory {#pca-theory}

### 🔴 Q. What is the Curse of Dimensionality? Explain PCA.

**Curse of Dimensionality:**
As the number of features (dimensions) increases, the data becomes very **sparse** and algorithms behave poorly.

```
Problems:
1. Distance becomes meaningless (everything is "far")
2. Need exponentially more data to fill the space
3. Overfitting increases
4. Training becomes very slow
5. Visualization impossible beyond 3D
```

Example: In 1D, 10 points cover a line well. In 10D, you'd need 10^10 = 10 billion points to cover the same density!

---

**Principal Component Analysis (PCA):**
PCA **reduces the number of dimensions** while keeping most of the information (variance).

**Core Idea:**
Find new axes (principal components) that capture the most variance in the data. PC1 captures the most variance, PC2 captures the second most, and so on.

**When to use PCA:**
- You have many correlated features
- You want to visualize high-dimensional data
- You want to speed up training

**Steps of PCA:**
```
Step 1: Standardize the data (subtract mean, divide by std)
Step 2: Calculate the Covariance Matrix
Step 3: Find Eigenvalues and Eigenvectors
Step 4: Sort eigenvalues in descending order
Step 5: Pick top k eigenvectors (principal components)
Step 6: Transform data to new k-dimensional space
```

**Why eigenvalues?**
Larger eigenvalue = that direction captures more variance = more important.

**Variance Explained:**
```
% variance by PC₁ = λ₁ / (λ₁ + λ₂ + ... + λₙ) × 100
```

Keep components until you've captured 90–95% of total variance.

---

## 19. PCA Numerical — Solved {#pca-num}

### 🔴 Q. Apply PCA on: x = [2, 1, 0, −1], y = [4, 3, 1, 0.5]

**Step 1: Calculate Mean**

```
x̄ = (2+1+0+(−1))/4 = 2/4 = 0.5
ȳ = (4+3+1+0.5)/4 = 8.5/4 = 2.125
```

**Step 2: Center the Data (subtract mean)**

| x | y | x' = x−x̄ | y' = y−ȳ |
|---|---|---|---|
| 2 | 4.0 | **+1.5** | **+1.875** |
| 1 | 3.0 | **+0.5** | **+0.875** |
| 0 | 1.0 | **−0.5** | **−1.125** |
|−1 | 0.5 | **−1.5** | **−1.625** |

**Step 3: Calculate Covariance Matrix**

Using sample covariance (divide by n−1 = 3):

```
Cov(x,x) = (1.5² + 0.5² + 0.5² + 1.5²) / 3
          = (2.25+0.25+0.25+2.25) / 3
          = 5/3 ≈ 1.667

Cov(y,y) = (1.875² + 0.875² + 1.125² + 1.625²) / 3
          = (3.516 + 0.766 + 1.266 + 2.641) / 3
          = 8.189 / 3 ≈ 2.729

Cov(x,y) = (1.5×1.875 + 0.5×0.875 + (−0.5)(−1.125) + (−1.5)(−1.625)) / 3
          = (2.8125 + 0.4375 + 0.5625 + 2.4375) / 3
          = 6.25/3 ≈ 2.083

Covariance Matrix:
C = | 1.667  2.083 |
    | 2.083  2.729 |
```

**Step 4: Find Eigenvalues**

det(C − λI) = 0:
(1.667−λ)(2.729−λ) − (2.083)² = 0
λ² − 4.396λ + (4.549 − 4.339) = 0
**λ² − 4.396λ + 0.21 = 0**

Using quadratic formula:
```
λ = [4.396 ± √(4.396² − 4×0.21)] / 2
  = [4.396 ± √(19.324 − 0.840)] / 2
  = [4.396 ± √18.484] / 2
  = [4.396 ± 4.299] / 2

λ₁ = (4.396 + 4.299)/2 = 4.348  ← 1st Principal Component
λ₂ = (4.396 − 4.299)/2 = 0.049  ← 2nd Principal Component
```

**Step 5: Variance Explained**

```
PC1 explains: 4.348 / (4.348+0.049) × 100 = 4.348/4.397 × 100 ≈ 98.9%
PC2 explains: 0.049 / 4.397 × 100 ≈ 1.1%
```

> **PC1 alone captures ~99% of the variance** → We can reduce from 2D to 1D and lose almost no information!

**Step 6: Find Eigenvector for PC1 (λ₁ = 4.348)**

(C − 4.348I)v = 0:
```
| 1.667−4.348   2.083 | |v₁|   |0|
| 2.083       2.729−4.348 | |v₂| = |0|

| −2.681  2.083 | v = 0
| 2.083  −1.619 |

−2.681v₁ + 2.083v₂ = 0
v₁ = (2.083/2.681)v₂ = 0.777v₂
```

Let v₂=1: v = [0.777, 1]
Normalize: ||v|| = √(0.777²+1²) = √1.604 = 1.267

**PC1 direction = [0.612, 0.789]** (approximately [0.61, 0.79])

This means the first principal component is a combination of both x and y, mostly leaning towards y.

---

## 20. Feature Selection Methods {#feature-sel}

### Q. Write a short note on feature selection method for dimensionality reduction.

**What is Feature Selection?**
Selecting the **most relevant subset of original features** and discarding irrelevant ones.

> Difference from PCA (Feature Extraction): Feature selection keeps original features. PCA creates new ones.

**Three Types:**

**1. Filter Methods** (rank features independently of the model)
```
- Correlation coefficient (remove highly correlated features)
- Chi-squared test (for categorical data)
- Information Gain / Mutual Information
- Variance threshold (remove near-zero variance features)
→ Fast, model-independent, but ignores feature interactions
```

**2. Wrapper Methods** (use a model to evaluate feature subsets)
```
- Forward Selection: start empty, add best feature one by one
- Backward Elimination: start all, remove worst one by one
- Recursive Feature Elimination (RFE)
→ Better accuracy but very slow for large datasets
```

**3. Embedded Methods** (feature selection built into the model)
```
- LASSO (L1 Regularization): shrinks some weights to exactly 0 → removes those features
- Ridge (L2 Regularization): shrinks weights, doesn't remove
- Decision Tree: selects best features naturally using information gain
→ Balance between speed and accuracy
```

**Why do dimensionality reduction?**
- Reduces overfitting (less noise, fewer irrelevant features)
- Speeds up training
- Improves model interpretability
- Saves storage and computation

---

# ═══════════════════════════════
# EXPERIMENTS — VIVA QUESTIONS
# ═══════════════════════════════

## 21. All 9 Experiments — Viva Q&A {#experiments}

---

### Exp 3A: Linear Regression

**What is the aim of this experiment?**
To fit a straight line (or plane) through data that best predicts a continuous output value.

**Equation:**
```
Simple:   y = β₀ + β₁x
Multiple: y = β₀ + β₁x₁ + β₂x₂ + ... + βₚxₚ
```

**Q. What loss function does linear regression minimize?**
MSE — Mean Squared Error = (1/n) × Σ(yᵢ − ŷᵢ)²
It minimizes the sum of squared residuals (Ordinary Least Squares).

**Q. What does R² = 0.85 mean?**
The model explains 85% of the variation in the output variable. Closer to 1 is better.

**Q. What is the difference between R² and Adjusted R²?**
R² always increases when you add features. Adjusted R² penalizes adding useless features. Use Adjusted R² when comparing models with different numbers of features.

**Q. What is multicollinearity? Why is it a problem?**
When two or more input features are highly correlated with each other (e.g., height in cm and height in inches). It makes individual coefficients unreliable and hard to interpret.

**Q. What is the train-test split? Why do we use it?**
We divide data into training set (to fit the model) and test set (to evaluate on unseen data). Typically 80:20 or 70:30. This checks if the model generalizes and isn't just memorizing the training data.

**Q. What metrics do you use to evaluate linear regression?**
- RMSE (Root Mean Square Error) — in same unit as y, sensitive to outliers
- MAE (Mean Absolute Error) — average absolute error
- R² — proportion of variance explained

**Q. What are the assumptions of linear regression?**
1. Linearity between X and Y
2. Independence of errors
3. Homoscedasticity (constant variance of errors)
4. Normality of errors
5. No multicollinearity

---

### Exp 3B: Logistic Regression

**What is the aim of this experiment?**
To classify data into categories (binary: yes/no, 0/1) by predicting probability using the sigmoid function.

**Q. Why can't we use linear regression for classification?**
Linear regression can predict values outside [0,1] (e.g., −2 or 5), which makes no sense as probabilities. Logistic regression outputs values strictly between 0 and 1.

**Q. What is the sigmoid function and what does it output?**
```
f(z) = 1 / (1 + e^−z)     Range: (0, 1)
```
It squashes any input to a value between 0 and 1, interpreted as a probability.

**Q. What is the default decision threshold in logistic regression?**
0.5. If predicted probability > 0.5 → Class 1, else → Class 0.
This threshold can be changed depending on the problem (e.g., medical diagnosis may use 0.3).

**Q. What loss function does logistic regression use?**
Binary Cross-Entropy (Log Loss):
```
Loss = −(1/n) × Σ [yᵢ log(p̂ᵢ) + (1−yᵢ) log(1−p̂ᵢ)]
```

**Q. What is the difference between logistic regression and linear regression?**

| Feature | Linear Regression | Logistic Regression |
|---|---|---|
| Output | Continuous value | Probability (0–1) |
| Problem type | Regression | Classification |
| Loss function | MSE | Log Loss |
| Activation | None (identity) | Sigmoid |

**Q. What metrics do you use to evaluate logistic regression?**
Accuracy, Precision, Recall, F1-Score, AUC-ROC, Confusion Matrix.

**Q. What is AUC-ROC?**
Area Under the ROC Curve. ROC plots True Positive Rate vs False Positive Rate at different thresholds. AUC = 1 is perfect, AUC = 0.5 is random guessing.

**Q. Can logistic regression handle multi-class problems?**
Yes — using One-vs-Rest (OvR) or Softmax (multinomial logistic regression).

---

### Exp 4: Support Vector Machine (SVM)

**What is the aim of this experiment?**
To find the optimal hyperplane that separates two classes with the maximum margin.

**Q. What is a hyperplane in SVM?**
A decision boundary. In 2D it's a line, in 3D it's a plane, in higher dimensions it's a hyperplane.
Equation: **w·x + b = 0**

**Q. What are support vectors?**
The data points that lie closest to the hyperplane. These points "support" or define the boundary. Only support vectors matter for defining the hyperplane — other points don't affect it.

**Q. What is the margin in SVM? How is it calculated?**
```
Margin = 2 / ||w||
```
SVM maximizes this margin → equivalent to minimizing ||w||.

**Q. What is the kernel trick? Why is it needed?**
Not all data is linearly separable. The kernel trick maps data to a higher-dimensional space where it becomes linearly separable — without explicitly computing those coordinates (making it computationally efficient).

**Q. Name common SVM kernels and when to use each.**
| Kernel | When to use |
|---|---|
| Linear | Data is linearly separable |
| Polynomial | Curved decision boundaries |
| RBF (Gaussian) | General purpose, works for most datasets |

**Q. What is C (regularization parameter) in SVM?**
- **Small C** → wider margin, more misclassification allowed (softer boundary, less overfitting)
- **Large C** → narrower margin, fewer misclassifications allowed (harder boundary, may overfit)

**Q. Why must we scale features before applying SVM?**
SVM is distance-based. If one feature has values 1–1000 and another 0–1, the large-valued feature dominates the distance calculation and the model is biased. Scaling makes all features contribute equally.

**Q. What is the difference between Hard Margin and Soft Margin SVM?**
- Hard Margin: No misclassification allowed — only works if data is perfectly separable
- Soft Margin: Allows some misclassifications using a slack variable ξ — for real-world noisy data

**Q. Can SVM be used for regression?**
Yes — it's called SVR (Support Vector Regression).

---

### Exp 5: Hebbian Learning Algorithm

**What is the aim of this experiment?**
To implement the Hebbian learning rule and train weights for a simple logic gate (OR/AND) using bipolar inputs.

**Q. State the Hebbian learning rule.**
"Neurons that fire together, wire together."
```
Δwᵢ = η × xᵢ × y
Δb  = η × y       (η = learning rate, usually 1)
```
Weights are updated for every input regardless of whether the output was correct.

**Q. What is the key difference between Hebbian learning and Perceptron learning?**
| Feature | Hebbian | Perceptron |
|---|---|---|
| Error checking | No (always updates) | Yes (updates only on error) |
| Input type | Bipolar (−1, +1) | Binary (0, 1) or Bipolar |
| Convergence | No guarantee | Guaranteed if linearly separable |
| Goal | Strengthen correlations | Minimize classification error |

**Q. Why are bipolar inputs used in Hebbian Learning?**
Binary input 0 causes no weight update (Δw = η × 0 × y = 0), so patterns with 0 inputs are ignored. Bipolar (−1) still produces a meaningful weight update.

**Q. Does Hebbian learning have a stopping condition?**
No formal stopping condition. It's a one-pass algorithm — weights are updated once for each training sample. There is no convergence guarantee based on error.

**Q. What are the final weights for the OR gate (bipolar)?**
w₁ = 2, w₂ = 2, b = 2

**Q. What are the final weights for the AND gate (bipolar)?**
w₁ = 2, w₂ = 2, b = −2

**Q. What inputs does Hebbian learning work best on?**
Linearly separable problems with bipolar representation.

---

### Exp 6: McCulloch-Pitts Model

**What is the aim of this experiment?**
To implement the binary threshold neuron (1943) and simulate AND and NOT logic gates without any learning — weights are set manually.

**Q. How does the McCulloch-Pitts neuron work?**
```
net = Σ(wᵢ × xᵢ)
Output = 1 if net ≥ θ (threshold), else 0
```
Inputs and outputs are binary (0 or 1 only).

**Q. What weights and threshold implement AND gate?**
w₁ = 1, w₂ = 1, θ = 2
Both inputs must fire (1+1=2 ≥ 2) for output = 1.

**Q. What weights and threshold implement NOT gate?**
w = −1 (inhibitory), θ = 0
x=1: net = −1 < 0 → output 0. x=0: net = 0 ≥ 0 → output 1.

**Q. What is an inhibitory connection?**
A connection with a negative weight (w = −1). If this input is active (=1), it suppresses firing regardless of other inputs.

**Q. What are the limitations of the McCulloch-Pitts model?**
1. **No learning** — weights must be set manually by hand
2. **Binary only** — cannot handle real-valued (continuous) inputs
3. **Fixed threshold** — no adaptive threshold
4. **Cannot solve XOR** — XOR is not linearly separable, needs a hidden layer

**Q. What is the XOR problem?**
XOR outputs 1 only when inputs differ (0,1 and 1,0 → 1; 0,0 and 1,1 → 0). You cannot draw a single straight line to separate these two classes — not linearly separable. Needs at least 2 layers (hidden layer) to solve.

**Q. What is the difference between McCulloch-Pitts and the Perceptron?**
| Feature | McCulloch-Pitts | Perceptron |
|---|---|---|
| Learning | None (manual weights) | Yes (error-correction rule) |
| Threshold | Fixed, set manually | Adaptive (learned as bias) |
| Inputs | Binary (0/1) | Binary or real-valued |
| Year | 1943 | 1958 (Rosenblatt) |

---

### Exp 7: Single Layer Perceptron

**What is the aim of this experiment?**
To train a single-layer perceptron using the error-correction learning rule to implement logic gates (OR).

**Q. What is the Perceptron Learning Rule?**
```
ŷ = 1 if net ≥ θ, else 0
If error (ŷ ≠ target):
  Δwᵢ = η × (target − ŷ) × xᵢ
  Δb   = η × (target − ŷ)
```
Key: weights are updated **only when there is an error**.

**Q. What is an epoch?**
One complete pass through the entire training dataset. Training runs for multiple epochs until all outputs are correct (no errors).

**Q. What is the Perceptron Convergence Theorem?**
If the training data is **linearly separable**, the Perceptron learning algorithm is guaranteed to converge (find a solution) in a finite number of steps.

**Q. What is the difference between Hebbian and Perceptron learning?**
Hebbian updates always; Perceptron updates only when the output is wrong. Perceptron is more focused — it only fixes mistakes.

**Q. What determines if the Perceptron has converged?**
When it completes a full epoch with **zero errors** — all inputs are classified correctly.

**Q. Why does the Perceptron fail on XOR?**
XOR is not linearly separable — no single straight line can separate the two classes. A single-layer perceptron can only implement linearly separable functions. XOR needs a **multi-layer perceptron (MLP)** with at least one hidden layer.

**Q. What is the role of bias in a Perceptron?**
Bias shifts the decision boundary away from the origin. Without bias, the decision boundary is forced to pass through the origin, severely limiting what patterns the model can learn.

**Q. After 2 epochs for OR gate (w₁=w₂=b=0, θ=0.2, η=1), what are the final weights?**
w₁ = 1, w₂ = 1, b = 1

---

### Exp 8: Error Backpropagation

**What is the aim of this experiment?**
To train a multi-layer neural network (MLP) using the backpropagation algorithm, which propagates error backward through layers to update weights.

**Q. What are the two phases of backpropagation?**
1. **Forward Pass** — input flows forward, output is produced
2. **Backward Pass** — error is computed at output, propagated backwards to update weights

**Q. Write the weight update equations for backpropagation.**
```
Output layer delta:  δₖ = (tₖ − yₖ) × yₖ × (1 − yₖ)
Hidden layer delta:  δⱼ = hⱼ × (1 − hⱼ) × Σ(δₖ × wⱼₖ)

Weight update (output layer): Δv = η × δₖ × hⱼ
Weight update (hidden layer): Δw = η × δⱼ × xᵢ
```

**Q. What activation function is used in backpropagation and why?**
Sigmoid: f(x) = 1/(1+e^−x)
Because its derivative is simple: f'(x) = f(x)×(1−f(x)) — easy to compute during backprop.

**Q. What is the vanishing gradient problem?**
In deep networks, the sigmoid derivative is at most 0.25. Multiplying many small gradients layer by layer makes the gradient nearly zero in early layers → those weights barely update → slow or no learning. Solved by using ReLU activation instead of sigmoid.

**Q. What is gradient descent?**
Optimization algorithm that moves model parameters in the direction that reduces the loss:
```
w_new = w_old − η × (∂Loss/∂w)
```
Backpropagation computes the gradients (∂Loss/∂w); gradient descent uses them to update.

**Q. What is learning rate (η)? What happens if it is too high or too low?**
- Too high → weights overshoot the minimum → oscillates or diverges
- Too low → training is very slow
- Typical values: 0.001 to 0.1

**Q. What is the difference between Single Layer Perceptron and Multi-Layer Perceptron?**
| Feature | SLP | MLP |
|---|---|---|
| Hidden layers | None | One or more |
| Can solve XOR | No | Yes |
| Training algorithm | Perceptron rule | Backpropagation |
| Problems it solves | Linearly separable only | Any (with enough neurons) |

**Q. What is the error function minimized in backpropagation?**
```
E = (1/2) × Σ(tₖ − yₖ)²
```

**Q. What is overfitting in a neural network? How to prevent it?**
When the network memorizes training data and fails on new data. Prevention: Dropout, Early Stopping, Regularization (L2), getting more training data.

---

### Exp 9: Principal Component Analysis (PCA)

**What is the aim of this experiment?**
To reduce the number of features (dimensions) in a dataset while retaining maximum variance/information.

**Q. What are the steps of PCA?**
```
Step 1: Standardize data (mean=0, std=1)
Step 2: Calculate the Covariance Matrix
Step 3: Find Eigenvalues and Eigenvectors of the covariance matrix
Step 4: Sort eigenvalues in descending order
Step 5: Select top k eigenvectors as Principal Components
Step 6: Transform data: X_new = X × [PC1 | PC2 | ... | PCk]
```

**Q. Why must we standardize data before PCA?**
PCA is based on variance. If features have different scales (e.g., salary in ₹10,000s vs age in years), the high-scale feature will dominate the principal components just because of its scale, not because it's more important.

**Q. What is a Principal Component?**
A new axis (direction) that is a linear combination of the original features. PC1 is the direction of maximum variance. PC2 is perpendicular to PC1 with the second most variance, and so on.

**Q. What does the eigenvalue represent in PCA?**
The eigenvalue of each principal component tells us **how much variance** that component captures. Larger eigenvalue = more important component.

**Q. How do you decide how many components to keep?**
Keep enough components to explain 90–95% of total variance:
```
Cumulative variance = Σλᵢ (for selected components) / Σλᵢ (all)
```
Plot a "scree plot" — look for the "elbow" where variance explained drops off sharply.

**Q. Is PCA supervised or unsupervised?**
Unsupervised — it does not use class labels. It only looks at the variance structure of the features.

**Q. What is the difference between feature selection and feature extraction (PCA)?**
| Feature Selection | Feature Extraction (PCA) |
|---|---|
| Keeps original features | Creates new features |
| Features remain interpretable | New components are harder to interpret |
| Examples: RFE, LASSO | Examples: PCA, LDA |

**Q. For the given data x=[2,1,0,−1], y=[4,3,1,0.5] — what did PCA give?**
- Covariance matrix: C = [[1.667, 2.083],[2.083, 2.729]]
- Eigenvalues: λ₁ = 4.348, λ₂ = 0.049
- PC1 captures **98.9%** of total variance → data can be reduced from 2D to 1D

**Q. What is the curse of dimensionality and how does PCA address it?**
As dimensions increase, data becomes sparse, distances become meaningless, and models overfit. PCA addresses it by projecting data onto fewer dimensions while keeping the most important variance, making learning easier and faster.



# ═══════════════════════════════
# QUICK FORMULA CHEAT SHEET
# ═══════════════════════════════

## 22. Formula Cheat Sheet {#formulas}

**Linear Regression:**
```
Ŷ = β₀ + β₁X
β₁ = (nΣxy − ΣxΣy) / (nΣx² − (Σx)²)
β₀ = (Σy − β₁Σx) / n
```

**SVM:**
```
Hyperplane: w·x + b = 0
Margin = 2/||w||
Distance of point (x₀,y₀) from ax+by+c=0: |ax₀+by₀+c|/√(a²+b²)
```

**Confusion Matrix:**
```
Accuracy  = (TP+TN)/(TP+TN+FP+FN)
Precision = TP/(TP+FP)
Recall    = TP/(TP+FN)
F1        = 2×P×R/(P+R)
```

**Hebbian Learning:**
```
Δwᵢ = η × xᵢ × y     (η=1 by default)
Δb  = η × y
```

**Perceptron Update:**
```
Δwᵢ = η × (target − output) × xᵢ
Δb  = η × (target − output)
```

**Backpropagation:**
```
Output delta: δₖ = (t−y) × y(1−y)
Hidden delta: δⱼ = h(1−h) × Σ(δₖ × wⱼₖ)
Weight update: Δw = η × δ × input
```

**Sigmoid:**
```
f(x) = 1/(1+e⁻ˣ)     Range: (0,1)
f'(x) = f(x)(1−f(x))
```

**PCA Steps:**
```
1. Standardize data
2. Covariance matrix C
3. Eigenvalues & Eigenvectors of C
4. Sort by eigenvalue (largest first)
5. Keep top k components
6. Transform: X_new = X × [PC1 | PC2 | ... | PCk]
```

**Diagonalization:**
```
A = PDP⁻¹
D has eigenvalues on diagonal
P has eigenvectors as columns
```

**SVD:**
```
A = UΣVᵀ
Singular values σ = √(eigenvalues of AᵀA)
V = eigenvectors of AᵀA
U = eigenvectors of AAᵀ
```

**Math Basics:**
```
Norm:       ||v|| = √(v₁²+v₂²+...+vₙ²)
Trace:      tr(A) = a₁₁+a₂₂+...+aₙₙ
Det (2×2):  det(A) = ad-bc
Orthogonal: u·v = 0
```

---

## Most Likely Viva Questions — Quick List

**IA-1:**
1. What are the steps to develop an ML application?
2. Define overfitting and underfitting. How to fix them?
3. Diagonalize [[2,2],[1,3]] — eigenvalues, eigenvectors, P and D
4. SVD of [[1,1],[7,7]] — singular values = 10, 0
5. Least squares line for given data, find y at x=4
6. What is SVM? What are support vectors? What is the margin?
7. Calculate accuracy, precision, recall from a confusion matrix
8. Calculate perpendicular distance from hyperplane

**IA-2:**
9. Compare BNN and ANN in a table
10. Explain Hebbian rule — do OR or AND gate (bipolar)
11. McCulloch-Pitts for AND and NOT — verify with truth table
12. Name and explain 4 activation functions with formula and range
13. Do single layer perceptron for OR — show 2 epochs step by step
14. Explain backpropagation — forward pass, error, backward pass, update equations
15. What is the curse of dimensionality?
16. Steps of PCA — apply on given data
17. What is TF-IDF? (if asked cross-subject)
18. What is EM algorithm?

**Experiments:**
19. What Python library for ML? → scikit-learn
20. Why standardize before SVM/PCA? → Distance-based, scale matters
21. What is train-test split? Why use it?
22. What is the perceptron convergence theorem?
23. Why sigmoid fails in deep networks? → Vanishing gradient

---

*Machine Learning Viva Preparation Guide*
*Mumbai University | T.E. Sem VI | IA-1 + IA-2 + Experiments*
