---
name: personalize
description: Personalize a Foundations of AI notebook for a specific interest domain (F1, cooking, music, basketball, or any domain). Rewrites narrative, analogies, variable names, and exercises while preserving all math and ML connections.
argument-hint: "[notebook-number|all] [domain]"
allowed-tools: Read, Bash, Edit, NotebookEdit, Grep, Glob
---

# Personalize a Notebook

You are personalizing a notebook from the Foundations of AI curriculum. Your job is to rewrite narrative, analogies, variable names, and exercises so abstract math concepts connect to a specific interest domain — while keeping all math, ML connections, and code correctness intact.

## Step 1: Parse Arguments

Extract the notebook target and domain from `$ARGUMENTS`.

- If both are provided (e.g., `02 cooking` or `all cooking`), proceed.
- If only a number or `all` is provided, ask the user for their domain.
- If only a domain is provided, ask the user which notebook (or `all`) to personalize.
- If neither is provided, ask for both.

**Single notebook**: Map the notebook number to its filename (e.g., `02` → `02_calculus.ipynb`). Use Glob with pattern `{number}_*.ipynb` to find the exact file.

**All notebooks**: Use Glob with pattern `[0-9][0-9]_*.ipynb` to collect all 28 notebooks. Process them sequentially in numerical order (01, 02, ... 28). For each notebook, run Steps 2–7 before moving to the next. The domain mapping (Step 3) only needs to be built/confirmed once — reuse it across all notebooks.

## Step 2: Read and Enumerate the Notebook

Read the target notebook. Identify every cell and categorize each as:
- **Markdown cell** — narrative, explanations, tables
- **Code cell** — imports, visualizations, computations, exercises
- **Exercise cell** — code cells with `# EXERCISE:` or `# TODO:` markers

## Step 3: Load or Build the Domain Mapping

**Known domains** (F1, cooking, music, basketball): Read `references/domain-mappings.md` (located at `.claude/skills/personalize/references/domain-mappings.md`) and use the pre-built mapping table for the requested domain.

**New domain**: Read the Core Concept Mappings template from `references/domain-mappings.md`. For each row in the template, generate a domain-specific mapping by answering the "Mapping Question to Ask" column. Present the completed table to the user and ask them to confirm or adjust before proceeding.

## Step 4: Personalize Cell by Cell

Work through the notebook sequentially. For each cell, apply the rules below.

### Golden Rules — What to Change

1. **Markdown narrative** — Rewrite explanations and analogy blocks for the target domain
2. **Variable names in code** — Use domain terms (`car_velocity` not `v`, `recipe_vector` not `x`)
3. **Tables** — Add a domain-specific column (e.g., "Cooking Analogy") to concept tables; never remove the ML column
4. **Exercises** — Fully rewrite exercise scenarios to use the domain
5. **Plot titles and labels** — `"Car Speed Through a Corner"` not `"A 2D Vector"`
6. **Summary** — Pair every concept with its domain parallel

### Golden Rules — What NOT to Change

1. **The math** — Formulas, equations, and proofs stay exactly the same
2. **The ML connections** — Keep all "Why This Matters in ML" content intact
3. **Helper function logic** — `plot_vectors()`, `angle_between()`, etc. stay functional
4. **Numerical values that affect correctness** — Don't change values if it would break `np.allclose()` checks
5. **Learning objectives** — The learning goals are universal
6. **Notebook structure** — Keep the section order (Intuition → Visualization → Deep Dive → Code)

### The Key Principle

> **Add a domain layer on top. Never remove the ML layer underneath.**

Every concept must have three levels of understanding:
1. **Mathematical** — The formula and its proof (unchanged)
2. **Domain** — "This is like [your interest]" (your personalization)
3. **ML/AI** — "This is used in neural networks for..." (unchanged)

### Markdown Cells

- Add a `### The [Domain] Connection` section after each concept introduction
- Add a domain column to existing tables (don't remove the ML column)
- Rewrite "What this means" blocks with domain language
- Add a `**[Domain] analogy:**` callout before or after formulas
- Update the notebook title with a domain tag (e.g., "— The Cooking Edition")
- Rewrite the opening paragraph to connect the topic to the domain

### Code Cells

- Rename variables to domain terms where natural
- Update print statements and plot titles to reference the domain
- Keep the mathematical operations identical
- Ensure `np.allclose()` checks still pass
- Do NOT change import statements, helper function internals, or numerical constants

### Exercise Cells

- Fully rewrite the scenario using the domain (this is where personalization has the most impact)
- Keep the mathematical task identical
- Update test case variable names if needed, but keep expected numerical values the same

### Table Patterns

Use these three patterns from the style guide:

**Pattern A — Add a domain column:**
```markdown
| Component | Meaning | [Domain] Analogy | Range |
|-----------|---------|------------------|-------|
| ||a|| | Length of vector a | [domain example] | 0 to ∞ |
```

**Pattern B — Add a domain row to ML tables:**
```markdown
| Application | How it's used | [Domain] Parallel |
|-------------|---------------|-------------------|
| Neural networks | Weighted sums | [domain example] |
```

**Pattern C — Domain-specific deep dive callout:**
```markdown
**[Domain] analogy**: [1-2 sentence concrete analogy from the domain]
```

## Step 5: Verify

After all cells are personalized, run the notebook to verify correctness:

```bash
jupyter nbconvert --to notebook --execute <notebook>.ipynb
```

If any cell fails:
1. Read the error output
2. Identify if you changed something that should have stayed the same (a numerical value, a function signature, an import)
3. Fix the issue and re-run

Check that all `np.allclose()` calls still return `True`.

## Step 6: Spot-Check the Three-Layer Rule

Pick three major concepts from the notebook and verify each has:
1. The math formula (unchanged from original)
2. A domain analogy (your personalization)
3. The ML connection (unchanged from original)

If any layer is missing, add it.

## Step 7: Personalization Checklist

Before declaring the notebook done, verify all items:

- [ ] Title updated with domain tag (e.g., "— The Cooking Edition")
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

## Reference Files

For detailed standards, consult these files (relative to this skill's directory):

- `references/style-guide.md` — Notebook structure, explanation patterns, visualization standards, code standards, exercise guidelines
- `references/domain-mappings.md` — Core concept mapping template and four complete example domain mappings
