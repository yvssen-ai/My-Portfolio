# Claude Code plugins

This repo doubles as a Claude Code plugin marketplace. The catalogue sits at the
repo root, because that is where Claude Code looks when you point it at a git
repository; the plugins themselves live in here.

```
.claude-plugin/
└── marketplace.json              catalogue — lists every plugin below
claude-plugins/
└── frontend-design/
    ├── .claude-plugin/
    │   └── plugin.json           this plugin's manifest
    ├── LICENSE.txt               Apache 2.0
    └── skills/
        └── frontend-design/
            └── SKILL.md          the skill itself
```

## Plugins

| Plugin | What it does |
| --- | --- |
| `frontend-design` | Design guidance for building or reshaping UI — aesthetic direction, typography, and choices that don't read as templated defaults. |

## Install

Straight from GitHub, no clone needed:

```
/plugin marketplace add yvssen-ai/My-Portfolio
/plugin install frontend-design@yassen-plugins
/reload-plugins
```

Or from a local clone:

```
/plugin marketplace add .
/plugin install frontend-design@yassen-plugins
/reload-plugins
```

## Using it

Claude picks the skill up on its own when a task is about visual design. To
call it directly, use the namespaced form — plugin name, then skill name:

```
/frontend-design:frontend-design
```

## Changing it

Bump `version` in `claude-plugins/frontend-design/.claude-plugin/plugin.json` on
every release; users only receive updates when that field changes. Validate
before publishing:

```
claude plugin validate . --strict
claude plugin validate ./claude-plugins/frontend-design --strict
```
