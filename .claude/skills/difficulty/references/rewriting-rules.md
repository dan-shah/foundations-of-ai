# Rewriting Rules

Detailed rules for transforming content between difficulty levels.

---

## Direction: Simplifying (Going to a Lower Level)

### Vocabulary Transformation
- Replace every technical term with a plain-language equivalent on first occurrence
- After defining a term in plain language, you may use the technical term with a reminder: "the derivative (remember: how fast something changes)"
- Avoid Latin/Greek terms unless they're the standard name (use "speed of change" before introducing "derivative")

### Notation Transformation
- Replace symbolic notation with verbal descriptions
- Example: Instead of `lim(h→0) [f(x+h) - f(x)] / h`, write: "What happens to the slope when we zoom in closer and closer?"
- When notation is introduced, build it piece by piece: "f(x) just means 'the output when we feed in x'"
- Use tables to bridge words to symbols gradually

### Scaffolding
- Before each new concept, add a brief "What you need to know first" section
- Use the pattern: "Remember how [previous concept]? Now imagine [new concept]..."
- Add "Check yourself" boxes: "Before reading on, can you explain [concept] in your own words?"
- Include wrong answers as learning moments: "A common mistake is thinking [X]. Actually, [Y] because..."

### Examples
- Multiply examples by 2-3x compared to the source
- Start with the simplest possible case, then gradually increase complexity
- Use contexts from the audience's world (see audience profiles)
- Include "predict before you calculate" prompts
- Add worked examples with every step shown

### Code Cells
- Add comments explaining each line
- Use descriptive variable names: `speed_at_each_second` not `dx`
- Add print statements showing intermediate values
- Simplify complex one-liners into multiple steps
- Keep the same mathematical operations

### Visual Descriptions
- Before every graph or plot, describe what the reader should look for
- After every graph, summarize what it showed: "Notice how..."
- Use spatial language: "goes up," "gets steeper," "flattens out"

---

## Direction: Deepening (Going to a Higher Level)

### Vocabulary Transformation
- Use precise technical terminology throughout
- Introduce terms with their formal definition, then use freely
- Reference standard notation and conventions from the field

### Notation Transformation
- Use full standard mathematical notation
- Add formal definitions using standard mathematical formatting
- Include quantifiers where appropriate
- Reference notation conventions: "Using the standard Leibniz notation..."

### Rigor Enhancement
- Add proof sketches for key results
- Include epsilon-delta definitions alongside intuitive ones
- Add "why this works" asides that connect to deeper theory
- Introduce edge cases and counterexamples
- Add "the careful reader will note that..." asides

### Examples
- Remove repetitive examples, keep only the most illustrative
- Add abstract/generalized examples
- Include counterexamples that test edge cases
- Replace worked-out steps with "verify that..." exercises
- Add connections to other fields: "Notice the similarity with [topology/analysis/etc.]"

### Code Cells
- Remove excessive comments (the reader can read code)
- Use concise, conventional variable names
- Add algorithmic complexity notes where relevant
- Include numerical stability considerations
- Can add more sophisticated implementations alongside simple ones

### Advanced Connections
- Add "Connections" callouts: "This generalizes to..." or "In measure theory..."
- Reference textbooks and papers for further reading
- Note when a simplified presentation hides subtlety
- Connect to research frontiers where appropriate

---

## Key Principles (All Directions)

### Never Condescending
- Simplifying does NOT mean dumbing down
- The ideas stay powerful; only the wrapping changes
- "This is the same idea that powers self-driving cars" — even for young audiences

### Preserve Agency
- Even at the lowest levels, prompt the reader to think, guess, and try
- Don't just tell — ask "What do you think happens when...?"
- Include moments where the reader discovers the idea before you state it

### Be Honest About Gaps
- When removing advanced content, briefly note what's being skipped:
  - "There's a more precise way to say this using limits — you'll see it later"
  - "Mathematicians have a formal proof of this that involves [X]"
- Never pretend the simplified version is the complete picture

### Maintain the Three Layers
Every concept should still have:
1. **The core idea** (adapted to audience level)
2. **Why it matters** (real-world or academic connection, adapted to audience)
3. **How it connects to ML/AI** (simplified or deepened as appropriate)
