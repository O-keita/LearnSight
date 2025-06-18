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
| Instance 1            | Adam               | None                 | 75         | ❌ No              | 0.0              | 0.001             | 0.9367       | 0.9367       | 0.9368        | 0.9367     | 0.22     |
| Instance 2            | Adam               | L2                   | 75         | ❌ No              | 0.0              | 0.001             | 0.9400       | 0.9395       | 0.9416        | 0.9400     | 0.19     |
| Instance 3            | RMSProp            | L2                   | 75         | ✅ Yes             | 0.2              | 0.0005            | 0.9433       | 0.9431       | 0.9440        | 0.9433     | 0.16     |
| Instance 4            | Adam               | L2                   | 75         | ✅ Yes             | 0.1              | 0.001             | **0.9633**   | **0.9633**   | **0.9633**    | **0.9633** | **0.11** |


## 🧠 Best Performing Neural Network Instance

- ### The best performing instance among all the four neural networks is **NN Instance 4**. It used:
  - **Adam** as the optimizer, which adapts the learning rate dynamically and performs well in most neural networks.
  - **L2 Regularization**, which penalizes large weights to help prevent overfitting and improve generalization.
  - **Early Stopping** was applied, halting training at **epoch 68 out of 75** when validation loss plateaued. With a patience of 5, this means no improvement was detected since **epoch 63**.
  - **A small dropout rate of 0.1**, meaning 10% of neurons were randomly dropped during training to reduce overfitting. Compared to higher dropout in previous models (e.g., 0.2), this setting led to better generalization.

- ### Further Explaining the Metrics:
  - From the best NN instance, we achieved an **accuracy of 0.9633**, meaning **96.33%** of students in the test set were correctly classified as either **High Achiever**, **Average**, or **At Risk**.
  - The **F1 Score** of **0.9633** reflects a strong balance between precision and recall across all categories.
  - The **Recall** of **96.33%** shows the model successfully identifies nearly all students in each class—**a critical factor** when identifying "At Risk" students who need early intervention and support.

---

## 🏁 Summary: Best Model Comparison

The best performing model overall was **Logistic Regression**, with an impressive **accuracy of 96.67%**, narrowly outperforming the top neural network model.

However, the neural network in **Instance 4** was a **very close contender** with **96.33% accuracy**, showing robust performance through **regularization, dropout, and early stopping**.

### 🧪 Insights:

- **Classical ML models** like **Logistic Regression** perform exceptionally well when the **data is clean** and **features are well-engineered**.
- **Neural Networks** offer greater **flexibility** and **representation power**, but require more **careful hyperparameter tuning**.
- **Instance 4's performance** shows that combining **dropout**, **early stopping**, and **L2 regularization** can lead to highly accurate and generalizable models.
- **SVM underperformed**, likely due to sensitivity to feature scaling or suboptimal kernel configuration.
- **XGBoost**, with **95.67% accuracy**, also demonstrated strong ensemble power and generalization—surpassing most neural networks except Instance 4.

### 🎓 Educational Impact:

In education-focused systems where **recall is vital**—especially for detecting "At Risk" students—both **Logistic Regression** and **NN Instance 4** are highly reliable models.  
Logistic Regression may be favored for its **speed and interpretability**, while NN Instance 4 provides powerful performance with deeper learning capability for complex patterns.

