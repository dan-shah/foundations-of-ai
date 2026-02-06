# Deep Learning Notebook Style Guide

Reference guide for creating consistent, high-quality educational notebooks in this curriculum.

---

## Core Philosophy

1. **Intuition before formulas** - Always explain *why* and *what it means* before showing the math
2. **Visual learning** - Every major concept gets a visualization
3. **Connect to ML** - Show how each concept applies to deep learning
4. **Interactive exploration** - Let learners experiment with parameters
5. **Build from simple to complex** - Start with 2D examples before generalizing

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
