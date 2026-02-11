---
name: story
description: Transform a Foundations of AI notebook into a multi-chapter narrative where concepts are discovered by characters within a story arc. The learner absorbs material as a natural consequence of following the plot.
argument-hint: "[notebook-number] [genre]"
allowed-tools: Read, Bash, Edit, Write, Grep, Glob
---

# Transform Notebook into Story

You are transforming a notebook from the Foundations of AI curriculum into a narrative-driven learning experience. Each concept is encountered, needed, and applied by characters within a story. The learner reads the story and absorbs the material as a natural consequence of following the plot.

## Step 1: Parse Arguments

Extract the notebook number and genre from `$ARGUMENTS`.

- If both are provided (e.g., `02 sci-fi`), proceed.
- If only a number is provided, default to `sci-fi` genre.
- If a genre is provided without a number, ask for the notebook number.
- If neither is provided, ask for both.

**Supported genres:** sci-fi (default), mystery, fantasy, heist

Map the notebook number to its filename. Use Glob with pattern `{number}_*.ipynb` to find the exact file.

## Step 2: Extract Concepts

Read the target notebook. Produce a structured concept list with dependencies:

```
Concept 1: [Name] — [description] — Prerequisites: none
Concept 2: [Name] — [description] — Prerequisites: Concept 1
...
```

Note which concepts are foundational (Act 1), which build on others (Act 2), and which are synthesis/application (Act 3).

## Step 3: Load Genre Template

Read `references/genre-templates.md` (located at `.claude/skills/story/references/genre-templates.md`) for the genre-specific narrative frame:
- Setting and world rules
- Central problem/conflict
- How concepts appear in this world
- Character archetypes that fit
- Typical scene structures

## Step 4: Build the Three-Act Arc

Map concepts to a three-act structure:

### Act 1: Setup (First ~25% of concepts)
- Introduce characters, world, and the central problem
- Early concepts appear as worldbuilding and context-setting
- Establish the "rules" of the world that make math necessary
- End with an inciting incident that raises the stakes

### Act 2: Rising Action (Middle ~50% of concepts)
- Each new concept is a complication or tool needed to progress
- Concepts build on each other just as in the original material
- Each scene is motivated by a story need — characters NEED this math
- Include a midpoint twist or revelation that reframes earlier concepts

### Act 3: Climax + Resolution (Final ~25% of concepts)
- The most advanced/synthesis concepts appear here
- Characters combine everything they've learned
- The central problem is solved using accumulated knowledge
- Include a denouement that reflects on the journey

## Step 5: Design Characters (2-4)

Create 2-4 named characters with distinct roles:

| Role | Purpose | How They Learn |
|------|---------|---------------|
| **The Thinker** | Asks "why?" — represents theoretical understanding | Works through logic, sees patterns |
| **The Doer** | Asks "how?" — represents practical application | Tries things, writes code, runs experiments |
| **The Skeptic** | Asks "are you sure?" — represents critical thinking | Questions assumptions, finds edge cases |
| **The Connector** | Asks "what else?" — represents synthesis | Sees links between concepts |

Each character should have: a name fitting the genre, a clear role in the story, a distinct voice in dialogue, and a character arc that mirrors the learning arc.

## Step 6: Write Scenes

Read `references/scene-writing-guide.md` (located at `.claude/skills/story/references/scene-writing-guide.md`) for the 5-part scene pattern.

For each concept, write a scene following the pattern:
1. **Narrative hook** (2-3 sentences) — Set the scene, create tension/curiosity
2. **Discovery** (1 paragraph) — Character encounters the concept organically
3. **Formal definition** (callout box) — The actual math definition, clearly labeled
4. **Application in story** (1-2 paragraphs) — Character uses the concept to advance the plot
5. **Reflection** (1-2 sentences) — Brief summary of what was learned

### Writing Rules
- **Dialogue ratio:** ~40% dialogue to keep scenes dynamic
- **Concept density:** Max 2 major concepts per scene
- **Metaphor consistency:** Maintain the same metaphor for a concept throughout
- **Show, don't dump:** Weave explanations into action and dialogue
- **Formal definitions stand alone:** Clearly boxed so readers can find the "real math"

## Step 7: Execute Code and Capture Outputs

The output is a **standalone HTML page**, not a notebook. To include plots and code outputs:

1. Write a temporary Python script that executes all code cells from the source notebook
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

Build a single `.html` file with:

### Page Structure
- **Title block** — Title, subtitle, character cards with color-coded borders
- **Sticky navigation** — Links to each Act and the Concept Index
- **Act headers** — Large headings with decorative line separators
- **Scene sections** — Narrative text, dialogue, math callouts, code outputs, embedded plots
- **Epilogue** — Character reflections, ML/AI connection table
- **Concept Index** — Scene-to-concept mapping table

### Design System
- **Background:** `#0d0d1a` with subtle star-field CSS effect
- **Panels/code:** `#16213e` with `#2a2a4a` borders
- **Primary accent:** `#e94560` (danger, emphasis)
- **Secondary accent:** `#16c79a` (success, code output)
- **Character colors:** Reyes `#e94560`, Okafor `#16c79a`, Chen `#4fc3f7`, Park `#f5a623`
- **Math callout:** `#16213e` background with `#4fc3f7` left border

### Math Rendering
Include KaTeX from CDN for LaTeX rendering:
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.css">
<script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/katex.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/katex@0.16.9/dist/contrib/auto-render.min.js"></script>
```
Call `renderMathInElement(document.body)` on DOMContentLoaded.

### Embedding Plots
Embed base64 plots directly:
```html
<img src="data:image/png;base64,..." alt="description">
```

### Code Output Blocks
```html
<div class="code-block">
  <div class="code-header">Description</div>
  <pre>output text here</pre>
</div>
```

### Dialogue Format
```html
<div class="dialogue">
  <span class="speaker reyes">Reyes:</span>
  <span class="line">"Dialogue here"</span>
</div>
```

## Step 9: Create Concept Index

Add a `Concept Index` section at the bottom mapping story elements back to concepts:

| Scene | Story Element | Calculus Concept | Formal Definition |
|-------|--------------|-----------------|-------------------|
| Act 1, Scene 1 | [element] | [concept] | $formula$ |

## Step 10: Verify

Open the HTML file in a browser to verify:
- All plots render correctly
- KaTeX renders all math expressions
- Navigation links work
- Page is responsive and readable

```bash
open story_<notebook-name>.html
```

## Step 11: Story Checklist

- [ ] Every concept from the source appears in the story
- [ ] Formal definitions are present and mathematically accurate (KaTeX renders)
- [ ] The story is coherent and engaging on its own
- [ ] Concepts appear in a logical, buildable order
- [ ] Three-act structure is clear
- [ ] 2-4 characters with distinct roles and voices
- [ ] Characters are consistent throughout
- [ ] Metaphors are consistent
- [ ] ~40% dialogue ratio maintained
- [ ] Max 2 concepts per scene
- [ ] All plots embedded and rendering
- [ ] Code outputs formatted in styled blocks
- [ ] Concept index maps every scene to its source concept
- [ ] ML/AI connections appear naturally in the story
- [ ] Page opens and renders correctly in browser

## Reference Files

- `references/genre-templates.md` — Genre-specific settings, conflicts, concept mapping, and character archetypes
- `references/scene-writing-guide.md` — The 5-part scene pattern with examples, dialogue tips, and formatting
