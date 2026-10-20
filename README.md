# AI-Native Design Engineering

A portable toolkit for AI-assisted Product Design, UX/UI, Design Engineering and Frontend Engineering.

Designed to work across **GitHub Copilot** and **OpenCode** using shared skills and platform-specific agent definitions.

## Principles

- Product intent before implementation
- Reuse the design system before inventing UI
- Design states, not just happy paths
- Build accessible, responsive interfaces
- Verify rendered output, not only source code
- Prefer small, reversible changes
- Keep human product decisions explicit

## Structure

```text
.agents/skills/        Shared reusable skills
.github/agents/        GitHub Copilot agents
.github/prompts/       Reusable Copilot prompts
.opencode/agents/      OpenCode agents
AGENTS.md              Shared project instructions
```

## Agents

- **Product Design** — frames problems, flows, interaction models and UX decisions.
- **Design Engineer** — translates design intent into production UI.
- **Frontend Engineer** — handles component architecture, state, performance and maintainability.
- **UI Quality** — validates visual quality, accessibility, responsiveness and regressions.

## Workflow

`Frame → Specify → Build → Verify → Review`

## Adaptation

Customize the framework, design system, commands, component library and testing stack in `AGENTS.md` before using the toolkit in a production repository.
