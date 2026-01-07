# Machine Learning & Deep Learning – Production Cheat Sheet

> **Purpose**: A sharp, end-to-end cheat sheet for **Machine Learning (ML)** and **Deep Learning (DL)**.
> Built for **applied engineers**, not theory-heavy researchers.
> Focused on **decision-making, failure modes, and production readiness**.
> Copy-paste friendly for emergencies and interviews.

---

## 1. Core Mental Model (Most Important Section)

Machine Learning is about **learning mappings from data**.
Deep Learning is about **learning representations + mappings**.

```text
Data → Features → Model → Loss → Optimization → Prediction
```

If you cannot explain where the signal comes from, stop modeling.

---

## 2. ML vs DL (Clear Boundary)

### Machine Learning

* Manual feature engineering
* Smaller datasets
* Faster training
* Easier interpretability

### Deep Learning

* Automatic feature learning
* Large datasets
* GPU-heavy
* Lower interpretability

DL is not better by default.

---

## 3. Problem Types (Identify Correctly)

### Supervised

* Regression
* Classification

### Unsupervised

* Clustering
* Dimensionality reduction

### Semi-supervised

* Limited labels

### Reinforcement Learning

* Sequential decisions

Wrong framing = wrong solution.

---

## 4. Data Preparation (Where Models Are Won or Lost)

Steps:

* Missing value handling
* Outlier treatment
* Encoding categorical variables
* Scaling and normalization

Garbage data produces confident nonsense.

---

## 5. Train / Validation / Test Split

```text
Train: learn patterns
Validation: tune hyperparameters
Test: final evaluation
```

Never touch test data during training.

---

## 6. Feature Engineering (ML Superpower)

Examples:

* Aggregations
* Ratios
* Lag features
* Rolling statistics

Better features beat better models.

---

## 7. Core ML Algorithms (Know When to Use)

### Regression

* Linear Regression
* Ridge / Lasso

### Tree-Based

* Decision Tree
* Random Forest
* Gradient Boosting

### Distance-Based

* KNN

Tree models dominate tabular data.

---

## 8. Model Training Example (ML)

```python
from sklearn.ensemble import RandomForestRegressor
model = RandomForestRegressor()
model.fit(X_train, y_train)
```

Always start with a baseline.

---

## 9. Evaluation Metrics (Choose Carefully)

### Regression

* MAE
* RMSE
* MAPE

### Classification

* Accuracy
* Precision
* Recall
* F1-score

Metric choice is a business decision.

---

## 10. Overfitting vs Underfitting

* Overfitting: memorization
* Underfitting: no signal learned

Balance bias and variance.

---

## 11. Deep Learning Fundamentals

Core components:

* Layers
* Activations
* Loss functions
* Optimizers

DL is optimization under constraints.

---

## 12. Neural Network Building Block

```python
import torch.nn as nn

model = nn.Sequential(
    nn.Linear(64, 32),
    nn.ReLU(),
    nn.Linear(32, 1)
)
```

Start small. Scale only when justified.

---

## 13. Loss Functions (Match the Task)

* MSE: regression
* Cross-entropy: classification
* Huber: robust regression

Wrong loss = broken training.

---

## 14. Optimizers (Practical View)

* SGD: stable, slower
* Adam: fast, common default

Learning rate matters more than optimizer.

---

## 15. Regularization Techniques

* L1 / L2 penalties
* Dropout
* Early stopping
* Data augmentation

Regularization controls generalization.

---

## 16. Scaling to Deep Learning

When DL makes sense:

* High-dimensional data
* Images, text, audio
* Non-linear patterns

Do not use DL for small tabular data blindly.

---

## 17. Training Loop (DL Mental Model)

```text
Forward → Loss → Backward → Update → Repeat
```

Debug training before scaling.

---

## 18. Evaluation for DL

Monitor:

* Training loss
* Validation loss
* Overfitting gap

Flat loss curves signal data issues.

---

## 19. Interpretability (Critical in Prod)

Techniques:

* Feature importance
* Partial dependence
* SHAP

Black boxes need guardrails.

---

## 20. Deployment Considerations

* Latency constraints
* Batch vs online inference
* Model size
* Hardware availability

A good model that cannot deploy is useless.

---

## 21. Common Anti-Patterns (Stop These)

* Skipping baselines
* Tuning without validation
* Data leakage
* Overcomplicated architectures
* Ignoring business metrics

---

## 22. ML vs DL Decision Checklist

Use ML if:

* Tabular data
* Limited samples
* Interpretability needed

Use DL if:

* Unstructured data
* Large datasets
* Complex patterns

---

## 23. Emergency Formulas

```text
Bias² + Variance + Noise = Error
```

```text
Precision = TP / (TP + FP)
Recall = TP / (TP + FN)
```

---

## 24. Final Mental Models

> Features beat models.
> Baselines beat assumptions.
> Simpler models fail less catastrophically.

---

