# Foundations of AI

A comprehensive, hands-on curriculum covering the mathematical foundations, neural network architectures, and modern AI techniques — from linear algebra to transformers and beyond.

**Built to be personalized.** This curriculum is designed so that anyone can adapt it to their interests. Love Formula 1? The dot product becomes setup-track alignment. Into cooking? Vectors become recipes. See [Make It Yours](#make-it-yours) below.

## What This Is

This is an open-source collection of 28 interactive Jupyter notebooks designed to take you from foundational math through building and training modern deep learning models. Every concept is taught with:

- **Intuitive explanations** before formulas
- **Visualizations** for every major concept
- **From-scratch implementations** so you understand what's happening under the hood
- **Practical exercises** with test cases to verify your understanding
- **Connections to real ML** showing why each concept matters
- **Personalizable narrative** that connects abstract math to something you care about

## How to Use This

**Read online:** Browse the chapters in the sidebar. All code output and visualizations are rendered inline.

**Run interactively:** Click the rocket icon ({fa}`rocket`) at the top of any notebook page and select **Colab** to open it in Google Colab with free GPU access. No local setup required.

**Run locally:** Clone the repository and install dependencies:

```bash
git clone https://github.com/dan-shah/foundations-of-ai.git
cd foundations-of-ai
pip install -r requirements.txt
jupyter notebook
```

## Curriculum Overview

| Part | Topics | Notebooks |
|------|--------|-----------|
| **1. Mathematical Foundations** | Linear algebra, calculus, probability & statistics | 01–03 |
| **2. Python Foundations** | OOP for ML, NumPy deep dive | 04–05 |
| **3. Neural Network Fundamentals** | Perceptrons, backpropagation, PyTorch, training | 06–09 |
| **4. Neural Network Architectures** | CNNs, RNNs, attention mechanisms | 10–12 |
| **5. Transformers & LLMs** | Transformer architecture, language models, embeddings, fine-tuning | 13–16 |
| **6. Reinforcement Learning** | RL fundamentals, Q-learning, policy gradients, PPO | 17–20 |
| **7. Applied AI Systems** | RAG, AI agents & tool use, evaluations, production monitoring | 21–24 |
| **8. Advanced Topics** | Tokenization & LM training, inference optimization, ML systems, multimodal AI | 25–28 |

## Make It Yours

The entire curriculum can be personalized to **your** interest using the personalization guide in [`skill.md`](skill.md). The idea is simple:

> The math stays rigorous. The code still runs. But the narrative, analogies, and exercises connect to something you already care about.

**How it works:**

1. Fork this repository
2. Pick your interest (F1, cooking, music, basketball, astronomy...)
3. Follow the mapping framework in `skill.md` to rewrite each notebook
4. Run `jupyter nbconvert --to notebook --execute <notebook>.ipynb` to verify everything still works

Every mathematical concept maps to your domain through a consistent pattern:

| Math Concept | Your Domain Question |
|-------------|---------------------|
| Vectors | "What's a list of numbers that describes something in my world?" |
| Dot product | "What two things do I compare for compatibility?" |
| Matrices | "What process transforms inputs into outputs?" |
| Eigenvectors | "What are the fundamental independent factors?" |
| SVD | "What hidden patterns explain what I see?" |

The linear algebra notebook (`01_linear_algebra.ipynb`) is the reference implementation, personalized through the lens of Formula 1 racing. See `skill.md` for the full guide and example mappings for F1, cooking, music, and basketball.

## Prerequisites

- Basic Python programming experience
- High school mathematics (algebra, basic calculus helpful but not required)
- Curiosity about how AI works

## Contributing

Found an error? Have a suggestion? Want to share your personalized version? Contributions are welcome — open an issue or submit a pull request on [GitHub](https://github.com/dan-shah/foundations-of-ai).

## License

This work is licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). You are free to share and adapt this material with attribution.
