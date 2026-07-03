# Artifact Designer Skill

Turn an agent into a small publishing studio for HTML artifacts.

This skill helps coding agents create, polish, preview, validate, and publish self-contained HTML pages: dashboards, reports, timelines, decision docs, benchmark viewers, prototypes, and walkthroughs.

It is also designed for a common fast path: if you already have an HTML file, the agent should publish that file directly instead of rebuilding it or wrapping it in a new project.

## What it is for

Use this skill when you want an agent to:

- create a shareable report from notes, data, diffs, benchmark results, or a PRD
- turn messy information into a clean interactive HTML artifact
- preview and validate an artifact before sharing it
- publish a static HTML page to a temporary or permanent public URL
- publish an existing HTML file exactly as-is

The skill bundles design guidance, a self-contained HTML template, validation rules, and publishing helpers. The user talks to the agent; the agent uses the bundled helpers behind the scenes.

## Example prompts

Create a new artifact:

> Create an artifact that explains this migration plan as a timeline with risks and owners.

> Build a dashboard artifact from these benchmark results. Include summary cards, a table, and a copyable JSON export.

> Turn this PRD into a shareable product brief with sections for goals, non-goals, milestones, and open questions.

Publish existing HTML directly:

> Publish `dist/report.html`.

> Preview this file and then publish it: `/tmp/lighthouse-summary.html`.

> Validate `coverage/index.html`; if it looks safe, publish it as a temporary URL.

Review or update an artifact:

> Open the latest artifact and tighten the design. Keep it self-contained.

> Add a decision matrix to the artifact and make the recommendation obvious.

> Import this published page, update the copy, and republish it.

## Behavior to expect

For new artifacts, the agent creates a project-local artifact under:

```text
.artifacts/<id>/
```

For existing HTML files, the agent should operate on the file directly. It should not create a wrapper artifact, copy the file into `.artifacts/`, or force the bundled design system onto it.

Validation has two modes:

- New artifacts: checks self-contained runtime rules, size limits, and expected design-system usage.
- Existing HTML files: checks publish safety and platform limits only. It does not require Artifact UI classes or design tokens.

## Design system

New artifacts use a restrained, developer-focused design system inspired by Geist: crisp borders, strong hierarchy, neutral surfaces, accessible contrast, and minimal motion.

You can override the design guidance with Markdown:

```text
.artifacts/DESIGN.md              # project override
~/.artifact-designer/DESIGN.md    # user default
```

## Installation

Install the skill into a compatible agent harness:

```bash
npx skills add geclos/artifact-designer-skill --skill artifact-designer
```

Then ask your agent to create, preview, validate, or publish an artifact.
