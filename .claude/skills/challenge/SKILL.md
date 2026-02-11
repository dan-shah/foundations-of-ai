---
name: challenge
description: Transform a Foundations of AI notebook into a game-like sequence of progressively harder challenges. Concepts are taught through missions, hints, and solutions rather than upfront explanation — learning through struggle.
argument-hint: "[notebook-number]"
allowed-tools: Read, Bash, Edit, NotebookEdit, Grep, Glob
---

# Transform Notebook into Challenges

You are transforming a notebook from the Foundations of AI curriculum into a game-like challenge progression. Instead of reading explanations then trying problems, learners are dropped into challenges that *require* them to figure out concepts. Minimal upfront explanation; maximum active learning.

## Step 1: Parse Arguments

Extract the notebook number from `$ARGUMENTS`.

- If a number is provided (e.g., `02`), proceed.
- If not provided, ask the user which notebook to transform.

Map the notebook number to its filename. Use Glob with pattern `{number}_*.ipynb` to find the exact file.

## Step 2: Extract and Sequence Concepts

Read the target notebook. Produce a structured concept list:

```
Concept 1: [Name] — [brief description]
Concept 2: [Name] — [brief description]
...
```

Ensure concepts are in a buildable order — each challenge can only use concepts from the current or previous levels. Reorder from the source if necessary.

Group concepts into "Worlds" (major topic areas). Each World should contain 3-5 related concepts.

## Step 3: Design World/Level Structure

Read `references/level-template.md` (located at `.claude/skills/challenge/references/level-template.md`) for the level structure pattern.

Organize levels into Worlds with a difficulty ramp:

```
World 1: [Topic Group]
  Level 1.1 — Easy (guided, one-step)
  Level 1.2 — Medium (less guidance, multi-step)
  Level 1.3 — Hard (no guidance, combines ideas)
  BOSS LEVEL — Synthesis challenge using all World concepts

World 2: [Topic Group]
  Level 2.1 — Easy (uses World 1 skills + new concept)
  ...
  BOSS LEVEL

FINAL BOSS — A challenge requiring concepts from all Worlds
```

## Step 4: Assign Challenge Types

Read `references/challenge-types.md` (located at `.claude/skills/challenge/references/challenge-types.md`) for the 7 challenge types.

Assign a challenge type to each level. Rules:
- **Vary types** — Never have more than 2 same-type challenges in a row
- **Match type to concept** — Procedural skills get Compute; intuition gets Predict; common mistakes get Debug
- **Ramp complexity** — Easy levels tend toward Compute/Predict; Hard levels toward Construct/Connect
- **Boss levels** — Always use Connect or Construct type (synthesis)

## Step 5: Write Each Level

For each level, write all 5 components:

### Mission
A concrete, specific task with a clear success condition. Write it as a direct instruction:
- "Find the derivative of f(x) = 3x² + 2x at x = 4"
- "This gradient descent code has a bug. Find and fix it."
- "Build a function whose derivative is always positive but decreasing"

### Intel
Minimal context — just enough to make the mission possible. Think "hints from a mentor," not "textbook." Include:
- The key formula or rule needed (stated concisely)
- One worked example if the concept is new
- A reminder of relevant previous concepts

### Hints (3 tiers, in `<details>` tags)
1. **Hint 1** — A nudge in the right direction (conceptual)
2. **Hint 2** — A more specific clue (methodological)
3. **Hint 3** — A worked-through approach (nearly the answer)

### Solution
Full worked solution with:
- The code that solves the challenge
- The formal concept explanation — this is where the "teaching" happens, AFTER the learner has struggled
- Common mistakes and why they happen
- Connection to ML/AI: how this concept is used in practice

### Bonus Challenge
An optional harder variant for learners who found the main challenge easy. Should extend the concept, not just add complexity.

## Step 6: Add Progress Tracker and Scoring

At the top of the notebook, add a progress tracker:

```markdown
| Level | Challenge | Status | Points | Hints Used |
|-------|-----------|--------|--------|------------|
| 1.1 | [Name] | ⬜ | /10 | /3 |
```

Scoring rubric:
- Easy levels: 10 points base, -2 per hint used
- Medium levels: 15 points base, -3 per hint used
- Hard levels: 20 points base, -4 per hint used
- Boss levels: 30 points base, -5 per hint used
- Bonus challenges: +5 extra points each
- Final Boss: 50 points

## Step 7: Assemble the Notebook

Build the notebook with this structure:
1. **Title + Introduction** — Set the game frame
2. **Progress Tracker** — The scoring table
3. **World 1** — World intro, Levels, Boss Level
4. **World 2** — World intro, Levels, Boss Level
5. (repeat for each World)
6. **Final Boss** — The ultimate synthesis challenge
7. **Score Summary** — Total possible points, achievement levels

Use `<details>` tags for all hints and solutions so they're hidden by default.

## Step 8: Verify

Run the notebook to verify all code cells execute:

```bash
jupyter nbconvert --to notebook --execute <notebook>.ipynb
```

Check:
- All solution code cells produce correct output
- All `<details>` tags are properly closed
- No solution appears before its challenge
- Every level has all 5 components

## Step 9: Challenge Checklist

Before declaring the notebook done:

- [ ] Every concept from the source is covered by at least one challenge
- [ ] Concepts appear in a buildable order
- [ ] All levels have 5 components (Mission, Intel, 3 Hints, Solution, Bonus)
- [ ] Challenge types are varied (no more than 2 same-type in a row)
- [ ] Difficulty ramps smoothly within each World
- [ ] Boss levels require synthesis of the World's concepts
- [ ] Final Boss requires concepts from all Worlds
- [ ] All hints are in `<details>` tags
- [ ] All solutions are in `<details>` tags and execute correctly
- [ ] Progress tracker lists all levels with point values
- [ ] Common mistakes are anticipated in solutions
- [ ] ML/AI connections appear in solution explanations
- [ ] All code cells execute without errors

## Reference Files

- `references/challenge-types.md` — The 7 challenge types with descriptions, best-use cases, and examples
- `references/level-template.md` — The complete level template with all 5 components and formatting patterns
