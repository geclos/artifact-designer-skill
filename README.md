# artifact-designer-skill

Portable skill for creating, validating, previewing, and publishing HTML artifacts.

New artifacts use `.artifacts/<id>/`. Existing HTML files can be validated, previewed, and published directly with `--file`.

## Layout

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

## New artifact

```bash
node artifact-designer/scripts/artifact.mjs create --title "Migration Dashboard" --instructions "Summarize the migration plan" --kind dashboard
node artifact-designer/scripts/artifact.mjs validate --id migration-dashboard --strict
node artifact-designer/scripts/artifact.mjs preview --id migration-dashboard --open
```

Edit:

```text
.artifacts/<id>/source/index.html
```

## Existing HTML file

```bash
node artifact-designer/scripts/artifact.mjs validate --file dist/report.html --strict
node artifact-designer/scripts/artifact.mjs preview --file dist/report.html --open
node artifact-designer/scripts/artifact.mjs publish --file dist/report.html --target temporary
```

Direct file validation does not require Artifact UI classes or design tokens.

## Design overrides

1. Project: `.artifacts/DESIGN.md`
2. User: `~/.artifact-designer/DESIGN.md`
3. Built-in: `artifact-designer/references/design-system.md`

## Installation

```bash
npx skills add geclos/artifact-designer-skill --skill artifact-designer
```
