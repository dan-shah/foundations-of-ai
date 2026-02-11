# Challenge Types

Seven challenge types to rotate through for variety and engagement.

---

## 1. Compute

**Description:** "Find the value of..." — Direct calculation or procedure application.

**Best For:** Procedural skills — taking derivatives, evaluating functions, computing gradients.

**Example:**
> Find the derivative of f(x) = 3x⁴ - 2x² + 7x - 1. Evaluate it at x = 2.

**Difficulty Scaling:**
- Easy: Single rule application (power rule on a monomial)
- Medium: Multiple rules combined (polynomial with various terms)
- Hard: Nested functions requiring chain rule + product rule

---

## 2. Predict

**Description:** "What will happen when..." — Build intuition by guessing before computing.

**Best For:** Developing intuition — predicting graph shapes, sign of derivatives, convergence behavior.

**Example:**
> Without calculating, sketch what f'(x) looks like if f(x) has a peak at x = 2 and a valley at x = 5.

**Difficulty Scaling:**
- Easy: Binary prediction (will this increase or decrease?)
- Medium: Qualitative sketch (draw the approximate shape)
- Hard: Quantitative estimate (roughly what value?)

---

## 3. Debug

**Description:** "This solution has an error. Find and fix it."

**Best For:** Common misconceptions — forgetting the chain rule, sign errors, off-by-one mistakes.

**Example:**
> A student computed d/dx[sin(3x)] = cos(3x). What's wrong? Fix it.

**Difficulty Scaling:**
- Easy: One obvious error (forgot to apply a rule)
- Medium: Subtle error (correct approach, arithmetic mistake)
- Hard: Multiple errors or conceptual misunderstanding

---

## 4. Construct

**Description:** "Build a function/expression that satisfies these conditions..." — Reverse-engineering.

**Best For:** Deep understanding — designing functions with specific properties.

**Example:**
> Construct a function f(x) where f'(x) > 0 for all x, but f'(x) is decreasing.

**Difficulty Scaling:**
- Easy: One constraint (find a function with this derivative)
- Medium: Two constraints (increasing AND concave down)
- Hard: Multiple constraints that seem contradictory

---

## 5. Optimize

**Description:** "Find the best/fastest/cheapest..." — Applied optimization.

**Best For:** Applied concepts — finding minima/maxima, gradient descent applications.

**Example:**
> A box with no lid has surface area 100 cm². What dimensions maximize volume?

**Difficulty Scaling:**
- Easy: 1D optimization (single variable)
- Medium: 2D optimization (two variables)
- Hard: Constrained optimization or non-convex landscape

---

## 6. Connect

**Description:** "These two things look different but are the same idea. Explain why."

**Best For:** Transfer learning — seeing the same concept in different forms.

**Example:**
> The derivative f'(a) gives the slope at x = a. The gradient ∇f gives the steepest ascent direction. How are these the same idea?

**Difficulty Scaling:**
- Easy: Two representations of the same concept
- Medium: Same concept in different domains
- Hard: Concepts that seem different but share deep structure

---

## 7. Estimate

**Description:** "Without calculating, roughly what is..." — Number sense and reasonableness.

**Best For:** Building intuition, sanity checking, approximation skills.

**Example:**
> f(x) = x³ passes through (2, 8) and (3, 27). Without computing, roughly what is f'(2.5)?

**Difficulty Scaling:**
- Easy: Order-of-magnitude estimate
- Medium: Ballpark figure with reasoning
- Hard: Tight bound with justification

---

## Rotation Guidelines

- Never use the same type more than twice in a row
- Boss levels should always be Connect or Construct (synthesis)
- Early levels lean toward Compute and Predict
- Later levels lean toward Debug, Construct, and Connect
- Estimate is great as a warm-up before harder challenges
- Debug works well right after introducing a concept
