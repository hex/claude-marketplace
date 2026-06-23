# hex-plugins

A marketplace of Claude Code plugins by hex.

## Installation

Add this marketplace to Claude Code:

```
/plugin marketplace add hex/claude-marketplace
```

Then browse and install plugins with:

```
/plugin install
```

## Available Plugins

| Plugin | Description |
|--------|-------------|
| [claude-council](https://github.com/hex/claude-council) | Consult multiple AI coding agents (Gemini, OpenAI, Grok) for diverse perspectives |
| [claude-image-generation](https://github.com/hex/claude-image-generation) | Generate and edit images using Google Gemini and OpenAI GPT Image APIs |
| [claude-guard](https://github.com/hex/claude-guard) | Safety guardian that prevents destructive commands and blocks credential exposure |
| [claude-tmux](https://github.com/hex/claude-tmux) | Connect to remote hosts via SSH in tmux panes with saved host management |
| [claude-taskmaster](https://github.com/hex/claude-taskmaster) | Completion guard that prevents premature stopping with TASKMASTER_DONE signal |
| [claude-crawl](https://github.com/hex/claude-crawl) | Web search, fetch, and crawl via Jina AI, Cloudflare Browser Rendering, and Firecrawl |
| [claude-release](https://github.com/hex/claude-release) | Project-agnostic /release slash command. Drives version bump, tests, docs review, release-notes draft, approval gate, commit/push, and GitHub release |

## Troubleshooting

### Install fails with `git@github.com: Permission denied (publickey)`

If `/plugin install` fails while cloning, with an SSH error like:

```
Failed to clone repository: ... git@github.com: Permission denied (publickey).
```

these plugins are published over HTTPS, so an SSH error means your git is
rewriting the HTTPS URL to SSH. Check for an `insteadOf` rule:

```
git config --get-regexp 'url\..*\.insteadof'
```

If it prints something like `url.git@github.com:.insteadof https://github.com/`,
either remove it:

```
git config --global --unset url.git@github.com:.insteadof
```

or make sure SSH access to GitHub works (`ssh -T git@github.com` succeeds, with
your key loaded in `ssh-agent`).

## License

MIT
