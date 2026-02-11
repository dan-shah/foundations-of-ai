# Deep Learning & AI Learning Hub

A comprehensive, progressive learning curriculum covering foundations through advanced AI topics.

---

## Table of Contents

1. [Part 1: Mathematical Foundations (Weeks 1-2)](#part-1-mathematical-foundations-weeks-1-2)
2. [Part 2: Programming Foundations (Week 3)](#part-2-programming-foundations-week-3)
3. [Part 3: Classical ML & Optimization (Weeks 4-5)](#part-3-classical-ml--optimization-weeks-4-5)
4. [Part 4: Neural Network Fundamentals (Weeks 6-9)](#part-4-neural-network-fundamentals-weeks-6-9)
5. [Part 5: Neural Network Architectures (Weeks 10-13)](#part-5-neural-network-architectures-weeks-10-13)
6. [Part 6: Transformers & LLMs (Weeks 14-19)](#part-6-transformers--llms-weeks-14-19)
7. [Part 7: Reinforcement Learning (Weeks 20-23)](#part-7-reinforcement-learning-weeks-20-23)
8. [Part 8: Applied AI Systems (Weeks 24-27)](#part-8-applied-ai-systems-weeks-24-27)
9. [Part 9: Advanced Topics (Weeks 28-30)](#part-9-advanced-topics-weeks-28-30)

---

## Part 1: Mathematical Foundations (Weeks 1-2)

### 1.1 Linear Algebra Refresher

**Concepts:**
- Vectors, matrices, and tensors
- Matrix operations (multiplication, transpose, inverse)
- Eigenvalues and eigenvectors
- Singular Value Decomposition (SVD)

**Learning Objectives:**
- [ ] Understand vector spaces and linear transformations
- [ ] Perform matrix operations fluently with NumPy
- [ ] Explain the geometric intuition behind eigendecomposition
- [ ] Apply SVD to dimensionality reduction

**Practical Exercises:**
- Implement matrix multiplication from scratch
- Visualize linear transformations in 2D
- Use SVD for image compression
- Build a simple recommender system using matrix factorization

**Resources:**
- 3Blue1Brown: Essence of Linear Algebra (YouTube)
- Linear Algebra Done Right (Axler)
- NumPy documentation

---

### 1.2 Calculus Refresher

**Concepts:**
- Derivatives and partial derivatives
- Chain rule (critical for backpropagation)
- Gradients and gradient descent
- Multivariable calculus concepts

**Learning Objectives:**
- [ ] Compute partial derivatives of multivariate functions
- [ ] Apply the chain rule to composite functions
- [ ] Understand gradients as directions of steepest ascent
- [ ] Implement gradient descent from scratch

**Practical Exercises:**
- Manually compute gradients for simple neural network layers
- Implement gradient descent to minimize functions
- Visualize gradient fields and optimization paths
- Compare different step sizes and their effects

**Resources:**
- 3Blue1Brown: Essence of Calculus (YouTube)
- Khan Academy Multivariable Calculus

---

### 1.3 Probability & Statistics

**Concepts:**
- Probability distributions (Gaussian, Bernoulli, Categorical)
- Bayes' theorem
- Maximum likelihood estimation (MLE)
- Information theory basics (entropy, KL divergence)

**Learning Objectives:**
- [ ] Work with common probability distributions
- [ ] Apply Bayes' theorem to update beliefs
- [ ] Derive MLE estimators for simple distributions
- [ ] Calculate entropy and KL divergence

**Practical Exercises:**
- Implement a Naive Bayes classifier from scratch
- Estimate parameters using MLE
- Visualize different probability distributions
- Calculate information gain for decision trees

**Resources:**
- StatQuest (YouTube)
- Think Bayes (Allen Downey)

---

---

## Part 2: Programming Foundations (Week 3)

### 2.1 Python OOP Refresher

**Concepts:**
- Classes and objects
- Inheritance and composition
- Magic methods (`__init__`, `__call__`, `__repr__`, `__getitem__`)
- Decorators and context managers
- Type hints

**Learning Objectives:**
- [ ] Design clean class hierarchies
- [ ] Use magic methods to create Pythonic APIs
- [ ] Write and use decorators
- [ ] Add type hints for better code documentation

**Practical Exercises:**
- Build a `Tensor` class with operator overloading
- Create a `@timer` decorator for profiling
- Implement a dataset class with `__getitem__` and `__len__`
- Use `@dataclass` for configuration objects

---

### 2.2 Scientific Python Stack

**Concepts:**
- NumPy deep dive (broadcasting, advanced indexing, ufuncs)
- Matplotlib for visualization
- Pandas basics for data manipulation

**Learning Objectives:**
- [ ] Master NumPy broadcasting rules
- [ ] Create publication-quality plots with Matplotlib
- [ ] Load and manipulate data with Pandas

**Practical Exercises:**
- Implement common operations using broadcasting (no loops)
- Create a visualization dashboard for model metrics
- Build a data preprocessing pipeline

---

## Part 3: Classical ML & Optimization (Weeks 4-5)

### 3.1 Classical Machine Learning

**Concepts:**
- Decision trees, random forests, gradient boosting (XGBoost)
- Support vector machines and kernel methods
- k-means and DBSCAN clustering
- k-NN and naive Bayes classification
- Model evaluation: cross-validation, ROC curves, confusion matrices

**Learning Objectives:**
- [ ] Build and interpret decision trees
- [ ] Understand ensemble methods (bagging, boosting)
- [ ] Apply SVMs with different kernels
- [ ] Evaluate models with proper metrics and cross-validation
- [ ] Know when classical ML beats deep learning

**Practical Exercises:**
- Train and visualize decision tree boundaries
- Compare random forest vs gradient boosting on tabular data
- Cluster data with k-means and DBSCAN
- Build a complete model evaluation pipeline with ROC curves

---

### 3.2 Optimization & Linear Programming

**Concepts:**
- Linear programming formulation and geometric intuition
- Simplex method (conceptual + implementation)
- Duality theory
- Convex optimization: convex sets, functions, global optimality
- Constrained optimization: Lagrange multipliers, KKT conditions

**Learning Objectives:**
- [ ] Formulate optimization problems mathematically
- [ ] Solve linear programs graphically and with scipy
- [ ] Understand primal-dual relationships
- [ ] Apply Lagrange multipliers to constrained problems
- [ ] Connect optimization to ML (SVM, regularization)

**Practical Exercises:**
- Solve linear programs graphically and verify with scipy
- Implement a simplified simplex method
- Visualize Lagrange multiplier geometry
- Formulate SVM as a constrained optimization problem

---

### 3.3 Optimization Theory for ML

**Concepts:**
- Convergence analysis of gradient descent
- Stochastic gradient descent theory
- Bias-variance tradeoff (formal treatment)
- VC dimension and generalization bounds
- PAC learning framework
- Regularization theory (L1 sparsity, L2 small weights)

**Learning Objectives:**
- [ ] Analyze gradient descent convergence rates
- [ ] Understand bias-variance decomposition formally
- [ ] Explain VC dimension and its role in generalization
- [ ] Derive why L1 gives sparsity and L2 gives small weights
- [ ] Understand why overparameterized networks can generalize

**Practical Exercises:**
- Compare GD vs SGD convergence empirically
- Visualize bias-variance tradeoff as model complexity changes
- Explore L1 vs L2 regularization geometry
- Observe double descent in practice

---

## Part 4: Neural Network Fundamentals (Weeks 6-9)

### 4.1 Perceptrons & Basic Networks

**Concepts:**
- Single neuron (perceptron) from scratch
- Activation functions (sigmoid, tanh, ReLU, softmax)
- Forward propagation
- Loss functions (MSE, cross-entropy)

**Learning Objectives:**
- [ ] Implement a perceptron from scratch
- [ ] Understand the role of nonlinear activations
- [ ] Compute forward pass for a multi-layer network
- [ ] Choose appropriate loss functions for different tasks

**Practical Exercises:**
- Train a perceptron on linearly separable data
- Visualize decision boundaries
- Implement common activation functions
- Compare loss functions on regression vs classification

---

### 4.2 Backpropagation

**Concepts:**
- Computational graphs
- Chain rule in practice
- Implementing backprop from scratch
- Numerical gradient checking

**Learning Objectives:**
- [ ] Draw computational graphs for neural networks
- [ ] Derive gradients using the chain rule
- [ ] Implement backpropagation manually
- [ ] Verify gradients numerically

**Practical Exercises:**
- Build a computational graph library
- Implement backprop for a 2-layer MLP
- Train on MNIST using only NumPy
- Debug gradients using numerical differentiation

**Key Project:** Build a complete neural network library from scratch (forward, backward, update)

---

### 4.3 Deep Learning Frameworks

**Concepts:**
- PyTorch fundamentals
- Tensors and GPU acceleration
- Autograd: automatic differentiation
- `nn.Module` for building models

**Learning Objectives:**
- [ ] Create and manipulate PyTorch tensors
- [ ] Use autograd for automatic gradient computation
- [ ] Build models using `nn.Module`
- [ ] Move computations to GPU

**Practical Exercises:**
- Reimplement the NumPy MLP in PyTorch
- Compare manual vs autograd gradients
- Build custom layers using `nn.Module`
- Profile CPU vs GPU performance

---

### 4.4 Training Deep Networks

**Concepts:**
- Optimizers (SGD, Momentum, Adam, AdamW)
- Regularization (L1, L2, Dropout)
- Batch normalization
- Learning rate scheduling

**Learning Objectives:**
- [ ] Understand the intuition behind different optimizers
- [ ] Apply regularization to prevent overfitting
- [ ] Use batch normalization effectively
- [ ] Implement learning rate schedules

**Practical Exercises:**
- Compare optimizer convergence on a toy problem
- Visualize the effect of regularization
- Implement dropout from scratch
- Train with cosine annealing schedule

---

## Part 5: Neural Network Architectures (Weeks 10-13)

### 5.1 Convolutional Neural Networks (CNNs)

**Concepts:**
- Convolution operations (stride, padding, dilation)
- Pooling layers (max, average)
- Classic architectures (LeNet, AlexNet, VGG, ResNet)
- Skip connections and residual learning

**Learning Objectives:**
- [ ] Implement convolution from scratch
- [ ] Understand receptive fields
- [ ] Build and train CNN architectures
- [ ] Use transfer learning with pretrained models

**Practical Exercises:**
- Implement 2D convolution with NumPy
- Visualize learned filters
- Build LeNet for MNIST
- Fine-tune ResNet for custom image classification

**Key Project:** Image classification on CIFAR-10 achieving >90% accuracy

---

### 5.2 Computer Vision: Beyond Classification

**Concepts:**
- Object detection: anchor boxes, IoU, NMS, YOLO architecture
- Semantic segmentation: FCN, U-Net architecture
- Instance segmentation concepts (Mask R-CNN)
- Vision Transformers (ViT): patch embeddings
- CLIP: connecting vision and language
- Transfer learning for vision tasks

**Learning Objectives:**
- [ ] Implement IoU and non-maximum suppression from scratch
- [ ] Understand YOLO's single-pass detection approach
- [ ] Build a U-Net for semantic segmentation
- [ ] Explain how Vision Transformers process images as patch sequences
- [ ] Use transfer learning for vision tasks

**Practical Exercises:**
- Implement IoU and NMS from scratch
- Build a simplified YOLO-style grid predictor
- Implement a mini U-Net in PyTorch
- Create patch embeddings for Vision Transformers

---

### 5.3 Recurrent Neural Networks (RNNs)

**Concepts:**
- Sequence modeling
- Vanishing and exploding gradients
- LSTM (Long Short-Term Memory)
- GRU (Gated Recurrent Unit)

**Learning Objectives:**
- [ ] Understand the RNN architecture
- [ ] Explain why vanilla RNNs struggle with long sequences
- [ ] Implement LSTM from scratch
- [ ] Apply RNNs to sequence tasks

**Practical Exercises:**
- Implement vanilla RNN and observe gradient issues
- Build LSTM cell from scratch
- Character-level language modeling
- Sentiment analysis on movie reviews

**Key Project:** Text generation using character-level LSTM

---

### 5.4 Attention Mechanisms

**Concepts:**
- Attention intuition (query, key, value)
- Soft attention vs hard attention
- Self-attention
- Multi-head attention

**Learning Objectives:**
- [ ] Understand attention as weighted aggregation
- [ ] Implement scaled dot-product attention
- [ ] Build multi-head attention module
- [ ] Add attention to sequence models

**Practical Exercises:**
- Visualize attention weights
- Implement attention for sequence-to-sequence
- Compare RNN with and without attention
- Build a simple attention-based classifier

---

## Part 6: Transformers & LLMs (Weeks 14-19)

### 6.1 Transformer Architecture

**Concepts:**
- "Attention Is All You Need" paper deep dive
- Positional encoding (sinusoidal, learned)
- Encoder-decoder structure
- Layer normalization and residual connections

**Learning Objectives:**
- [ ] Understand the full transformer architecture
- [ ] Implement positional encoding
- [ ] Build transformer blocks from scratch
- [ ] Train a transformer on a translation task

**Practical Exercises:**
- Implement the full transformer architecture
- Visualize attention patterns
- Train on a small translation dataset
- Experiment with different positional encodings

**Key Project:** Build a transformer from scratch and train on machine translation

---

### 6.2 Embeddings

**Concepts:**
- Word2Vec (Skip-gram, CBOW)
- GloVe: Global Vectors
- Sentence and document embeddings
- Vector databases and similarity search

**Learning Objectives:**
- [ ] Understand how embeddings capture semantics
- [ ] Train word embeddings from scratch
- [ ] Generate sentence embeddings
- [ ] Build a semantic search system

**Practical Exercises:**
- Implement Word2Vec Skip-gram
- Visualize embeddings with t-SNE/UMAP
- Use sentence transformers for similarity
- Build a document search engine

**Key Project:** Create a semantic search system for a document collection

---

### 6.3 Tokenization & Language Model Training

**Concepts:**
- Tokenization algorithms (BPE, WordPiece, SentencePiece)
- Subword tokenization tradeoffs
- Pretraining objectives (causal LM, masked LM)
- Training dynamics: loss curves, learning rate schedules
- Scaling laws (model size, data, compute)

**Learning Objectives:**
- [ ] Implement BPE and WordPiece tokenizers from scratch
- [ ] Understand how tokenization impacts model behavior
- [ ] Train a small language model training loop
- [ ] Explore scaling laws experimentally

**Practical Exercises:**
- Build BPE and WordPiece tokenizers from scratch
- Compare tokenization strategies on different text
- Implement a training loop with learning rate warm-up
- Visualize scaling law relationships

---

### 6.4 Language Models

**Concepts:**
- Autoregressive language modeling
- GPT architecture (decoder-only)
- BERT and bidirectional models (encoder-only)
- Scaling laws and architecture choices

**Learning Objectives:**
- [ ] Understand the difference between GPT and BERT
- [ ] Train a small GPT-style model
- [ ] Fine-tune BERT for classification
- [ ] Choose the right architecture for a task

**Practical Exercises:**
- Train a mini-GPT on a text corpus
- Fine-tune BERT for sentiment analysis
- Compare masked vs causal language modeling

**Key Project:** Train a small language model (~10M parameters) on a custom dataset

---

### 6.5 Fine-tuning & PEFT

**Concepts:**
- Transfer learning for NLP
- Full fine-tuning vs parameter-efficient methods
- LoRA (Low-Rank Adaptation)
- Prompt tuning and prefix tuning

**Learning Objectives:**
- [ ] Fine-tune a pretrained model on custom data
- [ ] Implement LoRA from scratch
- [ ] Compare PEFT methods
- [ ] Understand when to use each approach

**Practical Exercises:**
- Fine-tune GPT-2 on a specific domain
- Implement LoRA and apply to a model
- Compare training efficiency of different methods
- Prompt engineering experiments

---

## Part 7: Reinforcement Learning (Weeks 20-23)

### 7.1 RL Fundamentals

**Concepts:**
- Markov Decision Processes (MDPs)
- States, actions, rewards, policies
- Value functions (V and Q)
- Bellman equations

**Learning Objectives:**
- [ ] Formulate problems as MDPs
- [ ] Understand the Bellman optimality equations
- [ ] Distinguish between model-based and model-free RL
- [ ] Implement policy evaluation and improvement

**Practical Exercises:**
- Solve simple gridworld environments
- Implement value iteration
- Policy iteration from scratch
- Analyze exploration vs exploitation

---

### 7.2 Q-Learning

**Concepts:**
- Tabular Q-learning
- Epsilon-greedy exploration
- Deep Q-Networks (DQN)
- Experience replay and target networks

**Learning Objectives:**
- [ ] Implement Q-learning from scratch
- [ ] Understand why DQN needs experience replay
- [ ] Build and train a DQN
- [ ] Apply DQN to Atari games

**Practical Exercises:**
- Q-learning on FrozenLake
- Implement experience replay buffer
- Build DQN for CartPole
- Train DQN on an Atari game

**Key Project:** Train a DQN agent to play an Atari game

---

### 7.3 Policy Gradient Methods

**Concepts:**
- REINFORCE algorithm
- Variance reduction (baselines)
- Actor-Critic methods
- PPO (Proximal Policy Optimization)

**Learning Objectives:**
- [ ] Derive the policy gradient theorem
- [ ] Implement REINFORCE
- [ ] Build an Actor-Critic agent
- [ ] Understand and implement PPO

**Practical Exercises:**
- REINFORCE on CartPole
- Add baseline to reduce variance
- Implement Advantage Actor-Critic (A2C)
- Train PPO on continuous control tasks

---

### 7.4 PPO & Modern RL

**Concepts:**
- Proximal Policy Optimization (PPO)
- Trust regions and clipping
- RLHF (RL from Human Feedback)
- Modern RL applications

**Learning Objectives:**
- [ ] Understand and implement PPO
- [ ] Explain trust region methods
- [ ] Connect PPO to RLHF for LLM alignment
- [ ] Apply modern RL to practical problems

**Practical Exercises:**
- Implement PPO from scratch
- Compare PPO vs REINFORCE stability
- Simulate a simplified RLHF pipeline
- Train PPO on continuous control tasks

---

## Part 8: Applied AI Systems (Weeks 24-27)

### 8.1 Retrieval-Augmented Generation (RAG)

**Concepts:**
- Document chunking and embedding
- Vector similarity search
- Retrieval pipeline design
- Grounding LLM outputs in source documents

**Learning Objectives:**
- [ ] Build a complete RAG pipeline from scratch
- [ ] Understand chunking strategies and their tradeoffs
- [ ] Implement vector similarity search
- [ ] Evaluate retrieval quality

**Practical Exercises:**
- Build a RAG system from scratch
- Compare chunking strategies
- Implement semantic search with embeddings
- Evaluate retrieval precision and recall

---

### 8.2 AI Agents & Tool Use

**Concepts:**
- ReAct pattern (Reasoning + Acting)
- Tool use and function calling
- Memory systems (short-term, long-term)
- Planning and reasoning chains

**Learning Objectives:**
- [ ] Understand the ReAct paradigm
- [ ] Design tool interfaces for agents
- [ ] Implement memory systems
- [ ] Build agents that can plan multi-step tasks

**Practical Exercises:**
- Implement a simple ReAct loop
- Create tools for an agent (search, calculator, etc.)
- Build a conversation memory system
- Chain-of-thought prompting experiments

---

### 8.3 AI Evaluations

**Concepts:**
- LLM evaluation metrics and benchmarks
- Human evaluation design
- Automated evaluation with LLM-as-judge
- Red teaming and safety evaluation

**Learning Objectives:**
- [ ] Design evaluation frameworks for AI systems
- [ ] Implement automated evaluation pipelines
- [ ] Understand limitations of different eval approaches
- [ ] Build evaluation harnesses

**Practical Exercises:**
- Build an evaluation pipeline for an LLM task
- Compare human vs automated evaluation
- Implement LLM-as-judge evaluation
- Design a red teaming protocol

---

### 8.4 Production Monitoring

**Concepts:**
- ML system monitoring and observability
- Data drift and model degradation
- A/B testing for ML systems
- Incident response and rollback

**Learning Objectives:**
- [ ] Monitor ML systems in production
- [ ] Detect and respond to data drift
- [ ] Design A/B tests for model changes
- [ ] Build alerting and rollback mechanisms

**Practical Exercises:**
- Build a monitoring dashboard
- Implement drift detection
- Design an A/B testing framework
- Simulate production incidents and responses

---

## Part 9: Advanced Topics (Weeks 28-30)

### 9.1 Inference Optimization

**Concepts:**
- KV-cache and attention optimization
- Quantization (INT8, INT4)
- Speculative decoding
- Batching strategies (continuous batching)

**Learning Objectives:**
- [ ] Understand KV-cache mechanics
- [ ] Implement quantization from scratch
- [ ] Explain speculative decoding
- [ ] Optimize inference throughput and latency

**Practical Exercises:**
- Implement KV-cache for transformer inference
- Quantize a model and measure quality tradeoffs
- Build a speculative decoding prototype
- Compare batching strategies

---

### 9.2 ML Systems & Experiment Tracking

**Concepts:**
- Experiment tracking and reproducibility
- Feature stores and data pipelines
- Model versioning and registry
- Distributed training concepts

**Learning Objectives:**
- [ ] Track experiments systematically
- [ ] Design data pipelines for ML
- [ ] Version models and datasets
- [ ] Understand distributed training tradeoffs

**Practical Exercises:**
- Set up experiment tracking
- Build a simple feature store
- Implement model versioning
- Simulate distributed training scenarios

---

### 9.3 Multimodal AI

**Concepts:**
- Vision-language models (CLIP, LLaVA)
- Cross-modal attention and fusion
- Image generation (diffusion models)
- Audio and speech models

**Learning Objectives:**
- [ ] Understand cross-modal representations
- [ ] Implement contrastive learning (CLIP-style)
- [ ] Explain diffusion model fundamentals
- [ ] Build multimodal pipelines

**Practical Exercises:**
- Implement CLIP-style contrastive learning
- Build a simple image-text retrieval system
- Explore diffusion model sampling
- Create a multimodal classification pipeline

---

## Learning Approach

Each topic includes:
- **Conceptual explanations** with intuitive examples
- **Mathematical foundations** where relevant
- **Code implementations** (from scratch when educational)
- **Practical exercises** with increasing difficulty
- **Mini-projects** to demonstrate mastery

## Progress Tracking

Use the checkboxes in each section to track completed learning objectives. Each week should include:

- [ ] Reading/video materials
- [ ] Hands-on coding exercises
- [ ] One mini-project or substantial exercise
- [ ] Review and self-assessment

## Recommended Tools

- **Python 3.10+**
- **PyTorch** (primary deep learning framework)
- **Jupyter Notebooks** (for experimentation)
- **VS Code** (development environment)
- **Git** (version control)
- **Weights & Biases** (experiment tracking)

## Getting Started

1. Ensure your development environment is set up
2. Begin with Part 1: Linear Algebra (even if familiar, the exercises connect to ML)
3. Complete exercises before moving to the next section
4. Build projects to solidify understanding
5. Revisit earlier sections as needed when concepts resurface

---

*This curriculum is designed to be completed over approximately 32 weeks with dedicated study. Adjust pacing based on your background and available time.*
