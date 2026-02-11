# 📘 PART-1  :  
## Probability Density Function Learning using Roll-Number-Based Non-Linear Transformation

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
---

# PART-2 : Learning PDF using GAN (Data-Driven Approach)

## 📖 Objective

In this part, no analytical form of the probability density function is assumed.

The objective is to learn the distribution of the transformed variable $z$ directly from data using a Generative Adversarial Network (GAN).

Unlike Part-1, this approach does not assume a Gaussian distribution and instead models the density implicitly using neural networks.

--- 
###  Transformation  ( completely previously)

### 🧠 Step 2: GAN Architecture Design

A Generative Adversarial Network (GAN) was designed to learn the distribution of $z$.

The GAN consists of two neural networks:

####  1️⃣ Generator (G)

The Generator:

Takes random noise $\epsilon \sim \mathcal{N}(0,1)$ as input

Produces synthetic samples $z_f$

Learns to approximate the true data distribution

Input: Random noise vector
Output: Generated $z$ sample

#### 2️⃣ Discriminator (D)

The Discriminator:

Receives either real $z$ samples or fake $z_f$ samples

Outputs probability of being real

Input: 1-D sample
Output: Probability (real or fake)

#### ⚙️ Training Procedure

During training:

The Discriminator learns to distinguish real and fake samples.

The Generator learns to fool the Discriminator.

Both networks are optimized using Binary Cross-Entropy loss.

Training is performed iteratively until the generated samples resemble the real distribution.

### 📊 Step 3: PDF Approximation from Generator

After training:

A large number of synthetic samples $z_f$ were generated.

The probability density was estimated using:

Histogram Density Estimation

The learned distribution was compared with the real data distribution.

--- 
###  📈 Observations

#### 🔹Mode Coverage

The generator was able to capture the primary modes of the distribution.  Minor deviations were observed in regions with low data density.

#### 🔹 Training Stability

During training:

- Loss values oscillated initially

- Gradual stabilization was observed after sufficient epochs

- No severe mode collapse was detected

#### 🔹 Quality of Generated Distribution

The generated distribution closely followed the shape of the real transformed data.
Small discrepancies exist due to training limitations and finite sample size.
---
### ⚖️ Comparison of Methods

| Analytical Method (Part-1)       | GAN Method (Part-2)        |
| -------------------------------- | -------------------------- |
| Assumes Gaussian distribution    | No distribution assumption |
| Closed-form parameter estimation | Neural network training    |
| Fast computation                 | Computationally intensive  |
| Parametric model                 | Non-parametric model       |

### 🎯  Conclusion

This project demonstrates two distinct approaches to probability density estimation:

Parametric estimation using analytical Gaussian assumptions

Non-parametric learning using Generative Adversarial Networks

The comparison highlights the difference between theoretical modeling and data-driven learning methods.

The GAN-based method provides flexibility in modeling complex distributions without assuming any predefined functional form.