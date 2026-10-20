# Agent Operating Instructions

## Before changing anything

1. Identify the user outcome and acceptance criteria.
2. Inspect the repository structure, relevant existing UI and implementation patterns.
3. Inspect available design-system primitives, tokens and component conventions.
4. Identify the available context sources and their reliability.
5. State important assumptions and missing information before making consequential design decisions.

Figma or Figma MCP may be available, but they are not required. Never assume that design intent must come from Figma.

## Context-first workflow

Use this sequence for UI work:

`Intent → Context → Design Decision → Implementation → Evidence → Outcome`

### Intent

Clarify:
- Who is the user?
- What are they trying to accomplish?
- What problem or opportunity are we addressing?
- What are the acceptance criteria?

### Context

Gather the strongest available evidence from:
- product requirements and research
- existing product UI
- repository code and architecture
- design tokens and components
- design-system documentation or Storybook
- screenshots, exports and written specifications
- Figma/Figma MCP when available and approved
- browser/runtime behaviour and existing tests

Do not invent missing context. If the missing information materially affects the experience, flag it for human decision.

### Design Decision

Before implementation, make the important decisions explicit:
- interaction model and information hierarchy
- component and pattern reuse
- content and terminology
- important states and transitions
- responsive behaviour
- accessibility considerations
- assumptions and trade-offs

### Implementation

Implement the smallest coherent change that satisfies the intent and follows existing repository conventions. Prefer existing primitives and tokens over new dependencies or one-off patterns.

### Evidence

Verify what can actually be verified in the environment. Use available tests, builds, browser checks, screenshots or other appropriate evidence.

Never claim a check passed unless it was actually run. If a desired check is unavailable, say so and identify the remaining uncertainty.

### Outcome

Review the result against the original intent, acceptance criteria and user experience. Record meaningful gaps, follow-up work and lessons that should improve the toolkit.

## Quality baseline

- Preserve semantic HTML and keyboard accessibility.
- Consider loading, empty, error, success and disabled states where relevant.
- Consider responsive behaviour rather than optimizing for one viewport.
- Reuse design-system components and tokens.
- Avoid speculative dependencies.
- Keep changes small and reversible.
- Protect secrets, credentials and confidential product information.
- Human approval is required for consequential external actions such as commit, push, merge, deployment or publishing when the host workflow requires it.
