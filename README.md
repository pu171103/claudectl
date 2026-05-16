# claudectl

> **Automate your Claude Code context budget with a zero-dependency configuration switcher.**

`claudectl` is an open-source, lightweight CLI utility built in Rust to safely manipulate and swap Claude Code configurations across **Local**, **Project**, and **Global** scopes.

By automating your configuration files (`.claude/settings.local.json`, `.claude/settings.json`, and `~/.claude.json`), `claudectl` allows you to rapidly toggle active skills, switch agent profiles, and apply rule sets programmatically—saving your token context budget and keeping your workflows lightweight.

## ✨ Features

* **⚡ Sub-millisecond Execution:** Built in pure Rust with zero heavy runtime dependencies.
* **🎯 Scope-Aware Merging:** Intelligently mutates settings at the exact tier you target (Local, Project, or Global) without damaging other layers.
* **📉 Context Budget Optimization:** Instantly disable heavy active skills or plugins via the command line before launching Claude Code to trim token overhead.
* **🎭 Profile Swapping:** Save combinations of plugins and environment rules into standalone templates and swap them dynamically depending on your current task (e.g., frontend debugging vs. database migrations).
* **🤖 Open Source & Free:** 100% free, MIT/Apache dual-licensed, and built completely transparently for the developer community.

## 🚀 Installation

`claudectl` is distributed as a single statically linked binary for macOS, Linux, and Windows.

### Via Package Managers

#### macOS & Linux (Homebrew)

```bash
brew tap yourusername/claudectl
brew install claudectl

```

#### Windows (Scoop)

```powershell
scoop bucket add claudectl https://github.com/yourusername/claudectl-scoop.git
scoop install claudectl

```

#### Universal (Cargo)

```bash
cargo install claudectl

```

## 🛠️ Usage Examples

### Toggle Active Skills & Plugins

Quickly disable an expensive database skill in your project folder when you switch over to styling layout tasks:

```bash
claudectl skill disable project:sql-agent

```

### Apply Scoped Rules

Inject a specialized `.md` ruleset file directly into your local workspace configuration:

```bash
claudectl rules apply local:.github/workflows/frontend-rules.md

```

### Swap Complete Environment Profiles

Swap your entire global layout for a lean, minimal-token profile:

```bash
claudectl profile switch global:lean-mode

```

### Inspect Your Config Cascade

View a flattened breakdown of active settings showing exactly which file layer (Local, Project, or Global) a rule originates from:

```bash
claudectl status

```

## 🏗️ Technical Details

`claudectl` operates entirely locally by executing atomic writes against standard Claude Code configuration paths. It relies on `serde_json` to guarantee syntax validation and preserves existing JSON whitespace structures wherever possible.

The binary is fully statically compiled against `musl` on Linux to avoid runtime dependency version mismatches.

## 🤝 Contributing

This is a community-driven open-source project! Pull requests, feature requests, and issue reports are highly encouraged. Please review the `CONTRIBUTING.md` file for details on setting up your local Rust toolchain and compiling the test suites.

## 📄 License

This project is dual-licensed under either the **MIT License** or the **Apache License (Version 2.0)**, at your option.
