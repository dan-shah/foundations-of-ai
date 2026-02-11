# Level Template (HTML)

Every level follows this exact HTML structure. All 5 components are required.

---

## Standard Level Format

```html
<div class="level" id="level-W-N" data-difficulty="easy|medium|hard" data-base-points="10|15|20">

  <div class="level-header">
    <h3>Level [World].[Number]: [Evocative Name]</h3>
    <div class="level-meta">
      <span class="badge type-badge">[Compute | Predict | Debug | Construct | Optimize | Connect | Estimate]</span>
      <span class="badge points-badge">[10 | 15 | 20] pts</span>
      <span class="badge diff-badge">[Easy | Medium | Hard]</span>
    </div>
    <label class="complete-toggle">
      <input type="checkbox" data-level="W.N" data-base-points="10"> Mark Complete
    </label>
  </div>

  <div class="mission">
    <h4>Mission</h4>
    <p>[A concrete, specific task with a clear success condition.]</p>
  </div>

  <div class="intel">
    <h4>Intel</h4>
    <p>[Minimal context — just enough to make the mission possible. The key formula or rule, one worked example if new, a reminder of relevant previous concepts.]</p>
  </div>

  <div class="hints">
    <h4>Hints</h4>

    <details class="hint" data-level="W.N" data-hint-num="1" data-penalty="2">
      <summary>Hint 1 — Conceptual Nudge (-2 pts)</summary>
      <div class="hint-content">
        <p>[A nudge in the right direction. Doesn't give away the method.]</p>
      </div>
    </details>

    <details class="hint" data-level="W.N" data-hint-num="2" data-penalty="2">
      <summary>Hint 2 — Methodological Clue (-2 pts)</summary>
      <div class="hint-content">
        <p>[A more specific clue about which method/formula to use.]</p>
      </div>
    </details>

    <details class="hint" data-level="W.N" data-hint-num="3" data-penalty="2">
      <summary>Hint 3 — Detailed Walkthrough (-2 pts)</summary>
      <div class="hint-content">
        <p>[A nearly-complete worked approach. Everything except the final computation.]</p>
      </div>
    </details>
  </div>

  <details class="solution">
    <summary>Reveal Solution</summary>
    <div class="solution-content">

      <div class="solution-section">
        <h5>The Answer</h5>
        <div class="code-block">
          <div class="code-header">Solution Code</div>
          <pre><code>[Runnable code that solves the challenge]</code></pre>
        </div>
        <img src="data:image/png;base64,..." alt="[description]" class="solution-plot">
      </div>

      <div class="solution-section">
        <h5>The Concept</h5>
        <p>[Formal explanation — this is where the teaching happens.]</p>
      </div>

      <div class="solution-section">
        <h5>Common Mistakes</h5>
        <ul>
          <li><strong>[Mistake 1]:</strong> [Why it happens and how to avoid it]</li>
        </ul>
      </div>

      <div class="solution-section">
        <h5>ML Connection</h5>
        <p>[How this concept appears in machine learning]</p>
      </div>

    </div>
  </details>

  <div class="bonus-challenge">
    <h4>Bonus Challenge (+5 pts)</h4>
    <p>[An optional harder variant that extends the concept.]</p>
  </div>

</div>
```

---

## Boss Level Format

```html
<div class="level boss-level" id="boss-W" data-difficulty="boss" data-base-points="30">

  <div class="level-header">
    <h3>Boss Level: [Dramatic Name]</h3>
    <div class="level-meta">
      <span class="badge type-badge">Connect or Construct</span>
      <span class="badge points-badge">30 pts</span>
      <span class="badge diff-badge boss">Boss</span>
    </div>
    <label class="complete-toggle">
      <input type="checkbox" data-level="boss-W" data-base-points="30"> Mark Complete
    </label>
  </div>

  <div class="mission">
    <h4>Mission</h4>
    <p>[Multi-part challenge combining all concepts from this World.]</p>
    <ol>
      <li>[Sub-task using Concept A]</li>
      <li>[Sub-task using Concept B]</li>
      <li>[Sub-task combining A + B + C]</li>
    </ol>
  </div>

  <div class="intel">
    <h4>Intel</h4>
    <p>[Recap of all concepts from this World.]</p>
  </div>

  <div class="hints">
    <h4>Hints</h4>
    [Same 3-tier details structure, but hints reference specific levels. Penalty: -5 pts each.]
  </div>

  <details class="solution">
    <summary>Reveal Solution</summary>
    <div class="solution-content">
      [Full multi-part solution with synthesis explanation.]
    </div>
  </details>

  <div class="bonus-challenge">
    <h4>Bonus Challenge (+5 pts)</h4>
    <p>[Bridge to the next World's topics.]</p>
  </div>

</div>
```

---

## Final Boss Format

```html
<div class="level final-boss-level" id="final-boss" data-difficulty="final-boss" data-base-points="50">

  <div class="level-header">
    <h3>Final Boss: [Epic Name]</h3>
    <div class="level-meta">
      <span class="badge type-badge">Construct</span>
      <span class="badge points-badge">50 pts</span>
      <span class="badge diff-badge final-boss">Final Boss</span>
    </div>
    <label class="complete-toggle">
      <input type="checkbox" data-level="final-boss" data-base-points="50"> Mark Complete
    </label>
  </div>

  <div class="mission">
    <h4>Mission</h4>
    <p>[A substantial project-style challenge requiring concepts from every World.]</p>
  </div>

  <div class="intel">
    <h4>Intel</h4>
    <p>[Comprehensive cheat sheet — formulas and key ideas, no explanations.]</p>
  </div>

  <div class="hints">
    <h4>Hints</h4>
    [Same 3-tier details structure, referencing specific Worlds and Levels. Penalty: -8 pts each.]
  </div>

  <details class="solution">
    <summary>Reveal Solution</summary>
    <div class="solution-content">
      [Complete solution with reflection mapping each part back to concepts learned.]
    </div>
  </details>

</div>
```

---

## CSS Classes Reference

| Class | Element | Purpose |
|-------|---------|---------|
| `.level` | `<div>` | Standard level container |
| `.boss-level` | `<div>` | Boss level — gold gradient top border |
| `.final-boss-level` | `<div>` | Final boss — gold border + glow |
| `.level-header` | `<div>` | Level title, meta badges, complete toggle |
| `.mission` | `<div>` | Mission block — `#e94560` left border |
| `.intel` | `<div>` | Intel block — `#4fc3f7` left border |
| `.hints` | `<div>` | Hints container |
| `.hint` | `<details>` | Individual hint — `#f5a623` accent |
| `.hint-content` | `<div>` | Hint body text |
| `.solution` | `<details>` | Collapsible solution |
| `.solution-content` | `<div>` | Solution body |
| `.solution-section` | `<div>` | Sub-section within solution |
| `.solution-plot` | `<img>` | Embedded base64 plot image |
| `.bonus-challenge` | `<div>` | Bonus challenge block — dashed border |
| `.code-block` | `<div>` | Styled code container |
| `.code-header` | `<div>` | Code block label |
| `.complete-toggle` | `<label>` | Level completion checkbox |
| `.badge` | `<span>` | Metadata badge (type, points, difficulty) |

## Data Attributes Reference

| Attribute | Element | Purpose |
|-----------|---------|---------|
| `data-level` | `.hint`, checkbox | Level identifier (e.g., "1.1", "boss-1") |
| `data-hint-num` | `.hint` | Hint number (1, 2, or 3) |
| `data-penalty` | `.hint` | Point deduction for opening this hint |
| `data-base-points` | checkbox | Base points for the level |
| `data-difficulty` | `.level` | Difficulty tier for styling |

## Scoring

| Difficulty | Base Points | Hint Penalty |
|-----------|-------------|-------------|
| Easy | 10 | -2 per hint |
| Medium | 15 | -3 per hint |
| Hard | 20 | -4 per hint |
| Boss | 30 | -5 per hint |
| Final Boss | 50 | -8 per hint |
| Bonus | +5 | — |

## Score Summary Section

```html
<div id="score-summary">
  <h2>Score Summary</h2>
  <table class="achievement-table">
    <thead>
      <tr><th>Achievement</th><th>Points Required</th><th>Badge</th></tr>
    </thead>
    <tbody>
      <tr><td>Completed</td><td>&gt; 0</td><td>Beginner</td></tr>
      <tr><td>Solid</td><td>&gt; 50%</td><td>Intermediate</td></tr>
      <tr><td>Strong</td><td>&gt; 75%</td><td>Advanced</td></tr>
      <tr><td>Perfect</td><td>100%</td><td>Master</td></tr>
      <tr><td>No hints</td><td>100% + no hints</td><td>Legend</td></tr>
    </tbody>
  </table>
</div>
```
