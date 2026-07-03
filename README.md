# artifact-designer-skill

Portable, harness-independent skill for creating polished, self-contained HTML artifacts.

The skill does not depend on Pi. It stores generated artifacts in `.artifacts/<id>/` and includes a Node.js helper for scaffolding, validation, local preview, import, listing, and optional Cloudflare Workers publishing.

## Contents

```text
artifact-designer/
  SKILL.md
  references/
    artifact-theme.css
    artifact-template.html
    design-system.md
  scripts/
    artifact.mjs
```

## Quick use

```bash
node artifact-designer/scripts/artifact.mjs create --title "Migration Dashboard" --instructions "Summarize the migration plan" --kind dashboard
node artifact-designer/scripts/artifact.mjs validate --id migration-dashboard --strict
node artifact-designer/scripts/artifact.mjs preview --id migration-dashboard --open
```

Edit the generated source file:

```text
.artifacts/<id>/source/index.html
```

## Design overrides

The skill checks for design guidance in this order:

1. Project: `.artifacts/DESIGN.md`
2. User: `~/.artifact-designer/DESIGN.md`
3. Built-in: `references/design-system.md` and `references/artifact-theme.css`

## Installation

Install this repository with `npx skills add geclos/artifact-designer-skill --skill artifact-designer`. The installable skill lives in `artifact-designer/` so supporting files are copied with `SKILL.md`.
