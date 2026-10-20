---
name: visual-qa
description: Use when critiquing how a rendered interface looks — visual hierarchy, layout, alignment, spacing, typography and consistency with the design system or an approved design. For accessibility and responsive checks use accessibility-responsive-ui; for a full review of a change use the UI Quality agent.
---

# Visual QA

Review the rendered interface, not source code alone. This skill covers visual craft. Accessibility and responsive behaviour are checked in `.agents/skills/accessibility-responsive-ui/SKILL.md`; states and regressions are part of the UI Quality agent's process.

## Checks

- **Hierarchy:** the most important content and the primary action are what the eye lands on first. More than one visually primary action in the same view is usually a finding.
- **Layout and alignment:** elements share edges and follow the page grid. Nothing is a few pixels off.
- **Spacing:** values come from the spacing scale or tokens. Off-scale values are findings.
- **Typography:** sizes, weights and line heights come from the type scale, and match equivalent text on neighbouring screens.
- **Components:** existing components are used as designed, without restyled copies or one-off variants.
- **Design reference:** where an approved design exists, compare at the same viewport and mark each difference as intended, a defect, or unclear.

## Rules

- Record observations separately from assumptions.
- Prioritise by user impact and confidence. Don't recommend changes for personal preference.
- Report with the status values and severity scale in `docs/WORKFLOW.md`.
