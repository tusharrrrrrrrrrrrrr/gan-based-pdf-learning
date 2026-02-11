# 📘  Probability Density Function Learning using Roll-Number-Based Non-Linear Transformation

## 📖  Project Description

This project focuses on applying a personalized non-linear transformation to real-world air quality data and estimating the parameters of a probability density function (PDF).

The objective of this assignment is to:

Apply a roll-number-based non-linear transformation to NO₂ data.

Model the transformed data using a Gaussian probability density function.

Estimate the parameters of the distribution using statistical methods.

Understand how real-world data behaves under mathematical transformation.
---

## 📊 Dataset Information

Dataset: India Air Quality Data

Source: Kaggle

Feature Used: NO₂ (Nitrogen Dioxide concentration)

The NO₂ feature was selected as the primary variable 𝑥. 
Missing values were removed before performing mathematical operations to ensure accurate estimation.
---

## 🔄 Step 1: Non-Linear Transformation

Each NO₂ value $x$ was transformed into a new variable $z$ using the transformation:

$$
z = x + a_r \sin(b_r x)
$$

Where:

$$
a_r = 0.05 \times (r \bmod 7)
$$

$$
b_r = 0.3 \times (r \bmod 5 + 1)
$$

Here:

- $r$ is the university roll number  
- $\bmod$ represents the modulo (remainder) operation  

This transformation introduces controlled non-linearity into the dataset and makes the model personalized to the roll number.

--- 
## 📈 Step 2: Probability Density Function Modeling

The transformed variable $z$ was assumed to follow the probability density function:

$$
\hat{p}(z) = c\, e^{-\lambda (z - \mu)^2}
$$

This expression represents a Gaussian-type distribution.

--- 
## 🧮 Step 3: Parameter Estimation

The parameters of the distribution were estimated using the following statistical formulas:

---

### 1️⃣ Mean ($\mu$)

$$
\mu = \frac{1}{n} \sum_{i=1}^{n} z_i
$$

The mean represents the central tendency of the transformed data.

---

### 2️⃣ Variance ($\sigma^2$)

$$
\sigma^2 = \frac{1}{n} \sum_{i=1}^{n} (z_i - \mu)^2
$$

Variance measures the spread of the data.

---

### 3️⃣ Lambda ($\lambda$)

From the Gaussian form:

$$
\lambda = \frac{1}{2\sigma^2}
$$

---

### 4️⃣ Normalization Constant ($c$)

$$
c = \frac{1}{\sqrt{2\pi\sigma^2}}
$$

The constant $c$ ensures that the total probability integrates to 1.

---
## 🛠 Implementation Tools

The following tools and libraries were used in this project:

- **Python** 
- **NumPy** 
- **Pandas** 
- **Matplotlib**
- **Google Colab** 

---
## 📊 Final Estimated Parameters

After performing the transformation and estimation, the learned parameters are:

- **Mean ($\mu$)** = 25.8163  
- **Lambda ($\lambda$)** = 0.00146  
- **Normalization Constant ($c$)** = 0.02156  

These parameters define the estimated probability density function for the transformed NO₂ data.
---

## 📌 Key Concepts Applied

- Non-linear transformation

- Modulo arithmetic

- Gaussian distribution

- Probability density functions

- Maximum Likelihood Estimation (MLE)

- Statistical parameter learning
---
## 🎯 Conclusion

This project demonstrates how real-world environmental data can be mathematically transformed and modeled using probability theory.

By applying a roll-number-dependent transformation and estimating Gaussian parameters, the assignment strengthens understanding of:

Statistical modeling

Distribution fitting

Mathematical transformation of data

Practical application of probability theory

The experiment highlights how theoretical probability concepts can be applied to real datasets for parameter estimation and modeling.

---

## 📚 References

- Kaggle: India Air Quality Dataset

- Standard Gaussian Distribution Theory

- Probability and Statistics Concepts