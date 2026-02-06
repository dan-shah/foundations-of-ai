# Deep Learning & AI Learning Hub

A comprehensive, progressive learning curriculum covering foundations through advanced AI topics.

---

## Table of Contents

1. [Part 1: Mathematical Foundations (Weeks 1-3)](#part-1-mathematical-foundations-weeks-1-3)
2. [Part 2: Python Foundations (Week 4)](#part-2-python-foundations-week-4)
3. [Part 3: Neural Network Fundamentals (Weeks 5-8)](#part-3-neural-network-fundamentals-weeks-5-8)
4. [Part 4: Neural Network Architectures (Weeks 9-12)](#part-4-neural-network-architectures-weeks-9-12)
5. [Part 5: Transformers & LLMs (Weeks 13-18)](#part-5-transformers--llms-weeks-13-18)
6. [Part 6: Reinforcement Learning (Weeks 19-22)](#part-6-reinforcement-learning-weeks-19-22)
7. [Part 7: Robotics & Embodied AI (Weeks 23-25)](#part-7-robotics--embodied-ai-weeks-23-25)
8. [Part 8: AI Agents (Weeks 26-28)](#part-8-ai-agents-weeks-26-28)

---

## Part 1: Mathematical Foundations (Weeks 1-3)

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

## Part 2: Python Foundations (Week 4)

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

## Part 3: Neural Network Fundamentals (Weeks 5-8)

### 3.1 Perceptrons & Basic Networks

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

### 3.2 Backpropagation

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

### 3.3 Deep Learning Frameworks

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

### 3.4 Training Deep Networks

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

## Part 4: Neural Network Architectures (Weeks 9-12)

### 4.1 Convolutional Neural Networks (CNNs)

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

### 4.2 Recurrent Neural Networks (RNNs)

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

### 4.3 Attention Mechanisms

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

## Part 5: Transformers & LLMs (Weeks 13-18)

### 5.1 Transformer Architecture

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

### 5.2 Language Models

**Concepts:**
- Tokenization (BPE, WordPiece, SentencePiece)
- Autoregressive language modeling
- GPT architecture (decoder-only)
- BERT and bidirectional models (encoder-only)

**Learning Objectives:**
- [ ] Implement BPE tokenization
- [ ] Understand the difference between GPT and BERT
- [ ] Train a small GPT-style model
- [ ] Fine-tune BERT for classification

**Practical Exercises:**
- Build a BPE tokenizer from scratch
- Train a mini-GPT on a text corpus
- Fine-tune BERT for sentiment analysis
- Compare masked vs causal language modeling

**Key Project:** Train a small language model (~10M parameters) on a custom dataset

---

### 5.3 Embeddings

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

### 5.4 Fine-tuning & PEFT

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

## Part 6: Reinforcement Learning (Weeks 19-22)

### 6.1 RL Fundamentals

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

### 6.2 Q-Learning

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

### 6.3 Policy Gradient Methods

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

### 6.4 RL Projects

**Projects:**
1. **Game Playing Agent:** Train an agent to play a classic game
2. **Continuous Control:** Solve MuJoCo tasks (Hopper, Walker)
3. **Multi-Agent RL:** Simple competitive or cooperative environment

---

## Part 7: Robotics & Embodied AI (Weeks 23-25)

### 7.1 Robot Learning Basics

**Concepts:**
- Simulation environments (PyBullet, MuJoCo, Isaac Gym)
- Sensor data processing (cameras, lidar, proprioception)
- Motor control and action spaces
- Reward shaping for robotics

**Learning Objectives:**
- [ ] Set up a robot simulation environment
- [ ] Process sensor observations
- [ ] Design reward functions for robot tasks
- [ ] Train a simple locomotion policy

**Practical Exercises:**
- Set up PyBullet environment
- Train a robot arm to reach targets
- Implement basic locomotion controller
- Experiment with reward shaping

---

### 7.2 Imitation Learning

**Concepts:**
- Behavioral cloning
- Dataset aggregation (DAgger)
- Inverse reinforcement learning (IRL)
- Learning from demonstrations

**Learning Objectives:**
- [ ] Collect and process demonstration data
- [ ] Train a policy via behavioral cloning
- [ ] Understand the distribution shift problem
- [ ] Apply IRL to recover reward functions

**Practical Exercises:**
- Collect demonstrations for a simple task
- Implement behavioral cloning
- Compare BC with RL from scratch
- Experiment with DAgger

---

### 7.3 Sim-to-Real Transfer

**Concepts:**
- The reality gap
- Domain randomization
- System identification
- Adaptive methods

**Learning Objectives:**
- [ ] Understand challenges of sim-to-real transfer
- [ ] Implement domain randomization
- [ ] Design robust policies
- [ ] Evaluate transfer performance

**Practical Exercises:**
- Train with domain randomization
- Analyze policy robustness to perturbations
- Compare randomization strategies

---

## Part 8: AI Agents (Weeks 26-28)

### 8.1 Agent Architectures

**Concepts:**
- ReAct pattern (Reasoning + Acting)
- Tool use and function calling
- Memory systems (short-term, long-term, episodic)
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

### 8.2 Building Agents

**Concepts:**
- Agent frameworks (LangChain, LlamaIndex, custom)
- Retrieval-augmented generation (RAG)
- Multi-agent systems
- Agent evaluation and debugging

**Learning Objectives:**
- [ ] Build agents with LangChain/LlamaIndex
- [ ] Implement RAG for knowledge-grounded agents
- [ ] Design multi-agent collaboration
- [ ] Evaluate agent performance

**Practical Exercises:**
- Build a RAG-based Q&A agent
- Create a research assistant agent
- Implement agent-to-agent communication
- Build evaluation harnesses

---

### 8.3 Capstone Project

**Design and build a complete AI agent system:**

**Options:**
1. **Research Assistant:** An agent that can search papers, summarize findings, and answer questions
2. **Code Assistant:** An agent that can write, debug, and explain code
3. **Task Automation Agent:** An agent that can break down complex tasks and execute them
4. **Multi-Modal Agent:** An agent that can process and generate text, images, and code

**Requirements:**
- Clear problem definition
- Architecture design document
- Implementation with proper abstractions
- Evaluation on realistic tasks
- Documentation and demo

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

*This curriculum is designed to be completed over approximately 28 weeks with dedicated study. Adjust pacing based on your background and available time.*
