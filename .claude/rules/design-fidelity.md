---
paths:
  - src/**/*.astro
  - src/**/*.css
  - src/**/*.ts
---

# Design Fidelity: Never Simplify Stitch Designs

## Core principle

Stitch-generated designs are the **source of truth**. They represent intentional design decisions made in a visual design tool. Your role is to implement them faithfully, not to interpret or improve them.

## What makes Stitch designs intentional

Professional designs use techniques that AI coding agents instinctively "fix":

- **Asymmetric grid splits** (7/5, 8/4, 3/3/6 columns) are deliberate, not mistakes
- **Varying section heights** (`py-48` hero, `py-6` stat bar, `pt-20 pb-12` content) create intentional rhythm
- **Full-bleed sections** breaking container boundaries are a design pattern, not a layout error
- **Overlapping elements** with negative margins or grid overlap are compositional choices
- **Edge-aligned text** using only `pl-24` instead of centered containers is a conscious decision
- **Offset content** starting at column 2 or 4 instead of column 1 is not misalignment

## Absolute prohibitions

- NEVER replace asymmetric layouts with symmetric ones
- NEVER add centering (`mx-auto`, `text-center`) where the design uses edge alignment
- NEVER normalize spacing to be consistent across sections — varied vertical rhythm is intentional
- NEVER wrap content in `max-w-7xl mx-auto` containers unless the source has them
- NEVER simplify complex Tailwind class combinations into "cleaner" alternatives
- NEVER remove visual complexity (gradients, overlays, layered elements) for "simplicity"
- NEVER convert `grid` layouts to `flex` or vice versa
- NEVER assume that unusual spacing, sizing, or positioning values are mistakes

## When you think something looks wrong

If a layout decision looks unusual or potentially broken:

1. **Check the source HTML first** — if the source has it, keep it
2. **Ask the user** before making any change to layout, spacing, or visual hierarchy
3. **Never silently "fix"** something — even if you are confident it is a bug

## The "AI look" to avoid

These patterns are hallmarks of AI-generated or template websites. Never introduce them:

- Every section using identical `py-24 max-w-7xl mx-auto` wrappers
- Perfectly symmetric 50/50 grid splits throughout
- Uniform card heights and spacing
- Centered everything with no edge tension
- Homogeneous section heights
- Missing full-bleed or overlapping elements

## Responsive adaptations

When adding responsive breakpoints, the goal is to make the existing design work on smaller screens, not to redesign it:

- Stack columns on mobile (`grid-cols-1`) but preserve desktop ratios at `md:` and above
- Reduce absolute spacing values proportionally, do not normalize them
- Maintain the relative scale differences between sections
- Keep full-bleed sections full-bleed at all breakpoints
