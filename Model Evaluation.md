# Model Evaluation & Dataset Splitting (Explained Simply)

## 1. Why Do We Split a Dataset?

When we train a Machine Learning model, we divide the dataset into
**three parts**:

1.  **Training Set**
2.  **Validation Set**
3.  **Test Set**

### Example

Imagine you are preparing for an exam.

-   **Training Set** → The books and materials you study.
-   **Validation Set** → Practice tests you solve to check improvement.
-   **Test Set** → The final exam that measures your real performance.

This prevents the model from **memorizing the data** and ensures it
works well on **new unseen data**.

------------------------------------------------------------------------

# 2. Binary Classification

Binary classification means there are **only two classes**.

### Examples

-   Email → Spam or Not Spam
-   Medical scan → Tumor or No Tumor
-   Loan approval → Approved or Rejected

The model predicts **Positive or Negative**.

------------------------------------------------------------------------

# 3. Confusion Matrix

A **Confusion Matrix** helps us understand how well the model performs.

  Actual  Predicted   Positive              Negative
  ------------------- --------------------- ---------------------
  Positive            True Positive (TP)    False Negative (FN)
  Negative            False Positive (FP)   True Negative (TN)

### Meaning

**True Positive (TP)**\
Model correctly predicts positive.

Example: - Email is spam and model says spam.

**True Negative (TN)**\
Model correctly predicts negative.

Example: - Email is normal and model says not spam.

**False Positive (FP)**\
Model predicts positive but it is actually negative.

Example: - Important email marked as spam.

**False Negative (FN)**\
Model predicts negative but it is actually positive.

Example: - Spam email marked as normal.

------------------------------------------------------------------------

# 4. Accuracy

Accuracy measures **how many predictions were correct**.

Formula:

Accuracy = (TP + TN) / Total Predictions

### Example

If the model checked **100 emails**:

-   TP = 40
-   TN = 50
-   FP = 5
-   FN = 5

Accuracy = (40 + 50) / 100 = **90%**

Meaning the model predicted **90% correctly**.

------------------------------------------------------------------------

# 5. Precision

Precision answers:

> Out of all predicted positives, how many were actually correct?

Formula:

Precision = TP / (TP + FP)

### Example

Model predicted **50 emails as spam**.

-   40 were actually spam
-   10 were normal emails

Precision = 40 / 50 = **80%**

Meaning **20% were wrong predictions**.

------------------------------------------------------------------------

# 6. Recall (Sensitivity)

Recall answers:

> Out of all actual positives, how many did the model detect?

Formula:

Recall = TP / (TP + FN)

### Example

Suppose there were **50 spam emails**.

Model detected **40**.

Recall = 40 / 50 = **80%**

Meaning **10 spam emails were missed**.

------------------------------------------------------------------------

# 7. Precision vs Recall Tradeoff

Sometimes increasing one decreases the other.

Example:

Spam detection system:

-   If we make it **very strict**, it detects all spam (high recall) but
    marks normal emails as spam (low precision).
-   If we make it **very safe**, it rarely marks emails as spam (high
    precision) but misses many spam emails (low recall).

------------------------------------------------------------------------

# 8. F1 Score

F1 Score combines **Precision and Recall** into one metric.

Formula:

F1 Score = 2 × (Precision × Recall) / (Precision + Recall)

It gives a **balanced performance score**.

------------------------------------------------------------------------

# 9. Specificity

Specificity measures:

> Out of all actual negatives, how many were correctly predicted?

Formula:

Specificity = TN / (TN + FP)

Example: Detecting healthy patients correctly in a medical test.

------------------------------------------------------------------------

# 10. ROC Curve

ROC = **Receiver Operating Characteristic Curve**

It plots:

-   **True Positive Rate (Recall)**
-   **False Positive Rate**

By changing the **prediction threshold**.

Example:

If probability \> 0.5 → Positive class

But we can try:

-   0.3
-   0.5
-   0.7

Each threshold gives different performance.

------------------------------------------------------------------------

# 11. AUC (Area Under Curve)

AUC measures the **overall performance of the ROC curve**.

Range:

0 → Worst model\
0.5 → Random guessing\
1 → Perfect model

Higher AUC = **Better model**

------------------------------------------------------------------------

# 12. Imbalanced Dataset

Sometimes one class has **many more samples than the other**.

Example:

Fraud detection:

-   99% Normal transactions
-   1% Fraud

A model predicting **everything as normal** would still give **99%
accuracy**, which is misleading.

So we use:

-   Precision
-   Recall
-   F1 Score
-   ROC AUC

Instead of only accuracy.

------------------------------------------------------------------------

# 13. Multiclass Classification

When we have **more than two classes**.

Example:

Image classification:

-   Car
-   Bus
-   Truck

We use **One vs Rest Strategy**.

Example:

For class "Car":

-   Car → Positive
-   Bus + Truck → Negative

Then compute metrics and repeat for each class.

------------------------------------------------------------------------

# 14. Micro vs Macro Averaging

Used in multiclass problems.

**Micro Average** - Combines all predictions across classes. - Useful
when classes are imbalanced.

**Macro Average** - Computes metric per class then averages. - Treats
all classes equally.

------------------------------------------------------------------------

# Interview Questions & Answers

## 1. What is a Confusion Matrix?

A confusion matrix is a table used to evaluate classification models by
showing True Positives, True Negatives, False Positives, and False
Negatives.

------------------------------------------------------------------------

## 2. What is Accuracy?

Accuracy measures the percentage of correct predictions.

Accuracy = (TP + TN) / Total Samples

------------------------------------------------------------------------

## 3. What is Precision?

Precision measures how many predicted positives are actually correct.

Precision = TP / (TP + FP)

------------------------------------------------------------------------

## 4. What is Recall?

Recall measures how many actual positives were correctly identified.

Recall = TP / (TP + FN)

------------------------------------------------------------------------

## 5. When should we prefer Recall over Precision?

Recall is important when **missing a positive case is dangerous**.

Example: Disease detection or fraud detection.

------------------------------------------------------------------------

## 6. When should we prefer Precision?

Precision is important when **false positives are costly**.

Example: Spam detection or legal document classification.

------------------------------------------------------------------------

## 7. What is F1 Score?

F1 Score is the harmonic mean of Precision and Recall and balances both
metrics.

------------------------------------------------------------------------

## 8. What is ROC Curve?

ROC curve plots True Positive Rate vs False Positive Rate to evaluate
model performance across different thresholds.

------------------------------------------------------------------------

## 9. What is AUC?

AUC (Area Under Curve) measures the overall quality of the ROC curve.
Higher AUC means better model performance.

------------------------------------------------------------------------

## 10. How do you handle imbalanced datasets?

Common methods:

-   Use Precision/Recall instead of accuracy
-   Use F1 Score
-   Use ROC-AUC
-   Apply resampling (oversampling or undersampling)

------------------------------------------------------------------------
