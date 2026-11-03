# Contributing

Thanks for helping improve these skills!

## Principles every skill must follow

- **Vendor-agnostic**: no instructions that rely on a specific agent, model,
  tool name or platform.
- **Self-contained**: a skill folder must work when copied alone. It must not
  depend on other skills, external services or specific people.
- **Never assume**: skills ask the user for missing business information
  instead of inventing it.
- **Language**: skills respond in the user's language unless the user
  explicitly asks for another.
- **Concise**: keep `SKILL.md` focused. Move long material into
  `references/` (loaded on demand) or `assets/` (templates).

## Skill layout

```text
skills/<skill-name>/
├── SKILL.md          # required: front matter (name, description, license, metadata) + instructions
├── assets/           # optional: templates used in the output
└── references/       # optional: supporting material read on demand
```

Front matter rules:
- `name`: lowercase letters, digits and hyphens, max 64 characters, equal to the folder name.
- `description`: 1–1024 characters, says **what** the skill does and **when** to use it.
- `metadata.version` (if present): should use semantic versioning (e.g., `1.0.0`).
- Relative links inside `SKILL.md` should:
  - point to files that exist in the skill folder,
  - stay inside the skill folder (no `../` escapes).

## Making a change

1. Update the skill and its `metadata.version` (semantic versioning).
2. Update `CHANGELOG.md` with an entry for the version (format: `### <skill>/v<version>`
   or `### <version>` depending on the existing style).
3. Open a pull request describing the behavior change.
