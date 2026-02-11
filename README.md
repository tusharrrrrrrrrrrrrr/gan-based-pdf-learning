# Learning PDF using GAN (Data-Driven Approach)

## 📖 Objective

This project focuses on learning the probability density of a transformed real-world dataset using a Generative Adversarial Network (GAN).

Instead of assuming a predefined distribution, the model learns the density directly from data using adversarial training.

The objective of this assignment is to:

- Apply a roll-number-based non-linear transformation to NO₂ data

- Learn the probability distribution of the transformed variable

- Train a GAN to generate samples from the learned distribution

- Compare real and generated distributions

--- 
### 📊 Dataset Information

#### Dataset: India Air Quality Data
#### Source: Kaggle
#### Feature Used: NO₂ (Nitrogen Dioxide concentration)

The NO₂ feature is selected as the primary variable 
𝑥.
Missing values are removed before performing transformation.

---
#### Step 1: Non-Linear Transformation

Each NO₂ value $x$ is transformed into:

$$
z = x + a_r \sin(b_r x)
$$

Where:

$$
a_r = 0.5 \times (r \bmod 7)
$$

$$
b_r = 0.3 \times (r \bmod 5 + 1)
$$

### Here:

- $r$ is the university roll number  
- $\bmod$ represents the modulo operation  

The transformed values $z$ are treated as samples from an unknown probability distribution.


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

- Loss Function: Binary Cross-Entropy

- Optimizer: Adam

- Training Strategy: Alternating updates of Generator and Discriminator

- Epochs: (mention your value)

- Batch Size: (mention your value)

Training continues until the generated distribution closely matches the real distribution.

### 📊 Step 3: PDF Approximation from Generator

After training:

- A large number of synthetic samples $z_f$ were generated.

- The probability density was estimated using:

- Histogram Density Estimation

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

### 🛠 Implementation Tools

- Python

- NumPy

- Pandas

- Matplotlib

- PyTorch

- Google Colab

--- 

### 🎯  Conclusion

This project demonstrates a non-parametric approach to probability density estimation using Generative Adversarial Networks.

Unlike traditional parametric modeling, GANs learn complex data distributions directly from samples without assuming a predefined functional form.

The assignment highlights practical application of adversarial learning for density modeling.

--- 
### 📚 References

- Goodfellow et al., Generative Adversarial Networks (2014)

- Kaggle: India Air Quality Datase