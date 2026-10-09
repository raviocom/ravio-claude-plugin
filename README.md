# Ravio Claude Plugin

Ravio's compensation know-how as Claude skills. The skills drive the tools of
the Ravio connector (`https://app.ravio.com/mcp`); they hold no data of their
own.

## Install

- **claude.ai or the desktop app:** Customize → Plugins → Add marketplace →
  `raviocom/claude-plugins`, then add the `ravio` plugin. Connect the Ravio
  connector from the plugin's Connectors tab.
- **Claude Code:** `/plugin marketplace add raviocom/claude-plugins`, then
  `/plugin install ravio@ravio`.

## Commands and skills

| Command                                                | Skill                            | Writes           |
| ------------------------------------------------------ | -------------------------------- | ---------------- |
| `/ravio:ravio-mapping-disclaimer`                      | `ravio-mapping-disclaimer`       | no               |

Claude also picks the right skill on its own when a request matches its
description. Each `SKILL.md` lists the flows it supports and the tools each one
calls.
