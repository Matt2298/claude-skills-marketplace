# Claude Skills Marketplace

Personal [Claude Code plugins](https://docs.anthropic.com/en/docs/claude-code/plugins) marketplace.

## Getting started

### 1. Add the marketplace

```bash
/plugin marketplace add Matt2298/claude-skills-marketplace
```

### 2. Install a plugin

```bash
/plugin install <plugin-name>@matt-marketplace
```

---

## Plugins

| Plugin                                | Description                                       |
| ------------------------------------- | ------------------------------------------------- |
| **[obsidian-tasks](#obsidian-tasks)** | Skills for working with Obsidian vault task lists |

---

### obsidian-tasks

Skills for interacting with your Obsidian vault via the [Obsidian Tasks plugin](https://github.com/obsidian-tasks-group/obsidian-tasks).

| Skill          | Description                                                                                                               |
| -------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `do-next-task` | Read today's daily note, pick the highest priority incomplete task, attempt to complete it, mark it done, and report back |

```bash
/plugin install obsidian-tasks@matt-marketplace
```

---

## Contributing

### Repository structure

```
claude-skills-marketplace/
├── .claude-plugin/
│   └── marketplace.json     # Marketplace manifest (lists all plugins)
├── <plugin-name>/
│   ├── plugin.json          # Plugin metadata and version
│   ├── README.md            # Plugin documentation
│   └── skills/
│       └── <skill-name>/
│           └── skill.md     # Skill instructions for Claude
└── README.md
```

### Adding a new plugin

1. Create a top-level directory for the plugin
2. Add a `plugin.json` manifest (see `example-plugin/plugin.json`)
3. Add skills under `skills/<skill-name>/skill.md`
4. Register the plugin in `.claude-plugin/marketplace.json`
5. Document it in this README

### Adding a skill to an existing plugin

1. Create a directory under the plugin's `skills/` folder
2. Add a `skill.md` following the structure of existing skills
3. Bump the `version` in the plugin's `plugin.json` and `.claude-plugin/marketplace.json`

### Skill format

```markdown
---
name: plugin-name:skill-name
description: One-line description of when Claude should use this skill
---

# Instructions for Claude go here
```

---

## Local development

```bash
# Add the marketplace from a local clone
/plugin marketplace add ./claude-skills-marketplace

# Install a plugin
/plugin install <plugin-name>@matt-marketplace

# After making changes, reinstall to pick them up
/plugin uninstall <plugin-name>
/plugin install <plugin-name>@matt-marketplace
```
