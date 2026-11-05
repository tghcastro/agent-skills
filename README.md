# agent-skills

Vendor-agnostic AI agent skills for writing PRDs, requirements and test plans.

Each skill is a self-contained folder that follows the open
[Agent Skills](https://agentskills.io) format (`SKILL.md` + optional `assets/`
and `references/`). They work with any agent that supports skills, such as
Claude, GitHub Copilot and Cursor.

## Design Philosophy

Skills in this repository are built on these principles:
- **Vendor-agnostic**: no instructions that rely on a specific agent, model, tool
  or platform.
- **Never assume**: skills ask users for missing business information instead of
  inventing it.
- **Language-aware**: skills respond in the user's language unless explicitly asked
  otherwise.
- **Concise**: skills focus on the core workflow, moving long material into
  supporting files loaded on demand.

## Skills

| Skill | What it does | For |
|---|---|---|
| [create-prd](skills/create-prd/) | Interviews you and writes a concise PRD for a whole project or a single feature. Accepts chat, documents and work items as input, and never assumes business rules. | PMs, Developers, QA Engineers |
| [create-test-plan](skills/create-test-plan/) | Interviews you and writes a test plan with acceptance scenarios (Gherkin) and validation checklists for a feature. Uses testing heuristics to suggest scenarios. | QA Engineers, Developers, PMs |


## Installation

Copy the folder of the skill you want (e.g., `skills/create-prd/`) into the
skills directory your agent reads. Check your agent's documentation for the
exact location. Common examples:

| Agent | Project-level location |
|---|---|
| Claude Code | `.claude/skills/<skill-name>/` |
| GitHub Copilot | `.github/skills/<skill-name>/` |
| Generic / other agents | `.agents/skills/<skill-name>/` |

Copy only the `skills/<skill-name>/` folder.

### Install with git

This needs only `git`, with no third-party installer. Pin a release tag
(`<skill-name>/vX.Y.Z`, listed in [CHANGELOG.md](CHANGELOG.md)) so you get a
reviewed version instead of the latest `main`.

```bash
SKILL=create-prd
VERSION=v1.0.0
TARGET=.claude/skills   # change to your agent's skills directory (see table above)

TMP_DIR="$(mktemp -d)"
git -c advice.detachedHead=false clone --depth 1 --branch "$SKILL/$VERSION" https://github.com/tghcastro/agent-skills "$TMP_DIR"
mkdir -p "$TARGET"
cp -R "$TMP_DIR/skills/$SKILL" "$TARGET/"
rm -rf "$TMP_DIR"
```

⚠️ Skills give instructions to an AI agent, so read the skill's `SKILL.md` before
installing it. `create-prd` contains only Markdown, with no scripts or
executable code.

## Usage example

```text
Create a PRD for a feature that lets users export their monthly expenses as CSV.
```

```text
Create a test plan for the user registration feature based on this requirements document.
```

The agent will ask a few rounds of questions, confirm a summary with you, and
then write the document in the same language you used.

## Repository Structure

```text
skills/<skill-name>/   # installable skill (SKILL.md, assets/, references/)
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[Apache-2.0](LICENSE). See [NOTICE](NOTICE) for attributions.
