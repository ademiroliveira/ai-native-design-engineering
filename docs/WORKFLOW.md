# Context-First UI Workflow

## Purpose

This workflow turns product intent into a verified interface while keeping design decisions, implementation choices and evidence inspectable.

It is deliberately tool-agnostic. Figma, Figma MCP, Storybook, Playwright or other integrations may improve the workflow, but none is a prerequisite.

## Workflow

```text
Intent
  ↓
Context
  ↓
Design Decision
  ↓
Implementation
  ↓
Evidence
  ↓
Outcome
  ↺
```

The loop is iterative. Evidence can reveal that the design decision or implementation needs to change.

## 1. Intent

Define the problem before discussing the solution.

Capture:
- user and scenario
- desired outcome
- problem/opportunity
- acceptance criteria
- constraints
- non-goals

Output: a concise feature brief or equivalent task definition.

## 2. Context

Build a shared understanding from available evidence.

### Preferred context hierarchy

1. Existing product behaviour and repository implementation
2. Approved product requirements and research
3. Existing design system, components and tokens
4. Screenshots, exports and written design specifications
5. Runtime/browser evidence and available tests
6. Figma/Figma MCP when available and approved

This is not a strict ranking for every situation. Use the sources that best answer the question and note conflicts between them.

### Context audit

Before implementation, identify:
- what is known
- what is inferred
- what is missing
- what conflicts
- what requires human confirmation

Output: a short context audit.

## 3. Design Decision

Translate the context into explicit product and interaction decisions.

Cover only what is relevant:
- information architecture
- interaction model
- component selection
- content hierarchy
- state model
- responsive behaviour
- accessibility
- error and recovery paths
- trade-offs

Output: a lightweight design specification or decision record.

## 4. Implementation

Implement against the agreed decisions.

Guidelines:
- reuse existing components and tokens
- follow repository conventions
- avoid unnecessary dependencies
- preserve existing behaviour outside the intended scope
- implement important states, not just the happy path
- keep changes small and reviewable

Output: working UI and implementation changes.

## 5. Evidence

Verify the implementation using the capabilities actually available.

Possible evidence:
- unit/integration tests
- type checking and linting
- build output
- browser interaction
- screenshots at relevant viewports
- accessibility checks
- visual comparison against approved reference material

Do not substitute an assumed tool for unavailable evidence. Clearly distinguish:

- **Verified** — directly observed or tested
- **Partially verified** — some relevant checks completed
- **Unverified** — the environment did not permit the check

Rate each problem found:

- **Blocker** — a user can't complete the task, loses data, or is locked out. This includes people using a keyboard, screen reader, zoom or a small screen.
- **Major** — the task can be completed but is confusing or difficult, or the change misses an acceptance criterion, fails the project's accessibility standard, or departs from the design system.
- **Minor** — polish or friction that doesn't affect completing the task.

List Blockers first.

Output: verification notes or evidence.

## 6. Outcome

Review the result against the original intent.

Ask:
- Does it solve the intended user problem?
- Does it meet acceptance criteria?
- Does it fit the existing product language?
- Are important states and edge cases covered?
- Is the result accessible and responsive?
- What remains uncertain?

Record meaningful corrections and lessons. Feed recurring lessons back into the toolkit rather than adding ad-hoc instructions to individual tasks.

## Human checkpoints

Human review should remain explicit at consequential points:

- product intent and scope
- ambiguous or conflicting context
- meaningful UX trade-offs
- sensitive or high-impact product behaviour
- final approval for external actions such as merge or deployment

AI can accelerate exploration and implementation, but it should not silently turn assumptions into product decisions.

## Pilot guidance

For a first pilot, choose a small UI feature with clear acceptance criteria and enough interaction complexity to expose states and responsive behaviour.

Run the complete workflow without requiring Figma MCP. After the pilot, record:
- where context was easy or difficult to obtain
- which decisions required human input
- where implementation diverged from intent
- which verification methods were actually available
- what should change in the toolkit

Use those findings to evolve the system. Do not add agents or integrations merely because they sound useful.
