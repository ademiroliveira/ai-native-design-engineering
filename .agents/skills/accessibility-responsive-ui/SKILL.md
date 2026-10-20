---
name: accessibility-responsive-ui
description: Use when building, changing or reviewing user-facing UI — components, forms, dialogs, menus, navigation, layouts or interaction states. Checks the work against WCAG 2.2 AA (structure, keyboard and focus, accessible names, contrast, announcements, target size) and across viewport sizes, and reports each check as Verified, Partially verified or Unverified.
---

# Accessibility & Responsive UI

Accessibility and responsive behaviour are acceptance criteria, not polish. The default target is **WCAG 2.2 AA**; use the project's standard if it sets a different one.

Apply the checks to every changed component **in every important state** — default, focus, loading, empty, error, success, disabled — not only the default view. WCAG success criteria are given in brackets.

## While building

Prevent problems before checking for them:

- Use native elements before ARIA: `<button>` for actions, `<a href>` for navigation, `<label>` for inputs, `<fieldset>` and `<legend>` for groups. No click handlers on `<div>` or `<span>`.
- Reuse the design system's accessible primitives (dialog, menu, tabs, combobox) instead of building new ones.
- Don't remove focus outlines without a visible replacement.
- Don't add ARIA that repeats native semantics. Wrong ARIA is worse than none.
- Decide responsive behaviour from content priority before writing CSS: what stacks, collapses, truncates or moves into a menu at each breakpoint.

## Checks

### 1. Structure
- Headings form an outline: one `h1`, no skipped levels. [1.3.1]
- Landmarks (`header`, `nav`, `main`, `footer`) match the page layout. [1.3.1]
- Lists, tables and forms use their real elements. [1.3.1]
- Reading order and focus order match the visual order at every breakpoint. [1.3.2, 2.4.3]

### 2. Keyboard and focus
- Every interactive element can be reached with Tab and used without a mouse. [2.1.1]
- Enter activates links and buttons; Space activates buttons and checkboxes; arrow keys move within tabs, menus, radio groups and listboxes, following the ARIA Authoring Practices pattern for that widget.
- Escape closes dialogs, menus and popovers, and focus returns to the control that opened them.
- Modal dialogs keep focus inside while open. Nothing else traps focus. [2.1.2]
- The focus indicator is visible on every focusable element and isn't hidden behind sticky headers or overlays. [2.4.7, 2.4.11]
- After content is removed or replaced (delete, close, submit, route change), focus moves somewhere sensible — never to `<body>`.

### 3. Names, roles and states
- Every control has an accessible name. Icon-only buttons need `aria-label` or visually hidden text. [4.1.2]
- Inputs have a visible label. Placeholder text is not a label. [3.3.2]
- The accessible name contains the visible label text, so voice-control users can say what they see. [2.5.3]
- Exposed states match what is shown: `aria-expanded`, `aria-pressed`, `aria-selected`, `aria-current`, `aria-invalid`, `disabled`. [4.1.2]
- Informative images have alt text that describes their purpose; decorative images have `alt=""`. [1.1.1]

### 4. Colour and contrast
- Text is at least 4.5:1. Large text (24px, or 18.66px bold) is at least 3:1. [1.4.3]
- Control boundaries, focus indicators and meaningful icons or chart marks are at least 3:1 against adjacent colours. [1.4.11]
- Check hover, focus, error and placeholder colours, and every theme the product ships (for example dark mode). Disabled controls are exempt but should still look disabled.
- Colour is never the only signal for errors, required fields, status or links within text. [1.4.1]

### 5. Forms and errors
- Errors are described in text next to the field and linked with `aria-describedby`, and the field has `aria-invalid="true"`. [3.3.1]
- Error messages say how to fix the problem. [3.3.3]
- After a failed submit, focus moves to the first invalid field or to an error summary.
- Personal-data fields have the correct `autocomplete` value. [1.3.5]
- If a submit button is disabled, the UI explains what is missing.

### 6. Announcements and dynamic content
- Status messages (saved, results updated, loading finished, background errors) are announced without moving focus: `role="status"` or `aria-live="polite"`, and `role="alert"` only for urgent errors. [4.1.3]
- The live region exists in the DOM before text is injected into it; otherwise screen readers may not announce it.
- Content shown on hover or focus (tooltips, popovers) can be dismissed with Escape, can itself be hovered, and stays until dismissed. [1.4.13]

### 7. Motion
- Respect `prefers-reduced-motion`: remove or reduce non-essential animation.
- Nothing flashes more than three times a second. [2.3.1]
- Content that moves automatically for more than five seconds can be paused. [2.2.2]

### 8. Pointer and touch
- Targets are at least 24×24 CSS px, or spaced so that a 24px circle centred on each doesn't overlap another target. [2.5.8] Aim for 44×44px on touch-first surfaces.
- Anything done by dragging can also be done with a single tap or click. [2.5.7]
- Nothing depends on hover alone.

### 9. Responsive layout
- Use the project's breakpoints. If none are defined, check 320, 768 and 1280px widths.
- At 320px wide there is no horizontal scrolling, except for content that needs two dimensions (data tables, maps, code). [1.4.10]
- At 200% browser zoom, text and controls stay usable, with nothing clipped or overlapping. [1.4.4]
- Increased text spacing (line height 1.5, letter spacing 0.12em, word spacing 0.16em, paragraph spacing 2em) doesn't clip or overlap text. [1.4.12]
- The UI works in portrait and landscape. [1.3.4]
- Long names, long unbroken words, translated text and empty values don't break the layout. Truncated text is available in full somewhere.

## How to check

### With tooling
Use what the project already has. Don't add tooling for a single feature; record the missing capability as a gap instead.

- **Component tests:** query by role and accessible name (for example Testing Library `getByRole('button', { name: 'Save' })`). A query that fails because the name is missing is an accessibility bug. Use `jest-axe` or `vitest-axe` assertions if the project already does.
- **Storybook:** check the accessibility addon panel for every story that covers a changed state.
- **Browser:** run axe-core (for example `@axe-core/playwright` with the tags `wcag2a`, `wcag2aa`, `wcag21a`, `wcag21aa`, `wcag22aa`) on each changed state, not only on page load. Script the Tab order and capture a screenshot at each viewport.

A clean automated scan means "no automated violations found", not "accessible". Automated tools miss keyboard behaviour, focus management, announcement timing and whether names make sense. Those need a manual pass.

### Without tooling
- Run the checks by hand in a browser if one is available.
- If you can only read the code, say so. Findings from code alone are at most **Partially verified**.
- Screen reader: if one is available (VoiceOver, NVDA, TalkBack), run the primary flow with it. If not, list it under "Could not check" — it is the most common gap.

## Report

Status values (from `docs/WORKFLOW.md`):
- **Verified** — observed in the running UI, or asserted by a test that ran.
- **Partially verified** — only some states or viewports checked, automated checks only, or code reading only.
- **Unverified** — not checked. Say why.

Severity uses the Blocker / Major / Minor scale in `docs/WORKFLOW.md`. A failure that stops someone using a keyboard, screen reader, zoom or a small screen from completing the task is a Blocker, not a Major.

```markdown
### Accessibility & responsive review — <component or flow>

**Scope:** <states and viewports checked> · **Tools:** <what ran> · **Could not check:** <gaps and why>

| # | Check | WCAG | Result | Evidence | Status | Severity |
|---|-------|------|--------|----------|--------|----------|
| 1 | Focus returns to trigger when dialog closes | 2.4.3 | Fails: focus lands on `<body>` | Tab-order script, step 6 | Verified | Major |
```

## Common misses

- Only the default state was checked; loading and error states were never forced.
- Focus is lost after closing a dialog or deleting an item.
- Icon-only buttons have no accessible name.
- Placeholder text is the only label.
- A custom select, menu or combobox has no arrow-key support.
- Success toasts and inline updates aren't announced.
- `outline: none` with no replacement focus style.
- Fixed widths or long words cause horizontal scrolling at 320px.
- Hover-only actions can't be reached by keyboard or touch users.
