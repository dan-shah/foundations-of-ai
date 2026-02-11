# D3.js Boilerplate and Coding Patterns

Standard template and patterns for generating self-contained interactive visualizations.

---

## Base HTML Template

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script src="https://d3js.org/d3.v7.min.js"></script>
<style>
  body {
    margin: 0;
    padding: 16px;
    background: #1a1a2e;
    color: #e0e0e0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', system-ui, sans-serif;
    font-size: 14px;
  }
  .viz-container { max-width: 700px; margin: 0 auto; }
  .controls { display: flex; flex-wrap: wrap; gap: 16px; margin-bottom: 12px; align-items: center; }
  .control-group { display: flex; align-items: center; gap: 8px; }
  .control-group label { font-size: 13px; color: #a0a0b0; min-width: 80px; }
  input[type="range"] { width: 120px; accent-color: #e94560; }
  .readout {
    font-family: 'SF Mono', 'Fira Code', monospace;
    font-size: 14px; color: #16c79a;
    background: #16213e; padding: 6px 12px; border-radius: 4px; margin-top: 8px;
  }
  svg { display: block; background: #16213e; border-radius: 8px; }
  .axis line, .axis path { stroke: #3a3a5c; }
  .axis text { fill: #8080a0; font-size: 11px; }
  .grid line { stroke: #2a2a4a; stroke-dasharray: 2,4; }
  button {
    background: #0f3460; color: #e0e0e0; border: 1px solid #3a3a5c;
    padding: 6px 14px; border-radius: 4px; cursor: pointer; font-size: 13px;
  }
  button:hover { background: #1a4a7a; }
  select {
    background: #16213e; color: #e0e0e0; border: 1px solid #3a3a5c;
    padding: 4px 8px; border-radius: 4px; font-size: 13px;
  }
</style>
</head>
<body>
<div class="viz-container">
  <div class="controls" id="controls"></div>
  <svg id="canvas" width="700" height="400"></svg>
  <div class="readout" id="readout"></div>
</div>
<script>
const width = 700, height = 400;
const margin = {top: 20, right: 30, bottom: 40, left: 50};
const plotW = width - margin.left - margin.right;
const plotH = height - margin.top - margin.bottom;

const svg = d3.select("#canvas");
const g = svg.append("g")
  .attr("transform", `translate(${margin.left},${margin.top})`);

const xScale = d3.scaleLinear().domain([-5, 5]).range([0, plotW]);
const yScale = d3.scaleLinear().domain([-5, 5]).range([plotH, 0]);

// Axes
g.append("g").attr("class","axis").attr("transform",`translate(0,${plotH})`)
  .call(d3.axisBottom(xScale).ticks(10));
g.append("g").attr("class","axis").call(d3.axisLeft(yScale).ticks(10));

// Grid
g.append("g").attr("class","grid").selectAll("line.h")
  .data(yScale.ticks(10)).enter().append("line")
  .attr("x1",0).attr("x2",plotW).attr("y1",d=>yScale(d)).attr("y2",d=>yScale(d));
g.append("g").attr("class","grid").selectAll("line.v")
  .data(xScale.ticks(10)).enter().append("line")
  .attr("y1",0).attr("y2",plotH).attr("x1",d=>xScale(d)).attr("x2",d=>xScale(d));

// YOUR VISUALIZATION CODE HERE

</script>
</body>
</html>
```

---

## Common Patterns

### Drawing a Function Curve

```javascript
function drawCurve(fn, color = "#e94560", strokeWidth = 2.5) {
  const pts = [];
  const [xMin, xMax] = xScale.domain();
  for (let x = xMin; x <= xMax; x += (xMax-xMin)/200) {
    const y = fn(x);
    if (isFinite(y) && Math.abs(y) < 1000) pts.push([x, y]);
  }
  return g.append("path").datum(pts)
    .attr("d", d3.line().x(d=>xScale(d[0])).y(d=>yScale(d[1])))
    .attr("fill","none").attr("stroke",color).attr("stroke-width",strokeWidth);
}
```

### Draggable Point on a Curve

```javascript
function createDraggablePoint(fn, onDrag) {
  let cx = 0;
  const pt = g.append("circle").attr("r",8)
    .attr("fill","#e94560").attr("stroke","#fff").attr("stroke-width",2)
    .attr("cursor","pointer").attr("cx",xScale(cx)).attr("cy",yScale(fn(cx)));

  pt.call(d3.drag().on("drag", function(event) {
    const x = Math.max(xScale.domain()[0], Math.min(xScale.domain()[1],
      xScale.invert(event.x)));
    const y = fn(x);
    if (isFinite(y)) {
      cx = x;
      pt.attr("cx",xScale(x)).attr("cy",yScale(y));
      if (onDrag) onDrag(x, y);
    }
  }));
  return { point: pt, getX: () => cx };
}
```

### Tangent Line

```javascript
function drawTangentLine(fn, dfn, x0, length = 3) {
  const y0 = fn(x0), slope = dfn(x0);
  const x1 = x0 - length/2, x2 = x0 + length/2;
  const colorScale = d3.scaleLinear()
    .domain([-5, 0, 5]).range(["#4a9eff","#ffffff","#e94560"]).clamp(true);

  return g.append("line")
    .attr("x1",xScale(x1)).attr("y1",yScale(y0+slope*(x1-x0)))
    .attr("x2",xScale(x2)).attr("y2",yScale(y0+slope*(x2-x0)))
    .attr("stroke",colorScale(slope)).attr("stroke-width",2)
    .attr("stroke-dasharray","6,3");
}
```

### Slider Control

```javascript
function addSlider(containerId, label, min, max, value, step, onChange) {
  const div = document.createElement("div");
  div.className = "control-group";
  const lbl = document.createElement("label");
  lbl.textContent = label;
  const input = document.createElement("input");
  Object.assign(input, {type:"range", min, max, value, step});
  const val = document.createElement("span");
  val.style.cssText = "min-width:40px;color:#16c79a";
  val.textContent = value;
  input.addEventListener("input", () => { val.textContent = input.value; onChange(+input.value); });
  div.append(lbl, input, val);
  document.getElementById(containerId).append(div);
}
```

---

## Multi-Section Page Layout

The output is a single-page scrolling HTML document with all visualizations as sections.

### Section Template

```html
<section id="viz-[id]" class="viz-section">
  <h2>[Concept Name]</h2>
  <p class="intro">[2-3 sentence concept intro]</p>
  <div class="viz-container">
    <div class="controls" id="[id]-controls"></div>
    <svg id="[id]-canvas" width="700" height="400"></svg>
    <div class="readout" id="[id]-readout"></div>
  </div>
  <div class="try-this">
    <strong>Try This:</strong>
    <ol>
      <li>[Observational prompt]</li>
      <li>[Investigative prompt]</li>
      <li>[Predictive prompt]</li>
    </ol>
  </div>
  <div class="formal-def">
    <h3>The Mathematics</h3>
    <p>[Formal definition with Unicode math or KaTeX]</p>
  </div>
</section>
```

### Page-Level Styles

```css
.viz-section {
  max-width: 780px;
  margin: 0 auto 60px;
  padding: 0 24px;
}
.viz-section h2 {
  color: #e94560;
  font-size: 24px;
  border-bottom: 1px solid #3a3a5c;
  padding-bottom: 8px;
}
.intro { color: #c0c0d0; line-height: 1.6; }
.try-this {
  background: #16213e;
  border-left: 3px solid #e94560;
  padding: 12px 16px;
  margin-top: 16px;
  border-radius: 0 4px 4px 0;
  line-height: 1.6;
}
.try-this strong { color: #e94560; }
.formal-def {
  background: #16213e;
  border-left: 3px solid #16c79a;
  padding: 12px 16px;
  margin-top: 12px;
  border-radius: 0 4px 4px 0;
}
.formal-def h3 { color: #16c79a; margin: 0 0 8px; font-size: 14px; }
```

### JavaScript Isolation

Each visualization's code MUST be wrapped in an IIFE and use unique element IDs:

```javascript
// Viz 1: Tangent Line Explorer
(function() {
  const svg = d3.select("#viz1-canvas");
  // ... all viz1 code here ...
})();

// Viz 2: Derivative Comparator
(function() {
  const svg = d3.select("#viz2-canvas");
  // ... all viz2 code here ...
})();
```

---

## Design System

### Color Palette
| Role | Color |
|------|-------|
| Background (body) | `#1a1a2e` |
| Background (panels) | `#16213e` |
| Primary curve | `#e94560` |
| Secondary curve | `#0f3460` |
| Accent / numbers | `#16c79a` |
| Text | `#e0e0e0` |
| Muted text | `#a0a0b0` |
| Grid | `#2a2a4a` |
| Borders | `#3a3a5c` |

### Slope Color Scale
- Negative: `#4a9eff` (blue)
- Zero: `#ffffff` (white)
- Positive: `#e94560` (red)

### Sizing
- Standard SVG: 700 x 400px
- Margins: 20/30/40/50 (top/right/bottom/left)
- Draggable point: 8px radius
- Stroke: 2.5px curves, 2px tangent, 1px grid
