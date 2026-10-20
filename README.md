# AI-Native Design Engineering

A portable, context-first toolkit for AI-assisted Product Design, UX/UI, Design Engineering and Frontend Engineering.

The approach is designed to work across tools such as GitHub Copilot and OpenCode without depending on a specific editor, model, MCP server or design application.

## Operating model

`Intent → Context → Design Decision → Implementation → Evidence → Outcome`

The workflow is iterative. Verification may send work back to the design decision or implementation stage. The goal is not simply to generate code; it is to deliver a useful, accessible, maintainable experience and make the evidence behind quality claims visible.

## Principles

- Start with the user outcome and product intent, not a proposed UI.
- Inspect the repository, existing interface and design system before changing code.
- Make assumptions and missing context explicit.
- Reuse established components, tokens and interaction patterns before inventing new ones.
- Design the important states, including loading, empty, error, success and disabled states where relevant.
- Consider accessibility, responsive behaviour and keyboard interaction.
- Verify the rendered experience where practical; source-code review alone is not visual verification.
- Make small, reversible changes and preserve existing conventions.
- Keep product decisions, risky actions and final approval with people.
- Never claim a test, browser check or build passed unless it was actually run and its result observed.

## Context sources

**Figma MCP is optional.** Context can come from any suitable combination of:

- Product briefs, acceptance criteria and user research
- Repository structure, existing code and current product UI
- Design tokens, component libraries, design-system docs and Storybook
- Screenshots, exports, annotated mockups and written design specifications
- Browser inspection, available tests and runtime behaviour
- Figma files or Figma MCP, when available and approved

Prefer direct evidence over assumptions. When sources conflict, document the conflict and ask for a decision if it changes the user experience or technical approach.

## Role model

These responsibilities can be handled by separate agents, a single assistant, or a human/AI team:

- **Product Design** — frames the problem, user needs, journey and interaction decisions.
- **Design Engineer** — translates design intent into coherent interface behaviour and visual implementation.
- **Frontend Engineer** — protects component architecture, state, performance and maintainability.
- **UI Quality** — checks visual consistency, accessibility, responsiveness and regressions.

Use separate agents only when the work benefits from clear boundaries or independent review. More agents are not automatically better.

## Repository contents

- `AGENTS.md` — shared instructions for AI coding assistants, including the Project specifics to fill in
- `docs/WORKFLOW.md` — the end-to-end workflow, status values and severity scale
- `.agents/skills/` — tool-agnostic skills: detailed procedures loaded when a task matches
- `.github/` — GitHub Copilot instructions, agents and prompts, plus the pull request template
- `.opencode/agents/` — OpenCode agents

See `docs/FILE-MAP.md` for every file. Add further agents, prompts, skills or integrations only when they solve a demonstrated need and can be maintained.

## Getting started

1. Read `AGENTS.md` and `docs/WORKFLOW.md`.
2. Copy the toolkit files into the host project and fill in the Project specifics table in `AGENTS.md`: commands, design-system paths, breakpoints and design references.
3. Choose a small, low-risk UI feature with clear acceptance criteria.
4. Run the workflow end to end, including verification and human review.
5. Record gaps and improve the toolkit based on evidence from the pilot.

Do not assume a particular tool is available. Define the capability needed, use the best permitted method in the environment, and disclose any checks that could not be performed.
