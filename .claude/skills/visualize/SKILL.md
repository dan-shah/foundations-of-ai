---
name: visualize
description: Transform a Foundations of AI notebook into a standalone interactive HTML page with D3.js visualizations. Each abstract concept gets a corresponding interactive visual that learners can manipulate to build intuition through exploration.
argument-hint: "[notebook-number]"
allowed-tools: Read, Bash, Edit, Grep, Glob
---

# Create Interactive Visualizations

You are transforming a notebook from the Foundations of AI curriculum into a standalone HTML page with interactive, browser-based visualizations using D3.js. Each abstract concept gets a corresponding visual that learners can manipulate — dragging points, adjusting sliders, toggling overlays — to build intuition through exploration.

The output is a single self-contained `.html` file that opens in any modern browser. No Python, no Jupyter, no server required.

## Step 1: Parse Arguments

Extract the notebook number from `$ARGUMENTS`.

- If a number is provided (e.g., `02`), proceed.
- If not provided, ask the user which notebook to visualize.

Map the notebook number to its filename. Use Glob with pattern `{number}_*.ipynb` to find the exact file.

## Step 2: Audit Concepts for Visualization Potential

Read the target notebook. For each concept, categorize its visualization potential using the catalog in `references/viz-catalog.md` (located at `.claude/skills/visualize/references/viz-catalog.md`).

Produce a visualization plan:
```
Concept: [Name]
Viz Type: [from catalog]
Key Interaction: [what the user manipulates]
Key Insight: [what they discover through interaction]
Priority: [high/medium/low]
```

Aim for 4-8 visualizations per notebook, choosing concepts where interaction adds the most value.

## Step 3: Design Visualization Specs

For each planned visualization, write a spec:

```yaml
viz_id: [unique identifier]
concept: [the concept being visualized]
type: [from viz catalog]
components:
  - [visual element 1]
  - [controls: sliders, dropdowns, toggles]
interactions:
  - [interaction 1] → [visual response]
learning_moment: [what the user discovers]
```

## Step 4: Build the HTML Page

Read `references/d3-boilerplate.md` (located at `.claude/skills/visualize/references/d3-boilerplate.md`) for the HTML template and coding patterns.

Generate a single self-contained HTML file with all visualizations as sections on a scrolling page.

### Page Structure

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>[Notebook Name] — Interactive Visualizations</title>
  <script src="https://d3js.org/d3.v7.min.js"></script>
  <style>/* global styles */</style>
</head>
<body>
  <header>
    <h1>[Title]</h1>
    <p>[Brief intro about interacting with the visualizations]</p>
  </header>

  <section id="viz-1">
    <h2>[Concept Name]</h2>
    <p>[Brief concept introduction — 2-3 sentences]</p>
    <div class="viz-wrapper">
      <!-- SVG + controls + readouts -->
    </div>
    <div class="try-this">
      <strong>Try This:</strong>
      <ol><!-- guided prompts --></ol>
    </div>
    <div class="formal-def">
      <!-- LaTeX-rendered or plain-text formal definition -->
    </div>
  </section>

  <!-- ... more sections ... -->

  <section id="summary">
    <h2>Concept Summary</h2>
    <table><!-- maps each viz to its concept --></table>
  </section>

  <script>
    // All visualization code, each wrapped in an IIFE to isolate scope
    (function() { /* viz 1 */ })();
    (function() { /* viz 2 */ })();
    // ...
  </script>
</body>
</html>
```

### Technical Requirements
- Uses D3.js from CDN: `https://d3js.org/d3.v7.min.js`
- Completely self-contained — single `.html` file, no external dependencies beyond CDN scripts
- Opens directly in any modern browser (Chrome, Firefox, Safari, Edge)
- All CSS in a `<style>` block, all JS in `<script>` blocks
- SVG-based rendering for crisp scaling
- Each visualization's JavaScript wrapped in an IIFE to prevent variable collisions
- Each visualization targets unique element IDs (e.g., `viz1-canvas`, `viz2-canvas`)

### Visual Design
- Dark background (`#1a1a2e` body, `#16213e` panels)
- Vibrant curve colors (`#e94560`, `#0f3460`, `#16c79a`)
- Minimal chrome — let the math be the star
- Clean, readable fonts (system sans-serif)
- Slope coloring: blue (negative) to white (zero) to red (positive)
- Full-viewport sections with comfortable padding
- Smooth scroll between sections

### Interaction Design
- Drag = move a point
- Sliders = control parameters
- Toggles = show/hide overlays
- Dropdowns = switch between functions
- All interactions produce immediate, smooth visual feedback
- Touch-friendly targets (min 44px hit areas)

## Step 5: Write "Try This" Prompts

For each visualization, write 3-5 guided exploration prompts with a progression:

1. **Observational** — "Drag the point to the peak. What's the slope there?"
2. **Investigative** — "Find all points where the slope is zero."
3. **Predictive** — "Before toggling the overlay, predict what f'(x) looks like."
4. **Connective** — "How does this relate to [previous concept]?"

## Step 6: Add Formal Definitions

After each visualization's "Try This" section, include the formal mathematical definition. Use either:
- KaTeX from CDN (`https://cdn.jsdelivr.net/npm/katex/dist/katex.min.js`) for rendered LaTeX
- Plain Unicode math notation if KaTeX adds too much complexity

The definition should be brief — a reference card, not a lecture.

## Step 7: Verify

Open the HTML file in a browser and check:
- D3.js loads from CDN (requires internet connection)
- All visualizations render correctly
- Each interaction works (drag, slider, toggle, dropdown)
- No JavaScript console errors
- Page scrolls smoothly between sections
- Readouts update in real time

You can also validate the HTML structure:
```bash
# Check file exists and has reasonable size
ls -la [filename].html
# Quick syntax check — look for unclosed tags
grep -c '<script' [filename].html
grep -c '</script>' [filename].html
```

## Step 8: Visualization Checklist

- [ ] Output is a single self-contained `.html` file
- [ ] Every major concept has a corresponding visualization
- [ ] D3.js loaded from CDN correctly
- [ ] Each visualization has at least one meaningful interaction
- [ ] Each visualization's JS is isolated in an IIFE with unique element IDs
- [ ] "Try This" prompts guide toward key insights
- [ ] Formal definitions present alongside visualizations
- [ ] Visual design is consistent (dark theme, vibrant colors)
- [ ] Controls are labeled and intuitive
- [ ] Numerical readouts update in real time
- [ ] Mathematical computations in visualizations are correct
- [ ] No JavaScript console errors
- [ ] Concept summary table maps all visualizations to concepts
- [ ] File opens correctly in Chrome, Firefox, and Safari

## Reference Files

- `references/viz-catalog.md` — Visualization types with descriptions and best-use cases
- `references/d3-boilerplate.md` — HTML/CSS/JS template, D3 patterns, and design system
