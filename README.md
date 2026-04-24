# Self-Pruning Neural Network (AI Engineering Case Study)

This project implements a **self-pruning neural network** that learns to remove unnecessary connections during training using a differentiable gating mechanism.

---

## 🔍 Overview

- Each weight is associated with a **learnable gate (0–1)**  
- Gates control whether a connection is important  
- The model learns to suppress less useful weights during training  

---

## ⚙️ Key Components

### 🔹 Prunable Linear Layer
- Custom layer with learnable gate parameters  
- Gates computed using sigmoid  
- Effective weight = `weight × gate`  

### 🔹 Sparsity Regularization
- L1 penalty applied on gate values  
- Encourages the model to reduce active connections  
- Enables **self-pruning during training**  

### 🔹 Training Objective

Loss = CrossEntropy + λ × SparsityLoss  

---

## 📊 Results

| Lambda | Test Accuracy | Sparsity (%) |
|--------|-------------|--------------|
| 1e-4   | 0.5615      | 0.00         |
| 1e-3   | 0.5394      | 0.00         |
| 1e-2   | 0.5039      | 0.00         |

---

## 📈 Observations

- Increasing λ slightly reduces accuracy  
- Model performs **soft pruning** (weights shrink but don’t reach zero)  
- Strict thresholding results in 0% measured sparsity  

---

## 📉 Gate Distribution

- Most gate values lie in a low range (~0.05–0.1)  
- Very few reach exact zero  
- Indicates **gradual compression rather than hard pruning**  

---

## 📁 Files

- `self_pruning_nn.ipynb` → Implementation  
- `report.md` → Case study explanation  

---

## 🧠 Key Takeaways

- Built a differentiable pruning mechanism  
- Demonstrated accuracy vs sparsity trade-off  
- Observed limitations of sigmoid-based pruning  

---

## ✍️ Author

Radha Gohil
