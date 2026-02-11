# Scene Writing Guide

Every concept-scene follows a 5-part pattern.

---

## The 5-Part Scene Pattern

### Part 1: Narrative Hook (2-3 sentences)

**Purpose:** Set the scene, create tension or curiosity.

**Rules:**
- Start in medias res when possible
- Use sensory details — what do characters see, hear, feel?
- End with a question or problem the concept will answer
- Never start with "In this section, we'll learn about..."

**Example (Sci-Fi):**
> The proximity alarm shrieked. On the main display, Fragment 7-Alpha's trajectory curved sharply — it wasn't following the predicted path. "It's accelerating," Navigator Chen said. "But I need to know *how fast* that acceleration is changing, right now."

### Part 2: Discovery (1 paragraph)

**Purpose:** The character encounters the concept organically through action/dialogue.

**Rules:**
- The character should NEED the concept
- Use dialogue to voice the discovery
- Another character can play the skeptic
- Avoid "textbook voice" — keep it in character
- Build from existing knowledge to the new idea

**Example (Sci-Fi):**
> Chen pulled up the position data and started comparing consecutive readings. The gap was growing — it was speeding up. She zoomed in on two readings 0.1 seconds apart, then 0.01 seconds. "The closer together I sample," she realized, "the more precise the speed gets. What if I could sample at an infinitely small interval?"

### Part 3: Formal Definition (Callout Box)

**Purpose:** The actual mathematical definition. Preserves rigor.

**Format:**
```markdown
> **📐 The Mathematics**
>
> *[Concept Name]*
>
> $$[formula]$$
>
> Where:
> - $symbol_1$ = [meaning]
> - $symbol_2$ = [meaning]
>
> *In plain English: [one-line intuition]*
```

### Part 4: Application in Story (1-2 paragraphs)

**Purpose:** The character uses the concept to advance the plot (worked example).

**Rules:**
- Character explicitly applies the formula
- Show the numbers
- Include a code cell if computation is non-trivial
- The result should matter to the story
- Another character can verify or react

### Part 5: Reflection (1-2 sentences)

**Purpose:** Brief concept reinforcement.

**Rules:**
- Keep it short
- Can be dialogue or internal thought
- Connect back to story and mathematical concept
- Optionally foreshadow the next concept

---

## Dialogue Tips

### Voice Differentiation
- **The Thinker:** Longer sentences, "because" and "therefore," references principles
- **The Doer:** Shorter sentences, action verbs, "let me try," "hand me that"
- **The Skeptic:** Questions, qualifications, "but what if," "are we sure"
- **The Connector:** "This reminds me of," "it's like when," "same idea as"

### Concept Introduction Through Dialogue
Bad: "As you know, the derivative is defined as..."
Good: "Wait — when we tracked the signal decay, we looked at how fast it changed. What if we do the same thing here, with infinitely small samples?"

### Maintaining Tension
- Characters can disagree about approach
- Time pressure motivates quick calculation
- Consequences of wrong answers should be clear
- Let characters make mistakes and correct them

---

## Code Cell Integration

```python
# [Character name]'s calculation: [what they're computing]
# Story context: [why this matters]

fragment_position = lambda t: 2*t**3 + 5*t
fragment_velocity = lambda t: 6*t**2 + 5  # derivative

current_time = 4.7
speed = fragment_velocity(current_time)
print(f"Fragment speed at t={current_time}s: {speed:.1f} m/s")
```

**Rules:**
- Use story-relevant variable names
- Add comments referencing the story
- Print statements with story-relevant output
- Math must be identical to original notebook
- Frame with narrative: "Chen typed rapidly..." → code → "The result confirmed her theory."

---

## Pacing Guidelines

| Story Phase | Concept Density | Scene Length | Dialogue % |
|------------|----------------|-------------|-----------|
| Act 1 opening | Low (worldbuilding) | Long | 30% |
| Act 1 concepts | 1 per scene | Medium | 40% |
| Act 2 early | 1 per scene | Medium | 40% |
| Act 2 mid | 1-2 per scene | Medium-Long | 45% |
| Act 2 climax build | 2 per scene | Long | 40% |
| Act 3 climax | Synthesis | Long | 35% |
| Act 3 resolution | Reflection only | Short | 50% |
