---
name: difficulty
description: Adapt a Foundations of AI notebook for a specific audience level. Rewrites vocabulary, notation, examples, and pacing while preserving all core learning objectives and mathematical accuracy.
argument-hint: "[notebook-number] [audience]"
allowed-tools: Read, Bash, Edit, NotebookEdit, Grep, Glob
---

# Adapt Notebook Difficulty

You are adapting a notebook from the Foundations of AI curriculum for a specific audience. Your job is to rewrite vocabulary, notation, examples, explanation depth, and pacing so the content is accessible to the target audience — while keeping all core learning objectives and mathematical accuracy intact.

## Step 1: Parse Arguments

Extract the notebook target and audience from `$ARGUMENTS`.

- If both are provided (e.g., `02 middle-schooler` or `02 grad-student`), proceed.
- If only a number is provided, ask the user which audience level they want.
- If only an audience is provided, ask which notebook to adapt.
- If neither is provided, ask for both.

**Supported audiences:** eli5, middle-schooler, high-schooler, college-freshman, grad-student, non-technical-adult

Map the notebook number to its filename (e.g., `02` → `02_calculus.ipynb`). Use Glob with pattern `{number}_*.ipynb` to find the exact file.

## Step 2: Read and Understand the Source

Read the target notebook. Identify every cell and categorize each as:
- **Markdown cell** — narrative, explanations, tables, formulas
- **Code cell** — imports, visualizations, computations
- **Exercise cell** — code cells with `# EXERCISE:` or `# TODO:` markers

List all major concepts covered in the notebook.

## Step 3: Load the Audience Profile

Read `references/audience-profiles.md` (located at `.claude/skills/difficulty/references/audience-profiles.md`) and load the profile for the target audience. This gives you concrete parameters for:
- Vocabulary level
- Math notation level
- Assumed knowledge
- Explanation depth
- Example style
- Tone

## Step 4: Content Audit

Scan each section of the source and tag it with one of:
- **Keep** — Core concepts essential to learning objectives; present at appropriate level
- **Simplify** — Concepts that need to be explained at a lower level for this audience
- **Expand** — Concepts that need more depth/rigor for a higher-level audience
- **Add** — Background/prerequisites the target audience needs but the source doesn't cover
- **Remove** — Content above/below the target audience's level that isn't essential

## Step 5: Rewrite Cell by Cell

Read `references/rewriting-rules.md` (located at `.claude/skills/difficulty/references/rewriting-rules.md`) for detailed transformation rules.

Work through the notebook sequentially. For each cell, apply the appropriate rewriting direction:

### Simplifying (lower-level audiences)
- Replace technical terms with plain-language equivalents on first use
- Replace abstract notation with verbal descriptions
- Add scaffolding: "Before we understand X, let's make sure we're comfortable with Y"
- Multiply examples 2-3x, make them progressively harder
- Add "check your understanding" moments after each concept
- Use shorter paragraphs and sentences
- Add visual/spatial descriptions

### Deepening (higher-level audiences)
- Remove repetitive examples, keep only the most illustrative
- Add formal definitions, theorems, proof sketches
- Add "connections" callouts to related fields
- Introduce edge cases and counterexamples
- Replace worked-out steps with "verify that..." exercises
- Increase information density

### Golden Rules — What NOT to Change
1. **Core learning objectives** — Every concept the original teaches must still be taught
2. **Mathematical accuracy** — Simplified ≠ wrong. If you simplify notation, the underlying math must still be correct
3. **Code correctness** — All code cells must still execute and produce correct results
4. **Section order** — Keep the pedagogical sequence intact
5. **ML connections** — Preserve why each concept matters for AI/ML

## Step 6: Consistency Pass

After rewriting all cells, sweep through for:
- Are all prereqs the audience wouldn't know explained or removed?
- Is vocabulary level consistent throughout (no sudden jumps)?
- Do examples match the audience's world?
- Is the pacing appropriate?
- Are code variable names and comments at the right level?

## Step 7: Verify

Run the notebook to verify correctness:

```bash
jupyter nbconvert --to notebook --execute <notebook>.ipynb
```

If any cell fails:
1. Read the error output
2. Identify if you changed something that affected functionality
3. Fix the issue and re-run

## Step 8: Add Transformation Notes

Add an appendix cell at the end of the notebook with:
- Target audience
- Difficulty rating (1-10) based on vocabulary complexity, notation density, and assumed prerequisites
- Summary of what was added, simplified, removed, and why
- List of concepts that were deferred to later study (if any)

## Step 9: Adaptation Checklist

Before declaring the notebook done, verify all items:

- [ ] Target audience identified and profile loaded
- [ ] All core learning objectives preserved
- [ ] Vocabulary matches target audience throughout
- [ ] Math notation appropriate for audience level
- [ ] Examples use contexts familiar to the audience
- [ ] Explanation depth matches audience needs
- [ ] Scaffolding added where audience needs prerequisites
- [ ] Advanced content removed or flagged for later when appropriate
- [ ] Tone is consistent and appropriate (never condescending)
- [ ] All code cells still execute without errors
- [ ] ML/AI connections preserved
- [ ] Transformation notes appendix included

## Reference Files

For detailed standards, consult these files (relative to this skill's directory):

- `references/audience-profiles.md` — Detailed profiles for each audience level with vocabulary, notation, assumed knowledge, depth, examples, and tone parameters
- `references/rewriting-rules.md` — Specific rewriting rules for simplifying vs. deepening, with examples for each transformation direction
