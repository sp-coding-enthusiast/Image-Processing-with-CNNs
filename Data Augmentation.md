# CNN Data Augmentation and Dataset Splitting (Simple Notes)

## 1. What Happens After Data Collection?

After collecting image data for a CNN model, we usually perform:

1.  Noise removal
2.  Image enhancement
3.  Preprocessing
4.  Data augmentation
5.  Train / Validation / Test split

These steps help the model learn better and perform well in real-world
scenarios.

------------------------------------------------------------------------

# 2. Data Augmentation (Simple Explanation)

Data augmentation means **creating more training images from existing
images by applying small transformations**.

Instead of collecting thousands of new images (which is difficult), we
modify existing images slightly.

This helps the model learn **different variations of the same object**.

### Example

Suppose we are building a **Cat vs Dog classifier**.

Original image:

Cat sitting straight.

Now we create new versions:

-   Rotated cat image
-   Cropped cat image
-   Blurred cat image
-   Color adjusted cat image
-   Flipped cat image

Even though it is the **same cat**, these look slightly different.

To the CNN model, these behave like **new training examples**.

------------------------------------------------------------------------

# 3. Why Data Augmentation is Important

Data augmentation helps when:

### 1. Dataset is Small

Example:

Car images = 1000\
Bus images = 900\
Truck images = 20

The model learns cars and buses well but **fails to recognize trucks**.

Solution:

Generate more truck images using transformations.

### 2. Prevent Overfitting

Without augmentation, the model memorizes training images.

Augmentation introduces variation so the model **learns patterns instead
of memorizing**.

### 3. Improve Generalization

Real-world images may have:

-   Different lighting
-   Different camera angles
-   Different object positions

Augmentation prepares the model for such variations.

------------------------------------------------------------------------

# 4. Common Data Augmentation Techniques

## 1. Geometric Transformations

These change the shape or position of the object.

Examples:

-   Rotation
-   Cropping
-   Scaling
-   Flipping
-   Elastic deformation

Example:

A car image rotated 30° is still a car.

------------------------------------------------------------------------

## 2. Color Space Transformations

These change image color properties.

Examples:

-   Changing brightness
-   Adjusting contrast
-   Modifying RGB values
-   Hue/Saturation changes

Example:

A cat photographed during day vs evening lighting.

------------------------------------------------------------------------

## 3. Filtering Techniques

These simulate camera or environmental noise.

Examples:

-   Blur
-   Sharpening
-   Noise injection

Example:

Blurry CCTV images.

------------------------------------------------------------------------

## 4. Advanced Augmentation (Using GANs)

Advanced models like **GANs (Generative Adversarial Networks)** can
generate completely new images.

Example:

Generate synthetic faces or vehicles.

These look realistic and increase dataset size.

------------------------------------------------------------------------

# 5. Dataset Splitting

After preparing data, we split the dataset into three parts.

## 1. Training Data

Used to **teach the model**.

The model adjusts its weights and biases using this data.

Typical size:

70% -- 80% of dataset

Example:

If dataset has 10,000 images:

8000 used for training.

------------------------------------------------------------------------

## 2. Validation Data

Used to **check how well the model is learning during training**.

After each training cycle (epoch), the model is tested on validation
data.

This helps us detect:

-   Overfitting
-   Underfitting
-   Performance improvement

Typical size:

10% -- 15%

Example:

1000 images used for validation.

------------------------------------------------------------------------

## 3. Test Data

Used only **after training is complete**.

The model has **never seen this data before**.

This simulates **real-world performance**.

Typical size:

10% -- 20%

Example:

1000 images used for testing.

------------------------------------------------------------------------

# 6. Example Dataset Split

Dataset size = 10,000 images

Training = 7000\
Validation = 1500\
Test = 1500

Flow:

Training → Learn patterns\
Validation → Check learning progress\
Test → Final evaluation

------------------------------------------------------------------------

# 7. Important Rule

Never mix test data with training data.

If the model sees test data during training:

The evaluation becomes **unreliable**.

This is called **data leakage**.

------------------------------------------------------------------------

# 8. Real World Analogy

Think of preparing for an exam.

Training set → Studying books and examples.

Validation set → Practice tests during preparation.

Test set → Final exam.

If you practice using the final exam questions beforehand, the result is
meaningless.

------------------------------------------------------------------------

# 9. Interview Questions and Answers

## Q1: What is Data Augmentation?

**Answer:**

Data augmentation is the process of increasing training data by applying
transformations like rotation, cropping, flipping, or color changes to
existing images.

It improves model generalization and prevents overfitting.

------------------------------------------------------------------------

## Q2: Why is data augmentation used in CNN?

**Answer:**

It is used to:

-   Increase dataset size
-   Balance imbalanced datasets
-   Improve model robustness
-   Reduce overfitting

------------------------------------------------------------------------

## Q3: Give examples of augmentation techniques.

**Answer:**

Common techniques include:

-   Rotation
-   Cropping
-   Scaling
-   Flipping
-   Brightness adjustment
-   Blur filtering

------------------------------------------------------------------------

## Q4: What is the difference between training, validation, and test datasets?

**Answer:**

Training set is used to train the model.\
Validation set checks model performance during training.\
Test set evaluates the final performance on unseen data.

------------------------------------------------------------------------

## Q5: What happens if test data is used during training?

**Answer:**

This leads to **data leakage**, and the model's performance evaluation
becomes unreliable.

------------------------------------------------------------------------

## Q6: What is an imbalanced dataset?

**Answer:**

An imbalanced dataset occurs when some classes have significantly more
samples than others.

Example:

Car = 1000 images\
Bus = 900 images\
Truck = 20 images

This causes the model to perform poorly on underrepresented classes.

------------------------------------------------------------------------

# 10. Key Takeaways

-   Data augmentation creates new training examples.
-   It improves generalization and reduces overfitting.
-   Dataset must be split into training, validation, and test sets.
-   Test data should remain unseen during training.
