# Skills

Reusable agent skills for engineering workflows.

## Repository structure

```text
.
├── .github/workflows/   # Quality checks and releases
├── skills/              # Installable skills; one directory per skill
├── evals/               # Black-box evaluations matching skill names
├── AGENTS.md             # Repository maintenance rules for agents
└── LICENSE
```

`skills/` and `evals/` intentionally contain no examples yet.

## Skill contract

Each `skills/<skill-name>/` directory is independently installable and contains:

- `SKILL.md` — required instructions with `name` and `description` frontmatter.
- `agents/openai.yaml` — optional OpenAI interface metadata.
- `scripts/` — optional deterministic executables.
- `references/` — optional documentation loaded on demand.
- `assets/` — optional templates and static resources.

Skill names use lowercase kebab-case and must match their directory names. A skill must not depend on files outside its own directory.

## Add a skill

Use the official `$skill-creator` workflow to initialize and validate a new skill. Create only the resource directories the skill actually needs, then add matching evaluation cases under `evals/<skill-name>/` when behavior is ready to test.

## Install a skill

Use the open Agent Skills CLI. It detects supported agents and installs each skill into the appropriate directory.

Browse the skills available in this repository:

```sh
npx skills add hstarorg/skills --list
```

Install interactively:

```sh
npx skills add hstarorg/skills
```

Install one specific skill:

```sh
npx skills add hstarorg/skills --skill <skill-name>
```

Node.js and npm are required to run `npx`. Project installation is the default; pass `--global` to make a skill available across projects, or `--agent <agent-name>` to target a specific supported agent.

## Quality and releases

- `quality.yml` checks the repository and every committed skill on pushes and pull requests.
- `release.yml` packages each skill independently for semantic-version tags such as `v1.2.3`.

## License

MIT
