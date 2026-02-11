---
name: challenge
description: Transform a Foundations of AI notebook into a game-like sequence of progressively harder challenges. Concepts are taught through missions, hints, and solutions rather than upfront explanation — learning through struggle.
argument-hint: "[notebook-number]"
allowed-tools: Read, Bash, Edit, Write, Grep, Glob
---

# Transform Notebook into Challenges

You are transforming a notebook from the Foundations of AI curriculum into a game-like challenge progression. Instead of reading explanations then trying problems, learners are dropped into challenges that *require* them to figure out concepts. Minimal upfront explanation; maximum active learning.

The output is a single self-contained `.html` file with interactive hints, a live score tracker, and a polished game-like UI.

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

### Hints (3 tiers)
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

Scoring rubric:
- Easy levels: 10 points base, -2 per hint used
- Medium levels: 15 points base, -3 per hint used
- Hard levels: 20 points base, -4 per hint used
- Boss levels: 30 points base, -5 per hint used
- Bonus challenges: +5 extra points each
- Final Boss: 50 points

## Step 7: Execute Code and Capture Outputs

The output is a **standalone HTML page**, not a notebook. To include plots and code outputs:

1. Write a temporary Python script that executes all solution code from the source notebook
2. Save matplotlib plots as base64-encoded PNGs using:
   ```python
   import io, base64
   buf = io.BytesIO()
   fig.savefig(buf, format='png', dpi=150, bbox_inches='tight', facecolor=fig.get_facecolor())
   b64 = base64.b64encode(buf.getvalue()).decode()
   ```
3. Capture text outputs as strings
4. Save all results to a JSON file for assembly

## Step 8: Assemble Standalone HTML Page

Build a single `.html` file named `challenge_<notebook-name>.html` in the working directory.

### Page Structure
- **Title block** — Game title, notebook topic, total points available
- **Sticky score bar** — Fixed top bar showing: current score, hints used, levels completed, progress percentage
- **World sections** — Each World is a collapsible group with its levels
- **Level cards** — Each level is a styled card with Mission, Intel, Hints, Solution, Bonus
- **Final Boss** — Visually distinct section with gold accent
- **Score Summary** — Achievement tiers and final badge

### Design System (Game Theme)
- **Background:** `#1a1a2e` body, `#16213e` panels
- **Panel borders:** `#2a2a4a`
- **Mission accent:** `#e94560` (red — urgency, left border on mission blocks)
- **Success/score:** `#16c79a` (teal — score bar, correct answers)
- **Intel accent:** `#4fc3f7` (cyan — info panels, formulas)
- **Hint accent:** `#f5a623` (orange — caution, hint buttons)
- **Boss levels:** Gold gradient highlight (`#f5a623` → `#e94560`)
- **Final Boss:** Gold border + glow effect
- **Text:** `#e0e0e0` body, `#ffffff` headings
- **Font:** System sans-serif stack

### Interactive Score Tracker

The sticky score bar at the top tracks progress in real time using JavaScript:

```html
<div id="score-bar">
  <span>Score: <strong id="current-score">0</strong> / <span id="total-possible">0</span></span>
  <span>Hints: <strong id="hints-used">0</strong></span>
  <span>Progress: <strong id="levels-complete">0</strong> / <span id="total-levels">0</span></span>
  <div id="progress-fill"></div>
</div>
```

JavaScript tracks:
- Which levels are marked complete (checkbox per level)
- Which hints have been opened (each hint click increments counter and reduces that level's score)
- Running score total updated on every interaction
- Progress bar fill width

### Interactive Hints

Hints use `<details>` elements with JavaScript tracking:

```html
<details class="hint" data-level="1.1" data-hint-num="1" data-penalty="2">
  <summary>Hint 1 — Conceptual Nudge (-2 pts)</summary>
  <div class="hint-content">...</div>
</details>
```

When a hint `<details>` is opened for the first time:
- Deduct points from that level's score
- Increment global hint counter
- Update the score bar
- Mark the hint as "used" (no double-penalty on re-open)

### Level Completion

Each level has a "Mark Complete" checkbox:
```html
<label class="complete-toggle">
  <input type="checkbox" data-level="1.1" data-base-points="10">
  Mark Complete
</label>
```

When checked, the level's adjusted score (base minus hint penalties) is added to the total.

### Math Rendering

Include KaTeX from CDN for LaTeX rendering:
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css">
<script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/contrib/auto-render.min.js"></script>
```
Call `renderMathInElement(document.body)` on DOMContentLoaded.

### Embedding Plots
Embed base64 plots from Step 7 directly:
```html
<img src="data:image/png;base64,..." alt="description" class="solution-plot">
```

### Code Blocks
```html
<div class="code-block">
  <div class="code-header">Solution Code</div>
  <pre><code>...</code></pre>
</div>
```

## Step 9: Verify

Open the HTML file in a browser to verify:
- KaTeX renders all math expressions
- Hints collapse/expand and track score correctly
- Score bar updates in real time
- All solution plots render
- Page is responsive and readable

```bash
open challenge_<notebook-name>.html
```

## Step 10: Challenge Checklist

Before declaring the challenge done:

- [ ] Output is a single self-contained `.html` file
- [ ] Every concept from the source is covered by at least one challenge
- [ ] Concepts appear in a buildable order
- [ ] All levels have 5 components (Mission, Intel, 3 Hints, Solution, Bonus)
- [ ] Challenge types are varied (no more than 2 same-type in a row)
- [ ] Difficulty ramps smoothly within each World
- [ ] Boss levels require synthesis of the World's concepts
- [ ] Final Boss requires concepts from all Worlds
- [ ] All hints are in interactive `<details>` tags with score penalties
- [ ] All solutions are in `<details>` tags with code blocks and plots
- [ ] Sticky score bar tracks points, hints, and progress in real time
- [ ] Level completion checkboxes work correctly
- [ ] Common mistakes are anticipated in solutions
- [ ] ML/AI connections appear in solution explanations
- [ ] KaTeX renders all math expressions
- [ ] All embedded plots render correctly
- [ ] Design uses game theme (dark background, colored accents)
- [ ] Page opens and renders correctly in browser

## Reference Files

- `references/challenge-types.md` — The 7 challenge types with descriptions, best-use cases, and examples
- `references/level-template.md` — HTML structure for levels with all 5 components and formatting patterns
