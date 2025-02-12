---
layout: page
title: Introduction to Deep Learning
nav_order: 3
---
# Introduction to Deep Learning
{: .no_toc}



## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## 1. Introduction to Deep Learning

### 1.1 What is Deep Learning?
- **Definition:** Deep Learning (DL) is a subfield of Machine Learning (ML) that leverages deep neural networks to model complex patterns in data.
- **Key Idea:** Automatically learn representations from data, eliminating the need for manual feature engineering.
- **Three Key Components:**
  1. **Predictive Function (Model Architecture):** How we define the mapping from input data to output predictions.
  2. **Goodness Score (Loss Function):** A scalar measure that quantifies how well the predictive function performs.
  3. **Learning Procedure (Optimization):** The process (typically using gradient descent and backpropagation) to adjust the model parameters to minimize the loss.

### 1.2 Why Deep Learning?
- **Reduction in Human Effort:** No need for extensive manual feature extraction.
- **Handling Complex Problems:** Capable of modeling intricate, non-linear relationships.
- **Data Abundance & Compute Power:** The modern era features vast amounts of data and advanced hardware (GPUs, TPUs) to train large networks.

### 1.3 Why Now?
- **Hardware Advances:** Modern GPUs and distributed computing have made training deep networks feasible.
- **Algorithmic Improvements:** Better training techniques, architectures, and optimizers.
- **Data Explosion:** An abundance of digital data from varied sources is now available.

### 1.4 Hard Parts in Deep Learning
- **Problem Formulation:** Correctly framing the problem.
- **Data Collection & Preprocessing:** Gathering and preparing high-quality data.
- **Model Tuning:** Selecting appropriate architectures and hyperparameters to avoid overfitting and underfitting.

### 1.5 Recent and Interesting Applications
- Face Recognition
- Text-to-Speech
- Machine Translation
- Medical Diagnosis
- Self-driving Cars
- Game Playing (AlphaGo)
- Chatbots (ChatGPT, Gemini)
- Text-to-Image/Video Generators (DALL-E2, Imagen)**

---

## 2. Neural Networks

### 2.1 The Neuron: Building Block of Neural Networks

#### Layman Definition:
- **Inspiration:** Modeled after the human brain's neurons.
- **Function:** Receives multiple inputs, applies a transformation, and outputs a signal.

#### Brief History:
- Early work on perceptrons in the 1950s laid the foundation.
- Modern neural networks now comprise many layers (deep architectures) to model complex data.

#### Mathematical Definition:
- **Linear Combination:**
  $$ z = w^T x + b $$
  - $$ x $$: Input vector.
  - $$ w $$: Weight vector.
  - $$ b $$: Bias term.
- **Activation Function:**
  $$ a = \sigma(z) $$
  - $$ \sigma $$ could be a sigmoid, ReLU, tanh, or another non-linear function.

### 2.2 Neural Network Architecture

#### Layman Terms:
- **Structure:** Neurons are organized into layers:
  - **Input Layer:** Receives the raw data.
  - **Hidden Layers:** Extract and combine features.
  - **Output Layer:** Provides the final prediction.

#### Mathematical Formulation:
- For a given layer $$ l $$:
  - **Linear Step:**
    $$ Z^{[l]} = W^{[l]} a^{[l-1]} + b^{[l]} $$
  - **Activation Step:**
    $$ a^{[l]} = \sigma(Z^{[l]}) $$
  - Here, $$ a^{[l-1]} $$ is the activation from the previous layer.

#### Visualization
[Neural Network Visualization](https://playground.tensorflow.org/)

### 2.3 Why Are Neural Networks Powerful?
- **Automatic Feature Extraction:** They learn hierarchical features directly from raw data.
- **Universal Approximation Theorem:**  
  A neural network with one hidden layer can approximate any continuous function on compact subsets of $$ \mathbb{R}^n $$, given a sufficient number of neurons.

---

## 3. Loss Functions

### 3.1 What is a Loss Function?
- **Definition:** A loss function measures the error between the predicted outputs of a model and the actual target values.
- **Purpose:** It provides a scalar "goodness" score that guides the learning process.

### 3.2 Common Loss Functions

#### Mean Squared Error (MSE) for Regression:
- **Formula:**
  $$ \text{MSE} = \frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2 $$
  where $$ y_i $$ is the true value and $$ \hat{y}_i $$ is the predicted value.

#### Binary Cross-Entropy for Classification:
- **Formula:**
  $$ L = -\left[ y \log(\hat{y}) + (1 - y) \log(1 - \hat{y}) \right] $$
  where $$ y $$ is the true label (0 or 1) and $$ \hat{y} $$ is the predicted probability.

### 3.3 Logistic Regression Example: Cat Detection (Binary Classification)
- **Model Equation:**
  $$ \hat{y} = \sigma(w^T x + b) $$
- **Activation:**
  $$ \sigma(z) = \frac{1}{1 + e^{-z}} $$
- **Loss:** Use the binary cross-entropy loss defined above.

### 3.4 Extending to Multi-Class Classification: Cat, Dog, Lion
- **Model Setup:** Have an output for each class.
- **Softmax Activation:**
  - For each class $$ j $$:
    $$ z_j = w_j^T x + b_j $$
    $$ \text{softmax}(z_j) = \frac{e^{z_j}}{\sum_{k} e^{z_k}} $$
- **Loss Function:**
  - Cross-Entropy Loss for multi-class:
    $$ L = -\sum_{j} y_j \log(\hat{y}_j) $$
  where $$ y_j $$ indicates the true class and $$ \hat{y}_j $$ is the predicted probability for class $$ j $$.

---

## 4. Neural Networks in the Cat Example

### 4.1 Replacing the Linear Model with a Deep Neural Network
- **Traditional Linear Model:**
  $$ \hat{y} = \sigma(w^T x + b) $$
- **Deep Neural Network (with 1 Hidden Layer):**
  - **Hidden Layer Computation:**
    $$ Z^{[1]} = W^{[1]} x + b^{[1]} $$; 
    $$ a^{[1]} = \sigma(Z^{[1]}) $$
  - **Output Layer Computation:**
    $$ Z^{[2]} = W^{[2]} a^{[1]} + b^{[2]} $$; 
    $$ \hat{y} = \sigma(Z^{[2]}) $$
- **Interpretation:** The hidden layer allows the network to learn more complex, non-linear features from the input before making the final prediction.

---

## 5. Optimization: Gradient Descent and Backpropagation

### 5.1 Gradient Descent

#### Intuition:
- **Objective:** Minimize the loss function by adjusting the model parameters.
- **Method:** Iteratively update the parameters in the opposite direction of the gradient.

#### Pseudocode:
Initialize parameters (weights and biases) For each iteration: 
1. Compute the loss L on a mini-batch of data 
2. Compute gradients: dL/dw and dL/db 
3. Update parameters: w = w - α * (dL/dw) b = b - α * (dL/db)
where $$ \alpha $$ is the learning rate.

### 5.2 Backpropagation

#### Why Backpropagation?
- **Efficiency:** Deep networks require an efficient way to compute the gradients for all parameters.
- **Mechanism:** Uses the chain rule to propagate errors from the output back to the input layer.

#### How It Works:
- **Chain Rule Concept:**  
  For a parameter $$ \theta $$ that affects the loss $$ L $$ through an intermediate variable $$ z $$:
  $$ \frac{\partial L}{\partial \theta} = \frac{\partial L}{\partial z} \cdot \frac{\partial z}{\partial \theta} $$
- **Step-by-Step Process:**
  1. **Forward Pass:** Compute all intermediate activations $$ Z^{[l]} $$ and $$ a^{[l]} $$ for each layer.
  2. **Backward Pass:** Starting at the output layer, compute the gradient (error term) and propagate it backwards.

#### Worked Example: Cat Detection with a 1 Hidden Layer
- **Output Layer (Layer 2):**
  - **Error Term:**
    $$ \delta^{[2]} = \frac{\partial L}{\partial Z^{[2]}} $$
    For binary cross-entropy with sigmoid activation:
    $$ \delta^{[2]} = \hat{y} - y $$
  - **Gradients:**
    - Weights:
      $$ \frac{\partial L}{\partial W^{[2]}} = \delta^{[2]} (a^{[1]})^T $$
    - Biases:
      $$ \frac{\partial L}{\partial b^{[2]}} = \delta^{[2]} $$

- **Hidden Layer (Layer 1):**
  - **Error Propagation:**
    $$ \delta^{[1]} = (W^{[2]})^T \delta^{[2]} \circ \sigma'(Z^{[1]}) $$
    where $$ \circ $$ denotes element-wise multiplication.
  - **Gradients:**
    - Weights:
      $$ \frac{\partial L}{\partial W^{[1]}} = \delta^{[1]} \, x^T $$
    - Biases:
      $$ \frac{\partial L}{\partial b^{[1]}} = \delta^{[1]} $$

---

## 6. Summary and Tying Everything Together: Cat Detection with a 1 Hidden Layer Neural Network

### 6.1 Model Architecture
- **Input Layer:**  
  Receives raw image data (features).
- **Hidden Layer:**  
  - Computation:
    $$ Z^{[1]} = W^{[1]} x + b^{[1]} $$
    $$ a^{[1]} = \sigma(Z^{[1]}) $$
- **Output Layer:**  
  - Computation:
    $$ Z^{[2]} = W^{[2]} a^{[1]} + b^{[2]} $$
    $$ \hat{y} = \sigma(Z^{[2]}) $$

### 6.2 Loss Function
- **Binary Cross-Entropy Loss:**
  $$ L = -\left[ y \log(\hat{y}) + (1-y) \log(1-\hat{y}) \right] $$

### 6.3 Learning Procedure (Optimization)
- **Step 1:** **Forward Pass**  
  Compute activations $$ Z^{[1]}, a^{[1]}, Z^{[2]}, \hat{y} $$.
- **Step 2:** **Loss Computation**  
  Evaluate the loss $$ L $$ using the predicted $$ \hat{y} $$ and the true label $$ y $$.
- **Step 3:** **Backward Pass**  
  Use backpropagation to compute gradients for all parameters.
- **Step 4:** **Parameter Update**  
  Adjust weights and biases using gradient descent:
  $$ w \leftarrow w - \alpha \nabla_w L $$
  $$ b \leftarrow b - \alpha \nabla_b L $$
- **Step 5:** **Iteration**  
  Repeat for multiple epochs until convergence.

### 6.4 Overall Workflow Recap
1. **Model Definition:** Choose a neural network architecture (e.g., 1 hidden layer for cat detection).
2. **Loss Specification:** Define a loss function (binary cross-entropy for binary classification).
3. **Learning Mechanism:** Optimize the model parameters via gradient descent with backpropagation.
4. **Training Process:** Iteratively perform forward and backward passes to minimize the loss.

---

## Final Remarks
- **Deep Learning** integrates a clear model (neural network architecture), a quantifiable loss function, and an efficient optimization procedure.
- **Neural Networks** provide powerful, flexible architectures that automatically extract features.
- **Loss Functions** guide the model toward making better predictions.
- **Optimization via Gradient Descent and Backpropagation** allows the model to learn from data effectively.
- The **Cat Detection Example** illustrates these concepts, showing how a simple 1 hidden layer network is designed, trained, and optimized.