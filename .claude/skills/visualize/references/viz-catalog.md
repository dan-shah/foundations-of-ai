# Visualization Catalog

Eight visualization categories mapping concept types to interactive visual treatments.

---

## 1. Interactive Graph — Functions & Curves

**Description:** A function plotted on axes with slider-controlled parameters.

**Best For:** Function behavior — shapes, transformations, parameter effects.

**Interactions:** Sliders for parameters, dropdown to switch functions, hover for coordinates.

**Key Insight:** How parameters change curve shape and position.

---

## 2. Tangent Line Explorer — Rates & Derivatives

**Description:** A curve with a draggable point. Tangent line and slope readout follow the point.

**Best For:** Understanding derivatives as slopes, finding critical points.

**Interactions:** Drag point along curve, toggle f'(x) overlay, slope-colored tangent line (blue negative, white zero, red positive).

**Key Insight:** The derivative IS the slope of the tangent line. Where the curve peaks, the slope is zero.

---

## 3. Area Accumulator — Integrals & Accumulation

**Description:** Area under a curve that fills as the user drags bounds.

**Best For:** Integration as accumulation, Riemann sums, fundamental theorem.

**Interactions:** Drag bounds, toggle Riemann sum rectangles, slider for rectangle count.

**Key Insight:** The integral accumulates area. More rectangles = better approximation.

---

## 4. Zoom Animation — Limits & Continuity

**Description:** Animated zoom into a point, showing local behavior.

**Best For:** Limits, local linearity, continuity.

**Interactions:** Click "zoom in" repeatedly, toggle continuous/discontinuous functions.

**Key Insight:** Smooth curves look like straight lines when you zoom in enough (local linearity).

---

## 5. Step-Through — Chain Rule & Composition

**Description:** Multi-stage pipeline showing how input flows through composed functions.

**Best For:** Function composition, how derivatives chain together.

**Interactions:** Slider for input value, watch it flow through stages, see local stretching/compressing, toggle forward/backward pass.

**Key Insight:** The chain rule multiplies local rates of change through the chain.

---

## 6. Gradient Landscape — Optimization & 2D Surfaces

**Description:** 2D contour map or heatmap with draggable point and gradient arrows.

**Best For:** Gradient descent, local minima, saddle points.

**Interactions:** Drag point on surface, see gradient arrow, click "step" for gradient descent, slider for learning rate.

**Key Insight:** The gradient always points uphill. Descent follows the negative gradient.

---

## 7. Side-by-Side Panels — Comparisons & Relationships

**Description:** Two synchronized panels showing related quantities with linked cursor.

**Best For:** Function-derivative relationships, different representations of the same concept.

**Interactions:** Move cursor on one panel, see corresponding position on the other.

**Key Insight:** Corresponding features between related functions (zeros of f' = extrema of f).

---

## 8. Animated Transition — Transformations & Processes

**Description:** Before/after with smooth animated transition.

**Best For:** Iterative processes, Taylor series, function transformations.

**Interactions:** Play/pause, timeline scrub, speed control, step through iterations.

**Key Insight:** Understanding processes as sequences of transformations.

---

## Selection Guide

| If the concept involves... | Use this viz type |
|---------------------------|------------------|
| How a function behaves | Interactive Graph |
| Rate of change / slope | Tangent Line Explorer |
| Accumulation / area | Area Accumulator |
| Approaching a value | Zoom Animation |
| Composed functions / chains | Step-Through |
| 2D optimization / surfaces | Gradient Landscape |
| Comparing related quantities | Side-by-Side Panels |
| Iterative processes | Animated Transition |
