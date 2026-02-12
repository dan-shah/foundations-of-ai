# Foundations of AI

A comprehensive, hands-on AI curriculum — 32 interactive Jupyter notebooks from linear algebra to production AI systems.

**[Read online](https://dan-shah.github.io/foundations-of-ai)** — no setup required.

**Built to be transformed.** Five Claude Code skills let you personalize, simplify, gamify, narrate, or visualize any notebook — making every concept click for any learner.

## Quick Start

```bash
git clone https://github.com/dan-shah/foundations-of-ai.git
cd foundations-of-ai
pip install -r requirements.txt
jupyter notebook notebooks/
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

## Content Transformation Skills

This curriculum ships with five [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skills that transform any notebook into different learning formats. Each skill is a slash command — no setup required after cloning.

### `/personalize` — Domain Adaptation

Rewrites narrative, analogies, variable names, and exercises so abstract concepts connect to something you already care about. All math and code stays identical.

```bash
/personalize 02 cooking        # Single notebook
/personalize all F1             # Entire curriculum
```

Works with any domain — F1, cooking, music, basketball, astronomy, or anything else. Four domains have pre-built mappings; for others, Claude generates a mapping and confirms it with you before starting.

**Produces:** A personalized `.ipynb` notebook.

### `/difficulty` — Audience-Level Adjustment

Adapts vocabulary, notation, examples, and pacing for a specific audience while preserving all core learning objectives and mathematical accuracy.

```bash
/difficulty 02 middle-schooler
/difficulty 17 eli5
```

Supported audiences: eli5, middle-schooler, high-schooler, college-freshman, grad-student, non-technical-adult.

**Produces:** A difficulty-adapted `.ipynb` notebook.

### `/challenge` — Gamified Learning

Transforms a notebook into progressively harder missions. Concepts are taught through struggle — minimal upfront explanation, hints available when stuck, solutions revealed after attempting. Features interactive hint tracking, a live score bar, and a polished game-like UI.

```bash
/challenge 02
```

**Produces:** A standalone `.html` file with worlds, levels, boss fights, and a live score tracker.

### `/story` — Narrative Learning

Transforms a notebook into a multi-chapter story where characters discover and apply concepts within a plot arc. Learners absorb material as a natural consequence of following the narrative.

```bash
/story 02              # Defaults to sci-fi
/story 02 heist        # Choose a genre
```

Supported genres: sci-fi, mystery, fantasy, heist.

**Produces:** A standalone `.html` file with the narrative.

### `/visualize` — Interactive Explorations

Transforms a notebook into a standalone interactive HTML page with D3.js visualizations. Each abstract concept gets a corresponding visual that learners can drag, slide, and toggle to build intuition through exploration.

```bash
/visualize 02
```

**Produces:** A self-contained `.html` file — no Python, Jupyter, or server required.

## Examples

The `examples/` directory showcases each skill's output:

| Skill | Example | Description |
|-------|---------|-------------|
| `/personalize` | [linear_algebra_tennis.ipynb](examples/personalize/linear_algebra_tennis.ipynb) | Linear algebra through tennis serve mechanics |
| `/personalize` | [calculus_cooking.ipynb](examples/personalize/calculus_cooking.ipynb) | Calculus through cooking techniques |
| `/difficulty` | [calculus_middle_schooler.ipynb](examples/difficulty/calculus_middle_schooler.ipynb) | Calculus adapted for middle school students |
| `/challenge` | [calculus_game.html](examples/challenge/calculus_game.html) | Calculus as a gamified challenge sequence |
| `/story` | [calculus_meridian_protocol.html](examples/story/calculus_meridian_protocol.html) | Calculus embedded in a sci-fi narrative |
| `/visualize` | [calculus_interactive.html](examples/visualize/calculus_interactive.html) | Calculus with interactive D3.js visualizations |

## Without Claude Code

You can personalize manually using `skill.md` as your guide. It contains the same mapping framework, golden rules, and checklist that the `/personalize` skill uses:

1. **Fork** this repository
2. **Pick your interest** — F1, cooking, music, basketball, astronomy, whatever
3. **Follow `skill.md`** — mapping framework, step-by-step process, and example mappings
4. **Rewrite the notebooks** — one at a time, following the golden rules
5. **Verify** — run each notebook to confirm all code still executes

## Project Structure

```
├── notebooks/                         # 32 core curriculum notebooks (01–32)
├── examples/                          # Skill demonstration outputs
│   ├── personalize/                   #   Domain-adapted notebooks
│   ├── difficulty/                    #   Audience-level adaptations
│   ├── challenge/                     #   Gamified challenge HTML files
│   ├── story/                         #   Narrative HTML files
│   └── visualize/                     #   Interactive D3.js HTML files
├── .claude/skills/                    # 5 Claude Code skill definitions
├── intro.md                           # Jupyter Book landing page
├── curriculum.md                      # Detailed curriculum outline
├── skill.md                           # Style guide + personalization framework
├── _config.yml                        # Jupyter Book configuration
├── _toc.yml                           # Table of contents
└── requirements.txt                   # Python dependencies
```

## Prerequisites

- Basic Python programming
- High school math (algebra, basic calculus helpful but not required)
- Curiosity about how AI works

## Contributing

Found an error? Want to share your personalized version? Contributions are welcome — open an issue or submit a PR.

## License

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — free to share and adapt with attribution.
