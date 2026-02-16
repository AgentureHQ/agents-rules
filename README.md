# agent-conf

A tools to manage agents configuration.


**What problem does it solve?**

One set of agent rules, compiled to every tool's format (`CLAUDE.md`, `.cursor/rules/`, `AGENTS.md`). Without it, rules duplicate, drift, and lose consistency across repos, tools, and teams.

**Installation**:
```bash
uv tool install git+https://github.com/vkroz/agent-conf
```

**Core workflows**:
- **Init**: Bootstrap the `agent-conf/` directory structure in a new repo
- **Generate**: Transform vendor-neutral canonical rulesets (YAML + markdown in `agent-conf/`) into tool-specific outputs (`.agent-conf/` → `CLAUDE.md`, `.cursor/rules/`, etc.)
- **Sync**: Pull shared agent-conf from remote git repos (a public general-purpose agent-conf repo, plus org-private ones)
- **Hierarchical inheritance**: Resolve agent-conf across global → org → project → repo → user levels, controlled via `agent-conf.yaml` (specifying target agents, `nested_depth`, etc.)

**Additional context**

- The tool is rooted in the concept of a **"Agent Configuration"** — a vendor-neutral canonical format that compiles to multiple targets, analogous to how `rustc`/`tsc` compile source to different outputs. This compilation model is what distinguishes it from simpler sync tools like `rulesync`.
- A key unsolved friction: developers naturally edit tool-specific files (like `CLAUDE.md`) directly during coding, and those changes need to propagate **back** to the canonical agent configurations — a reverse-sync problem.
- The public repo would host general-purpose, community-contributed agent configurations, while orgs maintain private agent configurations.


## Contributing

Contributions are welcome.


---

Maintained by the Agenture team.
