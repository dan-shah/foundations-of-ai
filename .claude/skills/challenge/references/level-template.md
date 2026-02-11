# Level Template

Every level follows this exact structure. All 5 components are required.

---

## Standard Level Format

```markdown
---

## Level [World].[Number]: [Evocative Name]

**Type:** [Compute | Predict | Debug | Construct | Optimize | Connect | Estimate]
**Points:** [10 | 15 | 20 | 30 | 50]
**Difficulty:** [Easy | Medium | Hard | Boss | Final Boss]

### 🎯 Mission

[A concrete, specific task with a clear success condition.]

### 📋 Intel

[Minimal context — just enough to make the mission possible. The key formula or rule, one worked example if new, a reminder of relevant previous concepts.]

### 💡 Hints

<details>
<summary>Hint 1 (Conceptual Nudge)</summary>

[A nudge in the right direction. Doesn't give away the method.]

</details>

<details>
<summary>Hint 2 (Methodological Clue)</summary>

[A more specific clue about which method/formula to use.]

</details>

<details>
<summary>Hint 3 (Detailed Walkthrough)</summary>

[A nearly-complete worked approach. Everything except the final computation.]

</details>

### ✅ Solution

<details>
<summary>Click to reveal solution</summary>

**The Answer:**
[Code cell or mathematical result]

**The Concept:**
[Formal explanation — this is where the teaching happens.]

**Common Mistakes:**
- [Mistake 1]: [Why it happens and how to avoid it]

**ML Connection:**
[How this concept appears in machine learning]

</details>

### ⭐ Bonus Challenge

[An optional harder variant that extends the concept.]
```

---

## Boss Level Format

```markdown
## 🏆 Boss Level: [Dramatic Name]

**Type:** Connect or Construct
**Points:** 30
**Difficulty:** Boss

### 🎯 Mission

[Multi-part challenge combining all concepts from this World.]

Part 1: [Sub-task using Concept A]
Part 2: [Sub-task using Concept B]
Part 3: [Sub-task combining A + B + C]

### 📋 Intel

[Recap of all concepts from this World.]

### 💡 Hints

[Same 3-tier structure, but hints reference specific levels.]

### ✅ Solution

[Full multi-part solution with synthesis explanation.]

### ⭐ Bonus Challenge

[Bridge to the next World's topics.]
```

---

## Final Boss Format

```markdown
## 👑 Final Boss: [Epic Name]

**Type:** Construct
**Points:** 50
**Difficulty:** Final Boss

### 🎯 Mission

[A substantial project-style challenge requiring concepts from every World.]

### 📋 Intel

[Comprehensive cheat sheet — formulas and key ideas, no explanations.]

### 💡 Hints

[Same 3-tier structure, referencing specific Worlds and Levels.]

### ✅ Solution

[Complete solution with reflection mapping each part back to concepts learned.]
```

---

## Formatting Rules

### `<details>` Tags
- Always include a blank line after `<summary>` closing tag
- Always include a blank line before `</details>` closing tag
- Content inside should be full markdown

### Code Cells
- Solution code goes in a code cell immediately after the solution markdown
- Code must be runnable and produce output
- Include comments mapping steps to concepts

### Scoring
| Difficulty | Base Points | Hint Penalty |
|-----------|-------------|-------------|
| Easy | 10 | -2 per hint |
| Medium | 15 | -3 per hint |
| Hard | 20 | -4 per hint |
| Boss | 30 | -5 per hint |
| Final Boss | 50 | -8 per hint |
| Bonus | +5 | — |

### Score Summary
```markdown
## 🏅 Score Summary

| Achievement | Points Required | Badge |
|------------|----------------|-------|
| Completed | > 0 | 🌱 Beginner |
| Solid | > 50% | 🌿 Intermediate |
| Strong | > 75% | 🌳 Advanced |
| Perfect | 100% | 🏆 Master |
| No hints | 100% + no hints | ⭐ Legend |
```
