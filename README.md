# copilot-instructions

Working copy for Jan - April 2026
For article originally published in [Built-in](https://jackreichert.com/2026/04/22/dont-let-ai-make-you-lazy/) linked from blogpost.

The remainder of this repo is best practices I develop over time.
See [AGENTS.md](AGENTS.md) for more. Note, the code quality instructions have been moved into their own repo [code-quality-agents](https://github.com/jackreichert/code-quality-agents).
 with multiple skills.

## Shared agent instructions

[AGENTS.md](AGENTS.md) is the shared instruction template for installed AI coding tools. [scripts/link-agents](scripts/link-agents) renders its `{{USER_NAME}}` tokens using a per-user config, then links the result into the global locations used by Grok, Claude Code, Codex, and Cursor. The name-neutral [config/link-agents.conf](config/link-agents.conf) documents the config format. The script can also create project-level links for GitHub Copilot and other agents.

### Install

`link-agents` supports macOS and Linux with Bash 3.2 or newer. It uses Unix symbolic links and does not support native Windows shells; use it inside WSL on Windows.

Run the installer from the repository root:

```bash
./scripts/install
```

The installer prompts for your name, saves it in `~/.config/link-agents/config`, installs the template and command, and creates the global links. Changed template and config files are backed up with a timestamp before replacement. For unattended installation, provide the name through the environment:

```bash
AGENTS_USER_NAME="Alex" ./scripts/install
```

The generated config is parsed as data, not executed as a shell script. It may contain comments and one `AGENTS_USER_NAME` assignment.

Ensure `~/.local/bin` is on your `PATH`, then preview and create the global links:

```bash
link-agents --dry-run
link-agents
link-agents --status
```

Existing regular files are skipped by default. Use `--force` to replace them; each replaced file is first backed up with a timestamped `.bak.*` suffix.

The rendered file is written to `~/.local/share/link-agents/AGENTS.md`. Edit the template or config rather than this generated file, then rerun `link-agents`.

### Usage

Link the instructions into a project:

```bash
link-agents --project ~/path/to/repo
```

This creates links for `AGENTS.md`, `CLAUDE.md`, and `.github/copilot-instructions.md` in that project.

Use a source other than `~/AGENTS.md` with either option:

```bash
link-agents --source /path/to/AGENTS.md
AGENTS_SOURCE=/path/to/AGENTS.md link-agents
```

Override the configured name for one run with a flag or environment variable. Precedence is `--name`, `AGENTS_USER_NAME`, then the config file.

```bash
link-agents --name Alex
AGENTS_USER_NAME=Alex link-agents
```

Use a different config or rendered output location with `--config` and `--output`, or with `LINK_AGENTS_CONFIG` and `AGENTS_OUTPUT`.

Create a starter `~/AGENTS.md` when no source exists:

```bash
link-agents --init
```

Run `link-agents --help` for the complete command summary.
