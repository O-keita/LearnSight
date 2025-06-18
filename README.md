# 🎯 LearnSight: Student Learning Support Classifier

## 🌍 Mission

**LearnSight** is built to empower schools and educators—especially in underserved regions like The Gambia—to detect students' learning needs early and accurately. By using data-driven insights, LearnSight helps ensure that **no student falls through the cracks** by proactively identifying those who are at risk, average, or excelling.

We believe every learner deserves the support they need to reach their full potential, and LearnSight is our tool to make that vision a reality.

## 📌 Project Overview

**LearnSight** is a machine learning classification tool designed to predict a student's level of learning support needs using academic scores and socio-economic features. The ultimate goal is to help schools allocate resources more effectively by identifying:

- Students who are **At Risk** and need intervention,
- Those performing at an **Average** level who may benefit from mild support, and
- **High Achievers** who may thrive with advanced opportunities.

### 🧾 Dataset Features

We used a publicly available dataset that includes:
- Gender
- Race/Ethnicity
- Parental Level of Education
- Lunch Type (as a proxy for socio-economic status)
- Test Preparation Course
- Math Score
- Reading Score
- Writing Score

### 🛠 Models Implemented
- Classical ML: Logistic Regression, Support Vector Machine (SVM)
- Neural Networks: Basic and Optimized versions
- Advanced ML: XGBoost (with tuned hyperparameters)

### 🧠 Prediction Classes
- `0`: **At Risk**
- `1`: **Average**
- `2`: **High Achiever**

### 🔮 Sample Final Prediction

```python
{
    'gender': 1,
    'lunch': 0,
    'test preparation course': 0,
    'math score': 85,
    'reading score': 60,
    'writing score': 88,
    'race/ethnicity_group C': 1,
    'parental level of education_high school': 1,
    ...
}
```

## 📊 ML Algorithm Performance Comparison

| **Model**            | **Accuracy** | **F1 Score** | **Precision** | **Recall** | **Loss** |
|----------------------|--------------|--------------|---------------|------------|----------|
| Logistic Regression  | 0.9667       | 0.9668       | 0.9672        | 0.9667     | 0.09     |
| SVM                  | 0.8967       | 0.8970       | 0.9002        | 0.8967     | 0.21     |
| XGBoost              | 0.9567       | 0.9566       | 0.9567        | 0.9567     | 0.13     |





## 📝 NN Model Discussion

| **Training Instance** | **Optimizer Used** | **Regularizer Used** | **Epochs** | **Early Stopping** | **Dropout Rate** | **Learning Rate** | **Accuracy** | **F1 Score** | **Precision** | **Recall** | **Loss** |
|-----------------------|--------------------|----------------------|------------|--------------------|------------------|-------------------|--------------|--------------|---------------|------------|----------|
| Instance 1            | Adam               | None                 | 75         | No                 | 0                | 0.001             | 0.9433       | 0.9429       | 0.9444        | 0.9433     | 0.22     |
| Instance 2            | Adam               | L2                   | 75         | No                 | 0                | 0.001             | 0.9500       | 0.9495       | 0.9519        | 0.9500     | 0.19     |
| Instance 3            | RMSProp            | L2                   | 75         | Yes                | 0.2              | 0.0005            | 0.9300       | 0.9294       | 0.9301        | 0.9300     | 0.16     |
| Instance 4            | Adam               | L2                   | 75         | Yes                | 0.1              | 0.001             | 0.9433       | 0.9429       | 0.9443        | 0.9433     | 0.11     |


## 🧠 Best Performing Neural Network Instance

- ### The best performing instance among all the four neural networks is **NN Instance 2**. It used:
  - **Adam** as the optimizer, which adapts the learning rate dynamically and performs well in most neural network tasks.
  - **L2 Regularization**, which penalizes large weights and helps prevent overfitting.
  - **No early stopping**, meaning the model trained for the full 75 epochs, yet still achieved excellent results suggesting a stable and well-generalizing configuration.
  - **No dropout**, indicating the model was regularized only through L2, which proved sufficient and effective.

- ### Further Explaining the Metrics:
  - From our best NN instance, we achieved an **accuracy of 95.00%**, meaning that **95% of students** in the test dataset were correctly classified as **High Achiever**, **Average**, or **At Risk**.
  - The **F1 Score of 0.9495** shows our model maintains a near-perfect balance between **precision** and **recall** across all three student categories.
  - The **Recall of 95%** ensures that the model correctly identifies almost all true students in each class—especially important when trying to **detect “At Risk” students** who may need academic intervention.

---

## 🏁 Summary: Best Model Comparison

The **best performing model overall** was **Logistic Regression**, with a **remarkable accuracy of 96.67%**, slightly outperforming the best neural network instance.

However, **NN Instance 2** was a close second (**accuracy: 95.00%**) and showcased powerful generalization capabilities using **L2 regularization alone**.

### 🧪 Insights:

- Classical ML models like **Logistic Regression** excel when **features are clean and well-engineered**.
- Neural Networks offer better **flexibility** and **representation learning**, but demand **careful tuning** of architecture and hyperparameters.
- **NN Instance 2** showed that **simple L2 regularization** alone can be extremely effective without requiring dropout or early stopping.
- **SVM underperformed**, likely due to **lack of kernel tuning** or **feature scaling sensitivity**.
- **XGBoost** also performed competitively (**accuracy: 95.67%**) and remains a strong general-purpose option.

In educational applications—where **recall for “At Risk” students** is critical—**Logistic Regression** and **NN Instance 2** are both **highly suitable**, depending on whether **interpretability or flexibility** is prioritized.
