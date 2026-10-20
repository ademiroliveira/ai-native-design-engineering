---
name: design-system-implementation
description: Reuse and extend existing design-system components and tokens while preserving visual consistency and maintainability.
---

# Design System Implementation

Before creating UI, inspect the repository's component library, tokens, typography, spacing, colour, motion, and interaction conventions.

Map design intent to existing semantic tokens before introducing raw values. Prefer semantic tokens over component-specific values when available, and record gaps where the design cannot be expressed cleanly.

Prefer composition and existing primitives over one-off styling. Introduce new primitives only when an existing abstraction cannot express the intended behaviour cleanly.