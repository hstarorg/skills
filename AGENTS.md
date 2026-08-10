# Repository Guidelines

## Scope

- Treat `skills/` as the canonical source for reusable skills.
- Keep each `skills/<skill-name>/` independently installable.
- Store black-box evaluation cases in the matching `evals/<skill-name>/` directory.
- Keep repository maintenance concerns outside individual skill directories.

## Skill structure

- Name skill directories with lowercase letters, digits, and single hyphens only.
- Require `SKILL.md`; its frontmatter must contain `name` and `description`, and `name` must match the directory.
- Add `agents/openai.yaml`, `scripts/`, `references/`, or `assets/` only when the skill needs them.
- Do not add README, changelog, installation guide, or repository-level test infrastructure inside a skill.
- Reference bundled resources with paths relative to the skill root.
- Do not create relative-path dependencies between skills or on repository-root files.

## Development workflow

- Use the official `skill-creator` workflow to initialize and validate skills.
- Start from concrete user requests, including a normal case, an edge case, and a case that must not trigger the skill.
- Add or update evaluation cases before changing established behavior.
- Test executable scripts with representative valid and invalid inputs.
- Reproduce the checks in `.github/workflows/quality.yml` before finishing a change.
- Avoid repository-level templates or maintenance tooling until repeated use demonstrates a concrete need.

## Safety

- Never commit credentials, authentication caches, private keys, personal data, or real customer data.
- Require explicit confirmation for external writes, messages, publishing, deletion, transactions, or other consequential actions.
- Keep dependencies minimal and pinned where practical.
- Preserve unrelated user changes in a dirty worktree.
