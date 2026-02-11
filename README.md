# Foundations of AI

A comprehensive, hands-on AI curriculum — 32 interactive Jupyter notebooks from linear algebra to production AI systems.

**Built to be personalized.** Fork it, pick your passion, and make every concept click.

## Quick Start

```bash
git clone https://github.com/dan-shah/foundations-of-ai.git
cd foundations-of-ai
pip install -r requirements.txt
jupyter notebook
```

## What's Inside

32 notebooks covering a complete path from math foundations to production AI:

| Part | Topics | Notebooks |
|------|--------|-----------|
| **1. Math Foundations** | Linear algebra, calculus, probability & statistics | 01–03 |
| **2. Programming Foundations** | OOP for ML, NumPy deep dive | 04–05 |
| **3. Classical ML & Optimization** | Classical ML, linear programming, optimization theory | 06–08 |
| **4. Neural Networks** | Perceptrons, backpropagation, PyTorch, training | 09–12 |
| **5. Architectures** | CNNs, computer vision, RNNs, attention mechanisms | 13–16 |
| **6. Transformers & LLMs** | Transformer architecture, embeddings, tokenization, language models, fine-tuning | 17–21 |
| **7. Reinforcement Learning** | RL fundamentals, Q-learning, policy gradients, PPO | 22–25 |
| **8. Applied AI** | RAG, AI agents, evaluations, production monitoring | 26–29 |
| **9. Advanced Topics** | Inference optimization, ML systems, multimodal AI | 30–32 |

Every concept is taught with intuitive explanations before formulas, visualizations, from-scratch implementations, and practical exercises.

## Personalize It

This is the key idea: **anyone can adapt this curriculum to their interests**.

The math stays rigorous. The code still runs. But the narrative, analogies, variable names, and exercises get rewritten so abstract concepts connect to something you already care about.

### With Claude Code (Recommended)

If you have [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed, the `/personalize` skill is included in this repo and available immediately after cloning. No setup required.

**Personalize a single notebook:**
```bash
/personalize 02 cooking
```

**Personalize the entire curriculum:**
```bash
/personalize all cooking
```

This rewrites narrative, analogies, variable names, and exercises while preserving all math and ML connections. It works with any domain — F1, cooking, music, basketball, astronomy, or anything else. Four domains have pre-built mappings; for others, Claude will generate a mapping and confirm it with you before starting.

### Without Claude Code

You can personalize manually using `skill.md` as your guide. It contains the same mapping framework, golden rules, and checklist that the skill uses:

1. **Fork** this repository
2. **Pick your interest** — F1, cooking, music, basketball, astronomy, whatever
3. **Follow `skill.md`** — mapping framework, step-by-step process, and example mappings for four domains
4. **Rewrite the notebooks** — one at a time, following the golden rules
5. **Verify** — run each notebook to confirm all code still executes

### Example: Linear Algebra + Formula 1

The linear algebra notebook (`01_linear_algebra.ipynb`) is the reference implementation, personalized for Formula 1:

| Math Concept | F1 Analogy |
|-------------|-----------|
| Vectors | Car telemetry: `[speed, downforce, tire_temp]` |
| Dot product | Setup-track alignment: "How well does this setup match Monza?" |
| Norms | Actual car speed (L2), total g-force (L1), peak g (L-inf) |
| Matrices | Setup changes that transform performance |
| Eigenvectors | Natural performance axes of the car |
| SVD | Driver-circuit predictor from sparse results |

## Prerequisites

- Basic Python programming
- High school math (algebra, basic calculus helpful but not required)
- Curiosity about how AI works

## Project Structure

```
├── 01_linear_algebra.ipynb        # Notebooks 01-32 (the curriculum)
├── ...
├── 32_multimodal_ai.ipynb
├── .claude/skills/personalize/    # /personalize skill for Claude Code
│   ├── SKILL.md                   #   Skill definition and instructions
│   └── references/
│       ├── style-guide.md         #   Notebook style standards
│       └── domain-mappings.md     #   Concept mapping templates
├── intro.md                       # Jupyter Book landing page
├── curriculum.md                  # Detailed curriculum outline
├── skill.md                       # Style guide + personalization framework
├── _config.yml                    # Jupyter Book configuration
├── _toc.yml                       # Table of contents
└── requirements.txt               # Python dependencies
```

## Contributing

Found an error? Want to share your personalized version? Contributions are welcome — open an issue or submit a PR.

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — free to share and adapt with attribution.
