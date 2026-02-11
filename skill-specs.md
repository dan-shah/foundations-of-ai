# Content Transformation Skills — Detailed Specifications

These four skills share a common pattern: they take educational source material (a Jupyter notebook, markdown doc, or structured content) and transform it into a more engaging format. Each skill reads the source, applies a specific transformation strategy, and produces a new version of the content that teaches the same concepts through a different lens.

All skills should be designed to work with any subject matter — calculus, biology, programming, history — not just one topic.

---

## Shared Architecture

Every skill below follows this general flow:

1. **Parse** — Read the source material and identify discrete concepts, explanations, examples, and exercises
2. **Plan** — Decide how each concept maps to the skill's transformation (e.g., which story beat, which difficulty level, which visualization type)
3. **Transform** — Rewrite/restructure each section according to the skill's rules
4. **Assemble** — Produce the final output as a cohesive document (notebook, markdown, or HTML)

Each SKILL.md should instruct Claude to:
- Preserve all original learning objectives (nothing gets lost in translation)
- Maintain mathematical/technical accuracy (the transformation is cosmetic and pedagogical, not factual)
- Include metadata comments or annotations mapping transformed content back to original concepts so an instructor can verify coverage

---

## Skill 1: Story-Based Narrative Transformation

### What It Does

Converts educational material into a multi-chapter story where each concept is encountered, needed, and applied by characters within a narrative arc. The learner reads a story and absorbs the material as a natural consequence of following the plot.

### How It Works

**Step 1 — Concept Extraction**
The skill parses the source and produces a structured list:
```
Concept 1: Limits — what they are, notation, intuition
Concept 2: Derivatives — definition, power rule, chain rule
Concept 3: Applications — optimization, related rates
...
```

**Step 2 — Genre Selection**
The user provides a genre (or the skill defaults to one). Supported genres and their narrative templates:

| Genre | Narrative Frame | How Concepts Appear |
|-------|----------------|---------------------|
| **Mystery/Detective** | Solving a case, each clue requires a concept | "To decode the cipher, Detective Lena realized she needed to find the rate at which the signal was changing..." |
| **Sci-Fi/Space** | Crew navigating a mission, each obstacle is a concept | "The ship's trajectory was curving — to predict where it would be in 10 seconds, Commander Reyes needed the instantaneous rate of change..." |
| **Fantasy Quest** | Party on a journey, each challenge requires a concept | "The ancient door would only open when the water level in the chamber reached its maximum. Kael studied the flow..." |
| **Heist/Thriller** | Planning and executing a heist, each phase uses a concept | "To time the vault door's rotation perfectly, the crew needed to know exactly when it moved slowest..." |

**Step 3 — Story Arc Construction**
The skill maps concepts to a three-act structure:

- **Act 1 (Setup):** Introduce characters, world, and the central problem. Early concepts appear as worldbuilding and context-setting (definitions, notation, foundational ideas).
- **Act 2 (Rising Action):** Each new concept is a complication or tool needed to progress. This is where the bulk of the material lives. Concepts build on each other just as they do in the original material, but each one is motivated by a story need.
- **Act 3 (Climax + Resolution):** The most advanced/synthesis concepts appear here. The characters combine everything they've learned to solve the central problem.

**Step 4 — Scene Writing Rules**
For each concept-scene, the skill follows this pattern:
1. **Narrative hook** (2-3 sentences) — Set the scene, create tension or curiosity
2. **Discovery** (1 paragraph) — The character encounters the concept organically. The explanation is woven into action/dialogue, not dumped as exposition
3. **Formal definition** (callout box or aside) — The actual mathematical/technical definition, clearly labeled so the reader knows "this is the real thing." This preserves rigor
4. **Application in story** (1-2 paragraphs) — The character uses the concept to advance the plot. This serves as the worked example
5. **Reflection/check** (1-2 sentences) — A brief moment where the character (or narrator) summarizes what was learned. This is the concept reinforcement

**Step 5 — Output Format**
- Jupyter notebook with markdown cells for story + code cells for any computations the characters "perform"
- Or a standalone markdown/HTML document with clearly delineated story vs. formal content sections
- Include a "concept index" at the end mapping chapter/scene → original concept for instructor review

### Key Design Decisions the Skill Must Make
- **Character count:** 2-4 named characters with distinct roles (the thinker, the doer, the skeptic) so different learning perspectives are represented
- **Dialogue vs. narration ratio:** Aim for ~40% dialogue to keep it dynamic
- **Concept density:** No more than 2 major concepts per scene. If the source material has a dense section, split it into multiple scenes
- **Running metaphor consistency:** If derivatives are introduced as "velocity" in the story world, that metaphor should be maintained throughout, not switched arbitrarily

### Example Transformation
**Original:** "The derivative of f(x) at point a is defined as the limit of [f(a+h) - f(a)] / h as h approaches 0."

**Transformed (Sci-Fi):**
> "The asteroid field was shifting. Commander Reyes pulled up the position data — the fragments weren't moving at constant speed. 'I don't need to know where they are,' she muttered, dragging her finger along the trajectory curve on the display. 'I need to know where they're *going*.'
>
> She zoomed in on a single fragment's path, closer and closer, until the curve looked almost straight. That tiny straight-line slope — that was the answer. The fragment's instantaneous velocity.
>
> **[Formal: The derivative]**
> *The derivative of f(x) at point a is defined as:*
> *f'(a) = lim(h→0) [f(a+h) - f(a)] / h*
> *It represents the instantaneous rate of change of f at the point a.*
>
> Reyes keyed in the calculation. The slope at t = 4.7 seconds was 12.3 m/s bearing north-northwest. 'Hard starboard,' she called out. 'We've got a window.'"

### Eval Criteria
- Every concept from the source appears in the story (coverage)
- Formal definitions are present and accurate (rigor)
- The story is coherent and engaging on its own (narrative quality)
- Concepts appear in a logical/buildable order (pedagogical sequencing)
- A reader unfamiliar with the material could learn it from the story alone (self-sufficiency)

---

## Skill 2: Difficulty Adapter

### What It Does

Takes source material and a target audience, then rewrites it at the appropriate level of complexity, vocabulary, assumed knowledge, and depth. The same calculus notebook could become an introduction for a curious 12-year-old or a rigorous review for a grad student.

### How It Works

**Step 1 — Audience Profile**
The user specifies a target audience. The skill maps this to a profile with concrete parameters:

| Audience | Vocabulary Level | Math Notation | Assumed Knowledge | Explanation Depth | Example Style |
|----------|-----------------|---------------|-------------------|-------------------|---------------|
| **Middle Schooler (11-14)** | Everyday words, no jargon without definition | Minimal. Use words over symbols where possible. Avoid sigma notation, limit notation | Arithmetic, basic algebra, graphs as "pictures of equations" | Very deep on intuition, skip formal proofs entirely. Use "imagine..." and "think of it like..." heavily | Real-world, tangible: sports stats, phone battery drain, filling a pool |
| **High Schooler (15-18)** | Introduce technical terms with clear definitions on first use | Standard function notation, introduce limit notation gently | Algebra 2, basic trig, comfort with variables and equations | Balance intuition and formalism. Show why the formal definition matches the intuition | Mix of real-world and abstract: roller coasters, economics, physics |
| **College Freshman** | Technical terms used freely after first definition | Full standard notation | Precalculus, trig identities, some exposure to proofs | Start with intuition, quickly move to formal. Include "why does this work?" sections | More abstract, but still grounded: physics, optimization, engineering |
| **Grad Student / Reviewer** | Dense, precise, assumed familiarity | Full notation including epsilon-delta, measure theory hints | Undergraduate analysis, proof techniques, multivariable calc | Skip intuition unless it's genuinely novel. Focus on edge cases, generalizations, connections to other fields | Abstract, connecting to topology, functional analysis, etc. |
| **Non-Technical Adult** | Conversational, analogies over definitions | Almost none. Use visual/spatial descriptions instead | General numeracy. Can read a graph, understands "rate" colloquially | Very heavy on "why should I care?" and real-life relevance. Skip mechanics unless the person asks | Personal finance, cooking, health, travel, home improvement |
| **Someone's Grandparent** | Warm, patient, zero assumed jargon | None. Everything is described in words and pictures | Basic comfort with numbers | Extremely patient pacing. One idea at a time. Lots of "remember when we talked about X?" callbacks | Life experience: gardening growth rates, knitting patterns, recipe scaling |

**Step 2 — Content Audit**
The skill scans each section of the source and tags it:
- **Must keep:** Core concepts essential to the learning objectives
- **Simplify:** Concepts that can be explained at a lower level
- **Expand:** Concepts that need more depth for a higher-level audience
- **Add:** Background/prerequisites the target audience needs but the source doesn't cover
- **Remove:** Content above the target audience's level that isn't essential (e.g., epsilon-delta proofs for a middle schooler)

**Step 3 — Rewriting Rules by Direction**

*Simplifying (going to a lower level):*
- Replace every technical term with a plain-language equivalent on first occurrence
- Replace abstract notation with concrete verbal descriptions
- Add scaffolding: "Before we can understand X, let's make sure we're comfortable with Y"
- Multiply examples by 2-3x; make them progressively harder
- Add "check your understanding" moments after each concept
- Use shorter paragraphs and sentences
- Add visual descriptions ("Imagine a graph that looks like a hill...")

*Deepening (going to a higher level):*
- Remove repetitive examples, keep only the most illustrative one
- Add formal definitions, theorems, and proof sketches
- Add "connections" callouts: "This generalizes to..." or "Notice the similarity with..."
- Introduce edge cases and counterexamples
- Replace worked-out steps with "verify that..." exercises
- Add references to further reading (textbooks, papers)
- Increase information density per paragraph

**Step 4 — Consistency Pass**
After rewriting, the skill does a consistency sweep:
- Are all prereqs the target audience wouldn't know explained or removed?
- Is the vocabulary level consistent throughout (no sudden jumps)?
- Do examples match the audience's world? (Don't use "quarterly earnings" for a 12-year-old)
- Is the pacing appropriate? (Slow for lower levels, brisk for higher)

**Step 5 — Output Format**
- Same format as input (notebook → notebook, markdown → markdown)
- Include a "transformation notes" appendix listing what was added, simplified, removed, and why
- Include a difficulty rating (1-10) based on vocabulary complexity, notation density, and assumed prerequisites

### Key Design Decisions
- **Tone shifts with audience:** Warm and encouraging for younger/non-technical, collegial for grad students, patient for older adults
- **Never condescending:** Simplifying does NOT mean dumbing down. The ideas stay powerful; the wrapping changes
- **Preserve agency:** Even at lower levels, don't just tell — prompt the reader to think, guess, and try
- **Explicit about what's left out:** When removing advanced content, include a brief note: "There's a deeper version of this idea that involves [X] — you'll see it later if you keep going"

### Eval Criteria
- All core learning objectives are preserved (coverage)
- Vocabulary and notation match the target audience (level appropriateness)
- No concepts assume knowledge the target audience doesn't have (prereq check)
- Tone matches the audience (style)
- The content is still *accurate* even if simplified (rigor)
- A member of the target audience could realistically learn from this (usability)

---

## Skill 3: Game / Challenge Transformation

### What It Does

Converts educational material into a sequence of progressively harder challenges, puzzles, or levels. Instead of reading an explanation and then trying a problem, the learner is dropped into a challenge that *requires* them to figure out the concept. Minimal upfront explanation; maximum active learning.

### How It Works

**Step 1 — Concept Sequencing**
The skill takes the concept list from the source and ensures it's in a buildable order — each challenge can only use concepts from the current or previous levels. This may require reordering from the source.

**Step 2 — Challenge Design Framework**
Each concept becomes one or more "levels." Each level follows this structure:

```
┌─────────────────────────────────────┐
│  LEVEL N: [Evocative Name]          │
│                                     │
│  🎯 MISSION                        │
│  A concrete, specific task with a   │
│  clear success condition.           │
│                                     │
│  📋 INTEL                           │
│  Minimal context — just enough to   │
│  make the mission possible. NOT a   │
│  full explanation. Think "hints      │
│  from a mentor," not "textbook."    │
│                                     │
│  💡 HINT SYSTEM (3 tiers)           │
│  Hint 1: A nudge in the right       │
│          direction (conceptual)     │
│  Hint 2: A more specific clue       │
│          (methodological)           │
│  Hint 3: A worked-through approach  │
│          (nearly the answer)        │
│                                     │
│  ✅ SOLUTION                        │
│  Full worked solution with the      │
│  formal concept explanation. This   │
│  is where the "teaching" happens —  │
│  AFTER the learner has struggled.   │
│                                     │
│  ⭐ BONUS CHALLENGE                 │
│  An optional harder variant for     │
│  learners who found it easy.        │
└─────────────────────────────────────┘
```

**Step 3 — Challenge Type Variety**
The skill rotates through different challenge types to maintain engagement:

| Challenge Type | Description | Best For |
|----------------|-------------|----------|
| **Compute** | "Find the value of..." | Procedural skills (taking derivatives, solving equations) |
| **Predict** | "What will happen when..." | Building intuition (before showing the graph, guess its shape) |
| **Debug** | "This solution has an error. Find and fix it." | Common misconceptions (forgetting chain rule, sign errors) |
| **Construct** | "Build a function that satisfies these conditions..." | Deep understanding (reverse-engineering) |
| **Optimize** | "Find the best/fastest/cheapest..." | Applied concepts (optimization, related rates) |
| **Connect** | "These two things look different but are the same idea. Explain why." | Synthesis and transfer |
| **Estimate** | "Without calculating, roughly what is..." | Number sense, reasonableness checking |

**Step 4 — Progression Mechanics**
The skill structures levels into "worlds" (conceptual groups) with a difficulty ramp:

```
World 1: Limits
  Level 1.1 — Easy (guided, one-step)
  Level 1.2 — Medium (less guidance, multi-step)
  Level 1.3 — Hard (no guidance, combines ideas)
  BOSS LEVEL — Synthesis challenge using all World 1 concepts

World 2: Derivatives
  Level 2.1 — Easy (uses World 1 skills + new concept)
  ...
  BOSS LEVEL

FINAL BOSS — A challenge requiring concepts from all worlds
```

**Step 5 — Feedback Loops**
For each challenge, the skill designs specific feedback:
- **Common wrong answers** are anticipated and addressed: "If you got 2x, you might have forgotten the chain rule. Here's where it applies..."
- **Partial credit** is acknowledged: "You've got the right setup! The issue is in the last step..."
- **Encouragement** is calibrated to difficulty: Easy levels get minimal praise. Hard levels get "This was a tough one — nice work."

**Step 6 — Output Format**
- Jupyter notebook with interactive code cells where the learner writes and runs their solutions
- Or a markdown document with clearly separated MISSION / INTEL / HINTS / SOLUTION sections (hints and solutions in collapsible sections or marked for hide/reveal)
- Include a progress tracker: a markdown table at the top listing all levels with checkboxes
- Include a scoring rubric: each level is worth points based on difficulty, with bonuses for solving without hints

### Key Design Decisions
- **Struggle is the point.** The skill must resist the urge to over-explain upfront. Learning happens in the gap between "I don't know" and the solution
- **Hints, not just answers.** The 3-tier hint system is critical — it lets learners calibrate how much help they want
- **No dead ends.** Every challenge must be solvable with the INTEL provided + hints. If it's not, the INTEL is insufficient and the skill should add more
- **Boss levels are essential.** They force synthesis and prevent learners from only understanding concepts in isolation
- **Variety prevents fatigue.** Never have more than 2 same-type challenges in a row

### Eval Criteria
- Every concept from the source is covered by at least one challenge (coverage)
- Challenges are solvable with the given intel + hints (solvability)
- Difficulty progression is smooth (no sudden spikes) (progression)
- Solutions are correct and well-explained (rigor)
- Challenge types are varied (engagement)
- Boss levels genuinely require synthesis (integration)
- Common mistakes are anticipated in the feedback (pedagogy)

---

## Skill 4: Interactive Visualization Transformation

### What It Does

Augments educational material with rich, interactive visualizations — each abstract concept gets a corresponding visual that the learner can manipulate (change parameters, drag points, toggle elements) to build intuition through exploration. The primary output is a web-based HTML document or a set of standalone interactive components using D3.js or similar libraries.

### How It Works

**Step 1 — Visual Audit**
The skill scans each concept in the source and categorizes its visualization potential:

| Category | Visualization Type | Example |
|----------|-------------------|---------|
| **Functions/Curves** | Interactive graph with draggable parameters | y = ax² + bx + c with sliders for a, b, c |
| **Rates/Derivatives** | Tangent line that moves along a curve, slope displayed | Drag a point along f(x), see f'(x) update live |
| **Accumulation/Integrals** | Area under curve that fills as you drag bounds | Move left/right bounds, see area value change |
| **Limits** | Zoom animation approaching a point | Click "zoom in" repeatedly, see the function's behavior |
| **Sequences/Series** | Progressive addition visualization | Each term adds a block; partial sums grow toward the limit |
| **Optimization** | 2D/3D landscape with a movable point | Drag a point on a surface, see gradient arrows, find the minimum |
| **Comparisons** | Side-by-side synchronized panels | f(x) on left, f'(x) on right, linked cursor |
| **Transformations** | Before/after with animated transition | Apply chain rule step-by-step with visual morphing |

**Step 2 — Visualization Design Spec**
For each visualization, the skill produces a spec:

```yaml
viz_id: derivative_tangent_line
concept: "Derivative as slope of tangent line"
type: interactive_graph
components:
  - curve: "f(x) = x³ - 3x + 1" (or user-configurable)
  - tangent_line: line tangent to curve at movable point
  - slope_readout: numerical display of current slope
  - derivative_curve: optional overlay of f'(x)
interactions:
  - drag point along curve → tangent line and slope update in real time
  - toggle f'(x) overlay to compare
  - dropdown to switch between different functions
  - slider for animation speed (auto-sweep the point across the curve)
learning_moment: >
  The user sees that when the tangent line is flat, the derivative
  is zero (the "critical points"). When the tangent tilts steeply,
  the derivative is large. This builds physical intuition for what
  the derivative IS.
annotations:
  - At critical points, flash a label: "Slope = 0 → Critical Point!"
  - Color the tangent line by slope: blue (negative) → white (zero) → red (positive)
```

**Step 3 — Technical Implementation**
The skill generates self-contained HTML files with embedded JavaScript using:

**Primary library: D3.js** — for custom, precise, publication-quality visualizations
- SVG-based rendering for crisp scaling
- D3 transitions for smooth animations
- D3 drag behaviors for interactivity

**Supporting libraries (as needed):**
- **Math.js** — for evaluating mathematical expressions, symbolic differentiation
- **KaTeX** — for rendering mathematical notation inline in the visualization
- **Plotly.js** — as a fallback for standard 3D plots (optimization landscapes)

**Code structure per visualization:**
```
<div id="viz-[concept]">
  <div class="controls">     <!-- sliders, dropdowns, toggles -->
  <svg class="canvas">        <!-- the visualization -->
  <div class="readouts">      <!-- numerical displays, equations -->
  <div class="explanation">   <!-- brief text explaining what to try -->
</div>
```

**Step 4 — Guided Exploration Prompts**
Each visualization includes a set of "try this" prompts that guide the learner toward key insights:

```
🔍 Try This:
1. Drag the point to where the curve has a peak. What's the slope there?
2. Now drag it to the steepest part of the curve. What happens to the derivative?
3. Toggle on the f'(x) overlay. Where does f'(x) cross zero? What's
   happening on the f(x) curve at those same x-values?
4. Switch to f(x) = sin(x). Can you predict what f'(x) looks like
   before toggling the overlay?
```

These prompts are progression-based: early ones are observational ("what do you see?"), later ones are predictive ("what do you think will happen?"), and final ones are connective ("how does this relate to [previous concept]?").

**Step 5 — Layout and Assembly**
The skill assembles visualizations into a coherent document:

**Option A: Single-page scrolling webapp**
- Each concept gets a full-viewport section
- As you scroll, visualizations come into view and activate
- Text explanations flank the visualizations
- Smooth scroll-linked animations where appropriate

**Option B: Jupyter notebook with embedded HTML**
- Each cell contains an `IPython.display.HTML()` call with the self-contained visualization
- Markdown cells provide context between visualizations
- Code cells let learners modify parameters and re-run

**Option C: Standalone HTML files per concept**
- One file per visualization, linked from an index page
- Simplest to share and embed individually

**Step 6 — Visual Design Principles**
The skill follows these design rules:
- **Dark background, vibrant curves** — Easier on the eyes, curves pop. Use a palette like: background #1a1a2e, curves #e94560 / #0f3460 / #16c79a
- **Minimal chrome** — No heavy borders, legends, or axis labels unless needed. Let the math be the star
- **Responsive** — Works on desktop and tablet. Touch-friendly drag targets (min 44px)
- **Accessible** — Colorblind-safe palette options. Keyboard navigable. Screen reader descriptions for key states
- **Progressive disclosure** — Start simple (just the curve). Let the user add complexity (toggle tangent, toggle derivative, add second function)
- **Consistent interaction patterns** — Drag always means "move a point." Sliders always control parameters. Toggles always show/hide overlays

### Key Design Decisions
- **Interactivity > pretty pictures.** A static graph is a textbook figure. The value is in *manipulation* — the learner changes something and sees the consequence. Every visualization must have at least one meaningful interaction
- **One concept per visualization.** Don't overload. If a viz needs to show two concepts (e.g., derivative AND integral), split into two linked panels rather than one cluttered one
- **"Explore first, explain after" option.** The skill should support a mode where explanations are hidden until the learner has played with the visualization for a moment. Discovery before definition
- **The visualization IS the explanation.** Where possible, the visual should make the text explanation almost redundant. If you remove the text, the visualization + prompts should still teach the concept

### Eval Criteria
- Every major concept has a corresponding visualization (coverage)
- Visualizations are technically correct — curves, tangent lines, areas compute properly (accuracy)
- Interactions are smooth and responsive, no jank (UX quality)
- "Try this" prompts lead to genuine insights (pedagogy)
- The HTML/JS is self-contained and works in a modern browser without a server (portability)
- Visual design is clean, readable, and consistent (aesthetics)
- Visualizations work without the text (standalone clarity)

---

## Building These Skills: Practical Notes for Claude Code

### File Structure for Each Skill
```
skill-name/
├── SKILL.md              # The core skill instructions
├── evals/
│   ├── evals.json        # Test cases: source material + expected behavior
│   └── files/            # Sample input notebooks/docs for testing
└── templates/            # (optional) Reusable templates, boilerplate code
```

### Recommended Build Order

1. **Difficulty Adapter** — Simplest transformation (rewriting, not creating new structure). Good for validating the shared parsing/concept-extraction step that all skills will need.
2. **Game/Challenge** — Next simplest structurally (clear template per level). Tests the skill's ability to create novel content (challenges) from existing material.
3. **Story-Based Narrative** — Requires creative writing ability + structural planning. Harder to evaluate objectively. Build after you have confidence in concept extraction.
4. **Interactive Visualization** — Most technically complex (generates working code). Build last so you can focus on code correctness without worrying about the transformation logic.

### Testing Strategy
For each skill, create 2-3 eval cases:
- **Small input:** A single-concept section (e.g., just "what is a derivative?"). Tests that the transformation works at the atomic level
- **Medium input:** A 3-5 concept section (e.g., "limits, derivatives, and the power rule"). Tests concept sequencing and connections
- **Cross-domain input:** A non-math topic (e.g., a section on DNA replication or supply/demand). Tests that the skill is truly subject-agnostic

### Composability
These skills should be designed to compose. A learner could get:
- A story (Skill 1) adapted to middle school level (Skill 2)
- A game (Skill 3) with interactive visualizations embedded in each level (Skill 4)
- A visualization page (Skill 4) with difficulty adapted for grad students (Skill 2)

To enable this, each skill should accept the output of another skill as input, not just raw source material. The concept annotations / metadata each skill embeds make this possible.
