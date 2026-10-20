---
name: browser-visual-verification
description: Verify implemented UI in a browser using observable behaviour, screenshots, relevant viewports, and visual comparison when supported.
---

# Browser Visual Verification

When browser tooling is available, verify the rendered experience after implementation.

Check the primary flow and critical states at relevant viewport sizes. Capture evidence for notable observations and compare against approved design references or stable baselines when available.

Investigate meaningful visual differences rather than automatically accepting snapshots. Use the repository's existing visual-regression capability when present; do not add tooling without a clear need.

If browser access is unavailable, say so explicitly and use the strongest available evidence instead. Never claim visual verification without observed evidence.