# Deep Learning Notebook Style Guide

> **Using Claude Code?** Run `/personalize [notebook-number] [domain]` to have Claude
> personalize a notebook automatically, following all the rules in this guide.

Reference guide for creating consistent, high-quality educational notebooks in this curriculum.

**This curriculum is designed to be personalized.** Anyone can adapt these notebooks to their interests — Formula 1, cooking, music, basketball, astronomy, whatever makes the math click for you. See the [Personalization Guide](#personalizing-the-curriculum) below.

---

## Core Philosophy

1. **Intuition before formulas** - Always explain *why* and *what it means* before showing the math
2. **Visual learning** - Every major concept gets a visualization
3. **Connect to ML** - Show how each concept applies to deep learning
4. **Interactive exploration** - Let learners experiment with parameters
5. **Build from simple to complex** - Start with 2D examples before generalizing
6. **Make it personal** - Connect abstract concepts to something the learner cares about

---

## Notebook Structure

```
# Part X.Y: Topic Name

Brief intro explaining why this matters for deep learning.

## Learning Objectives
- [ ] Checkboxes for self-assessment

---

## 1. First Concept

### Intuitive Explanation (markdown)
### Visualization (code)
### Deep Dive: Why This Matters (markdown + tables)
### Code Example (code)

## 2. Second Concept
... (repeat pattern)

---

## Exercises
### Exercise 1: ...

---

## Summary
### Key Concepts (bullet points)
### Connection to Deep Learning (table)
### Checklist (checkboxes)

---

## Next Steps
```

---

## Explanation Patterns

### Pattern 1: Formula Breakdown

When introducing a formula, break it into components:

```markdown
#### Breaking down the formula:

| Component | Meaning | Range |
|-----------|---------|-------|
| $\|a\|$ | Length of vector a | 0 to ∞ |
| $\cos(\theta)$ | Alignment factor | -1 to 1 |
```

### Pattern 2: Comparison Tables

Compare related concepts side-by-side:

```markdown
| Concept | Formula | Intuition | ML Use |
|---------|---------|-----------|--------|
| L1 Norm | $\sum|v_i|$ | Taxicab distance | Sparsity |
| L2 Norm | $\sqrt{\sum v_i^2}$ | Straight line | Regularization |
```

### Pattern 3: "What it means" Explanations

After any formula, add a plain-English interpretation:

```markdown
**What this means:** The dot product tells you "how much does vector b
point in the same direction as vector a?"
- Positive = similar direction
- Zero = perpendicular
- Negative = opposite directions
```

### Pattern 4: ML Connection Tables

Show practical applications:

```markdown
### Why This Matters in Machine Learning

| Application | How it's used |
|-------------|---------------|
| Neural networks | Weighted sums are dot products |
| Attention | Query-key similarity via dot product |
| Embeddings | Cosine similarity for semantic matching |
```

---

## Visualization Standards

### Setup Cell (first code cell)

```python
import numpy as np
import matplotlib.pyplot as plt

%matplotlib inline
plt.style.use('seaborn-v0_8-whitegrid')
np.random.seed(42)
```

### Figure Sizes

- Single plot: `figsize=(10, 6)` or `figsize=(8, 8)` for square
- Side-by-side (2): `figsize=(14, 5)`
- Grid (2x2): `figsize=(12, 10)`
- Grid (2x3): `figsize=(15, 10)`

### Plot Standards

```python
# Always include:
ax.set_xlabel('x')
ax.set_ylabel('y')
ax.set_title('Descriptive Title')
ax.legend()
ax.grid(True, alpha=0.3)

# For 2D vector plots:
ax.set_aspect('equal')
ax.axhline(y=0, color='k', linewidth=0.5)
ax.axvline(x=0, color='k', linewidth=0.5)
```

### Color Conventions

- Original/input: `'blue'`
- Transformed/output: `'red'`
- Highlighted/special: `'green'`
- Secondary: `'orange'`, `'purple'`
- Use `alpha=0.3` to `0.7` for overlapping elements

### Interactive Visualizations

Show how changing parameters affects output:

```python
# Vary a parameter and show effect
for param in [0.1, 0.5, 1.0, 2.0]:
    result = compute(param)
    plt.plot(x, result, label=f'param={param}')
plt.legend()
```

---

## Code Standards

### Function Documentation

```python
def function_name(param1, param2):
    """
    Brief description of what this does.

    Args:
        param1: Description
        param2: Description

    Returns:
        Description of return value
    """
```

### Print Output Format

```python
print(f"Result: {value:.4f}")  # 4 decimal places for floats
print(f"Vector: {vector}")      # Arrays print directly
print(f"Check passed: {np.allclose(a, b)}")  # Boolean checks
```

### Exercise Structure

```python
# EXERCISE: Brief description
def exercise_function(params):
    """
    Docstring explaining the task.
    """
    # TODO: Implement this!
    # Hint: Helpful hint

    pass  # or partial implementation

# Test
result = exercise_function(test_input)
expected = known_answer
print(f"Your result: {result}")
print(f"Expected: {expected}")
print(f"Correct: {np.allclose(result, expected)}")
```

---

## Deep Dive Sections

When a concept needs extra explanation, add a "Deep Dive" section:

```markdown
### Deep Dive: Understanding [Concept]

[2-3 paragraphs of intuitive explanation]

#### Key Insight

[The one thing they should remember]

#### Common Misconceptions

| Misconception | Reality |
|---------------|---------|
| ... | ... |
```

---

## Exercises Guidelines

1. **Start simple** - First exercise should be straightforward
2. **Build complexity** - Later exercises combine concepts
3. **Provide scaffolding** - Give hints and partial implementations
4. **Include tests** - Let learners verify their solutions
5. **Connect to ML** - Final exercise should be ML-relevant

---

## Required Packages by Topic

### Part 1: Math Foundations
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats  # for probability
```

### Part 2: Python Foundations
```python
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
```

### Part 3+: Neural Networks
```python
import numpy as np
import matplotlib.pyplot as plt
import torch
import torch.nn as nn
```

---

## Checklist for New Notebooks

Before finalizing a notebook, verify:

- [ ] Learning objectives at the top
- [ ] Intuitive explanation before every formula
- [ ] At least one visualization per major concept
- [ ] Tables connecting concepts to ML applications
- [ ] Interactive examples where parameters can be varied
- [ ] Exercises with test cases
- [ ] Summary with checklist at the end
- [ ] "Next Steps" pointing to the next topic
- [ ] All code cells run without errors
- [ ] Consistent formatting and style

---
---

# Personalizing the Curriculum

## Overview

Every notebook in this curriculum can be personalized to **your** interest. The math stays rigorous. The code still runs. But the narrative, analogies, variable names, and exercises get rewritten so that abstract concepts connect to something you already care about.

**The premise**: "What is a vector?" is abstract. "What is a car's telemetry snapshot?" is concrete. Learning happens faster when new ideas attach to existing knowledge.

---

## The Golden Rules

### What to change
1. **Markdown narrative** — Rewrite explanations and "F1 analogy" blocks for your domain
2. **Variable names in code** — `velocity` instead of `v`, `driver_rating` instead of `rating`
3. **Tables** — Add a domain-specific column (e.g., "Cooking Analogy") to concept tables
4. **Exercises** — Fully rewrite exercise scenarios to use your domain
5. **Plot titles and labels** — `"Car Speed Through a Corner"` instead of `"A 2D Vector"`
6. **Summary** — Pair every concept with its domain parallel

### What NOT to change
1. **The math** — Formulas, equations, and proofs stay exactly the same
2. **The ML connections** — Keep all "Why This Matters in ML" content intact
3. **Helper function logic** — `plot_vectors()`, `angle_between()`, etc. stay functional
4. **Numerical values that affect correctness** — Don't change values if it would break `np.allclose()` checks
5. **Learning objectives** — The learning goals are universal
6. **Notebook structure** — Keep the section order (Intuition → Visualization → Deep Dive → Code)

### The key principle

> **Add a domain layer on top. Never remove the ML layer underneath.**

Every concept should have three levels of understanding:
1. **Mathematical** — The formula and its proof (unchanged)
2. **Domain** — "This is like [your interest]" (your personalization)
3. **ML/AI** — "This is used in neural networks for..." (unchanged)

---

## The Mapping Framework

Every mathematical concept maps to a domain through a consistent pattern. Here's the universal template:

### Core Concept Mappings

| Math Concept | What to Map | Mapping Question to Ask |
|-------------|-------------|------------------------|
| **Vectors** | Measurements / state | "What's a list of numbers that describes something in my domain?" |
| **Vector addition** | Combining forces / effects | "What things combine additively in my domain?" |
| **Scalar multiplication** | Scaling / amplifying | "What scales up or down in my domain?" |
| **Dot product** | Alignment / similarity | "What two things do I compare for compatibility?" |
| **Projection** | Useful component | "When is only part of something useful?" |
| **Norms** | Magnitude / intensity | "What's the 'total size' of something?" |
| **Matrices** | Transformations / processes | "What process takes inputs and produces different outputs?" |
| **Matrix multiplication** | Sequential processes | "What processes happen in sequence?" |
| **Inverse** | Undoing a process | "What reverses something in my domain?" |
| **Singular matrix** | Information loss | "When is something irreversible?" |
| **Eigenvalues/vectors** | Natural axes / modes | "What are the fundamental independent factors?" |
| **SVD** | Hidden factor decomposition | "What hidden factors explain the patterns I see?" |
| **PCA** | Main sources of variation | "What's the #1 thing that differs between instances?" |

---

## Example Mappings by Interest

### Formula 1 Racing

| Math Concept | F1 Mapping |
|-------------|-----------|
| Vector | Car telemetry: `[speed, downforce, tire_temp, throttle]` |
| Vector addition | Forces on the car: engine + aero + cornering = net force |
| Scalar multiply | DRS boost (2x), braking (0.5x), spin (-1x) |
| Dot product | Setup alignment: "How well does this setup match the track?" |
| Projection | Corner exit speed projected onto the straight |
| Norms | Actual car speed (L2), total g-force sum (L1), peak g (L∞) |
| Matrix | Setup change: transforms base performance into new profile |
| Composition | Multiple setup changes applied in sequence |
| Inverse | Reverting a setup change to baseline |
| Eigenvectors | Natural performance axes (straight-line speed vs cornering) |
| SVD | Driver-circuit recommender: predict performance at new tracks |

### Cooking & Recipes

| Math Concept | Cooking Mapping |
|-------------|----------------|
| Vector | Recipe: `[flour_g, sugar_g, butter_g, eggs, temp_C]` |
| Vector addition | Combining two recipes (mixing cookie dough + frosting) |
| Scalar multiply | Doubling a recipe (2x), halving (0.5x) |
| Dot product | Flavor compatibility: "How well do these ingredients go together?" |
| Projection | "How much of this spice blend is actually adding sweetness?" |
| Norms | Total calories (L1), richness score (L2), strongest flavor (L∞) |
| Matrix | Cooking process: raw ingredients → cooked dish transformation |
| Composition | Multi-step recipe: marinate → sear → braise |
| Inverse | "Unseasoning" — what would neutralize this flavor? |
| Eigenvectors | Fundamental flavor axes: sweet-savory, rich-light, spicy-mild |
| SVD | Taste profile decomposition: predict if someone likes a new dish |

### Music & Audio

| Math Concept | Music Mapping |
|-------------|-------------|
| Vector | Audio frame: `[bass, mid, treble, tempo, loudness]` |
| Vector addition | Mixing two tracks together (layering) |
| Scalar multiply | Volume knob: amplify (2x), mute (0x), invert phase (-1x) |
| Dot product | Musical similarity: "How alike are these two songs?" |
| Projection | "How much bass is in this mix?" |
| Norms | Overall loudness (L2), total frequency energy (L1), peak frequency (L∞) |
| Matrix | Equalizer: transforms flat audio into shaped output |
| Composition | Signal chain: EQ → compression → reverb |
| Inverse | Noise cancellation: undo the noise transformation |
| Eigenvectors | Natural resonant frequencies of an instrument |
| SVD | Listener-song recommender: predict if someone likes a new track |

### Basketball

| Math Concept | Basketball Mapping |
|-------------|-------------------|
| Vector | Player stats: `[points, assists, rebounds, steals, blocks]` |
| Vector addition | Team stats = sum of all player contributions |
| Scalar multiply | Minutes scaling: starter (1x) vs bench player (0.5x) |
| Dot product | Player-team fit: "How well does this player match what the team needs?" |
| Projection | "How much of this player's value is scoring vs playmaking?" |
| Norms | Overall impact (L2), box score total (L1), best single stat (L∞) |
| Matrix | Coaching system: transforms raw talent into team performance |
| Composition | Play sequence: screen → pass → cut → finish |
| Inverse | Defensive counter: undo the opponent's offensive play |
| Eigenvectors | Fundamental player archetypes (scorer, playmaker, defender) |
| SVD | Player-team matchup predictor from sparse scouting data |

---

## Step-by-Step Personalization Process

### Step 0: Choose your domain
Pick something you genuinely care about. The best domains have:
- **Measurable quantities** (for vectors and norms)
- **Things that combine** (for addition)
- **Comparisons** (for dot products)
- **Processes** (for matrices)
- **Rankings or ratings** (for SVD exercises)

### Step 1: Fill out the mapping table
Copy the "Core Concept Mappings" template above and fill in your domain's answers. This is your cheat sheet for the entire rewrite.

### Step 2: Rewrite one notebook at a time
Work through each notebook sequentially. For each cell:

**Markdown cells:**
- Add a `### The [Domain] Connection` section after each concept intro
- Add a domain column to existing tables (don't remove ML column)
- Rewrite "What this means" blocks with domain language
- Add a `**[Domain] analogy:**` callout before or after formulas

**Code cells:**
- Rename variables to domain terms (`car_velocity` not `v`)
- Update print statements and plot titles
- Keep the mathematical operations identical
- Make sure `np.allclose()` checks still pass

**Exercise cells:**
- Full rewrite of the scenario (this is where personalization shines most)
- Keep the mathematical task identical
- Update test cases if variable names changed

### Step 3: Run the notebook
```bash
jupyter nbconvert --to notebook --execute <notebook>.ipynb
```
Every cell must execute without errors. The personalization is narrative only — if the code breaks, you changed something you shouldn't have.

### Step 4: Verify the three-layer rule
Spot-check: does every major concept still have all three layers?
1. The math formula (unchanged)
2. A domain analogy (your addition)
3. The ML connection (unchanged)

---

## Table Patterns for Personalization

### Pattern A: Add a Domain Column

Original:
```markdown
| Component | Meaning | Range |
|-----------|---------|-------|
| ||a|| | Length of vector a | 0 to ∞ |
```

Personalized (F1):
```markdown
| Component | Meaning | F1 Analogy | Range |
|-----------|---------|------------|-------|
| ||a|| | Length of vector a | Car's actual speed | 0 to ∞ |
```

### Pattern B: Add a Domain Row to ML Tables

Original:
```markdown
| Application | How it's used |
|-------------|---------------|
| Neural networks | Weighted sums |
| Attention | Query-key similarity |
```

Personalized (F1):
```markdown
| Application | How it's used | F1 Parallel |
|-------------|---------------|-------------|
| Neural networks | Weighted sums | Telemetry pattern matching |
| Attention | Query-key similarity | "Which past laps predict this one?" |
```

### Pattern C: Domain-Specific Deep Dives

Add a callout block after the standard explanation:

```markdown
**F1 analogy**: Think of the dot product as measuring setup-track alignment.
A car tuned for Monza (low downforce) has a high dot product with Monza's
demands and a negative dot product with Monaco's demands.
```

---

## Personalization Checklist

Before considering a notebook "personalized," verify:

- [ ] Title updated with domain tag (e.g., "— The Formula 1 Edition")
- [ ] Opening paragraph connects the topic to the domain
- [ ] Every major concept has a domain analogy
- [ ] Tables have a domain column (without losing the ML column)
- [ ] Variable names in code use domain terms where natural
- [ ] Plot titles and axis labels reference the domain
- [ ] All exercises rewritten with domain scenarios
- [ ] Summary pairs every concept with its domain parallel
- [ ] All code cells still execute without errors
- [ ] All `np.allclose()` checks still pass
- [ ] The math is untouched — formulas, proofs, and equations are identical
- [ ] ML connections are preserved alongside (not replaced by) domain analogies
