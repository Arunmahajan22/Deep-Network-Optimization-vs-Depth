## Structural Analysis of Gradient Flow in Deep Neural Networks  
**Roll Number: 102303346**

---

## 📖 Abstract

This project investigates gradient propagation behavior in deep neural networks under deterministic architectural constraints derived from roll-number parameters. The objective is to analyze how increasing network depth affects gradient magnitude distribution across layers using the Gradient Ratio Index (GRI) as a structural fingerprint.

All computations — including forward propagation, backward propagation, gradient computation, and parameter updates — are implemented manually using NumPy without any deep learning frameworks.

---

## 🔬 Dataset

A nonlinear regression dataset was constructed:

y = sin(x₀) + 0.5x₁² − 0.8x₂

This enforces:
- Oscillatory behavior (sine term)
- Curvature (quadratic term)
- Linear dependency

The dataset therefore requires nonlinear representational capacity.

---

## ⚙️ Architecture (Roll-Number Constrained)

Roll Number: 102303346  
Last three digits: 346  

a = 6  
b = 4  
c = 3  

Derived architecture:

- Hidden Width = 6 + a = 12  
- Hidden Layers = 4 + (b mod 3) = 5  
- Learning Rate = 0.002 × (c + 1) = 0.008  
- Activation = ReLU (since a is even)  
- Initialization Range = [-1/7, +1/7]  
- Bias = 0  

Baseline Architecture:

3 → 12 → 12 → 12 → 12 → 12 → 1

All architectural properties strictly follow assignment constraints.

---

## 📊 Part A – Gradient Flow Experiment

### Baseline Model (5 Hidden Layers)

Training: 400 epochs

Results:

- Loss Epoch 1: 2.0239966428645446  
- Loss Epoch 100: 1.6227947912195544  
- Loss Epoch 400: 1.6077226071061075  

Gradient Norms:

- ‖∇W_first‖ = 0.0005896816602454895  
- ‖∇W_last‖ = 0.0003822231531776964  

GRI:

GRI = 1.5427680278995164

Interpretation:
- Gradient propagation was stable.
- No vanishing or exploding gradients.
- Early layers received sufficient learning signal.
- Optimization was slow but consistent.

---

### Structural Break (Depth Increase)

Since (b mod 3) = 1, three additional hidden layers were introduced.

New depth: 8 hidden layers.

Results:

- Loss Epoch 1: 1.6084530339737773  
- Loss Epoch 400: 1.6078097933813102  
- GRI: 0.368518044011785  

Observation:
- GRI decreased significantly (1.54 → 0.37).
- Early-layer gradients weakened relative to later layers.
- Training stagnated.
- No divergence observed.

Conclusion:
Increasing depth enhanced representational capacity but introduced gradient attenuation, leading to optimization difficulty. Depth alone does not guarantee improved learning performance.

---

## 📘 Part B – Parameter Scaling Analysis

### Dense Layer Parameters

Input size: 30 × 30  
Hidden neurons: 36  

Total parameters:

(900 × 36) + 36 = 32436

---

### Convolution Layer Parameters

Filter size: 4 × 4  
Number of filters: 14  

Total parameters:

(16 × 14) + 14 = 238

Insight:
Dense layers scale with full spatial resolution, while convolution layers scale only with local filter size due to weight sharing.

---

### Manual Convolution Result

Center convolution output: -18

---

## 🧠 Key Findings

1. Depth influences gradient magnitude distribution.
2. Gradient Ratio Index (GRI) effectively measures signal survival.
3. Increased depth may introduce optimization instability.
4. Representation power and optimization stability are distinct properties.

---

## 🛠 Implementation Details

- Language: Python  
- Libraries Used: NumPy, Pandas  
- No PyTorch / TensorFlow / Keras  
- No automatic differentiation  
- All gradients computed manually  

---

## 🔒 Integrity Statement

This implementation is structurally unique because:

- Architecture depends on roll-number digits.
- Learning rate varies.
- Depth varies.
- Activation varies.
- Gradient norms vary.
- Convolution computations vary.

Therefore, results are personalized and cannot be generically replicated without violating assignment constraints.

---

## 📌 Repository Description (Top Line)

Structural analysis of gradient propagation in deep neural networks using manual backpropagation and Gradient Ratio Index (GRI).
