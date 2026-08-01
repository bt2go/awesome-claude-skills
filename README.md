# Awesome Claude Skills [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of Claude Code skills, plugins, marketplaces and the docs that actually matter, for people building agent workflows instead of collecting bookmarks.

## Why this exists

Skills are a small format with a large surface: a folder, a `SKILL.md`, a description line that decides whether the thing ever loads. The useful references are scattered across docs pages, changelogs and half finished repos, and most "awesome" lists in this space are padded with links that resolve to 404. Every entry below is one line, and nothing is listed unless it is confirmed to exist.

## Contents

- [Official docs](#official-docs)
- [Skill collections](#skill-collections)
- [Single purpose skills](#single-purpose-skills)
- [Plugin marketplaces](#plugin-marketplaces)
- [MCP servers worth pairing](#mcp-servers-worth-pairing)
- [Statuslines and hooks](#statuslines-and-hooks)
- [Writing your own skill](#writing-your-own-skill)
- [Talks and posts](#talks-and-posts)

## Official docs

- [Claude Code docs](https://docs.claude.com/en/docs/claude-code/overview) - the canonical reference, start here before any blog post
- [Agent Skills](https://docs.claude.com/en/docs/claude-code/skills) - the SKILL.md format, discovery rules and directory layout
- [Plugins](https://docs.claude.com/en/docs/claude-code/plugins) - how plugins bundle skills, commands, agents and hooks
- [Plugin marketplaces](https://docs.claude.com/en/docs/claude-code/plugin-marketplaces) - hosting your own marketplace from a git repo
- [Hooks reference](https://docs.claude.com/en/docs/claude-code/hooks) - the event names and payloads, which are easy to get wrong from memory
- [Settings](https://docs.claude.com/en/docs/claude-code/settings) - permissions, environment variables and precedence order
- [Model Context Protocol](https://modelcontextprotocol.io) - the spec behind MCP servers
- [anthropics/claude-code](https://github.com/anthropics/claude-code) - the CLI itself, plus its issue tracker and changelog

## Skill collections

- [claude-skills](https://github.com/botaoishere/claude-skills) - 12 small skills for commits, reviews, tests, docs and audits, installable as one plugin
- Curated multi skill packs from the community - PRs welcome, link only packs you have installed and run

## Single purpose skills

- [commit-sage](https://github.com/botaoishere/commit-sage) - conventional commit messages from the staged diff
- Skills that do exactly one job and do it well - PRs welcome, one line each, no forks of the same idea

## Plugin marketplaces

- [Claude Code plugin marketplace docs](https://docs.claude.com/en/docs/claude-code/plugin-marketplaces) - the `.claude-plugin/marketplace.json` schema
- Public community marketplaces - PRs welcome, entries must resolve and install cleanly with `/plugin marketplace add`

## MCP servers worth pairing

- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) - the reference server collection, including filesystem, git, fetch and memory
- [MCP server quickstart](https://modelcontextprotocol.io/quickstart/server) - build your own server in Python or TypeScript
- [MCP inspector](https://github.com/modelcontextprotocol/inspector) - poke at a server's tools and resources before wiring it into an agent

## Statuslines and hooks

- [Statusline reference](https://docs.claude.com/en/docs/claude-code/statusline) - the JSON your script receives on stdin, which is the part people miss
- [Hooks guide](https://docs.claude.com/en/docs/claude-code/hooks-guide) - worked examples of PreToolUse and PostToolUse
- Community statusline scripts - PRs welcome, include a screenshot and the runtime it needs

## Writing your own skill

A skill is a directory containing one file. This is the entire minimum:

```markdown
---
name: dockerfile-review
description: Use when the user writes or edits a Dockerfile and wants it checked.
---

# Dockerfile review

## Procedure
1. Read the Dockerfile and note the base image and its tag.
2. Flag any unpinned tag, any secret baked into a layer, and any root user at runtime.
3. Check layer ordering: dependency install before source copy, so the cache survives edits.
4. Report the image size cost of each finding.

## Output format
One line per finding: `line N - problem - fix`.
```

Drop that at `.claude/skills/dockerfile-review/SKILL.md` and it is live in the next session.

Two rules decide whether a skill is ever useful: the description must start with "Use when" and name the trigger, and the body must be a procedure rather than a personality.

## Talks and posts

- [Anthropic engineering blog](https://www.anthropic.com/engineering) - the agent design posts, including context and tool use practice
- [Claude Code release notes](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md) - the fastest way to learn what the CLI gained this month
- Conference talks and long form write ups on skill design - PRs welcome

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). One entry per PR, one line per entry, no fabricated links.

## License

[CC0 1.0](LICENSE). To the extent possible under law, the maintainer has waived all copyright to this list.
