# HalloGlitch — Distribution & User Guide

**Product:** HalloGlitch  
**Category:** Universal Agent  
**Tagline:** An Agent Without Boundaries  
**Official Repository:** `https://github.com/ramiglitch/HalloGlitch`  
**License:** MIT License  

---

## 1. Overview & System Requirements

HalloGlitch is an independent Universal Agent built on the open-source Hermes Agent engine. It provides autonomous tool calling, multi-session memory, Model Context Protocol (MCP) server integration, a terminal REPL, an Ink terminal UI (TUI), and a native Electron desktop interface.

### Supported Platforms
- **Windows**: Windows 10 / 11 (x64 and ARM64).
- **macOS**: macOS 13.0+ (Apple Silicon).
- **Linux**: Ubuntu 22.04+, Debian 12+, Fedora, Arch.

### Prerequisites (For Source & CLI Execution)
- **Python**: `>= 3.11, < 3.15` (Python 3.14 recommended).
- **Package Manager**: `uv` (`https://astral.sh/uv`).
- **Node.js & pnpm** (Optional for frontend development): Node `>= 26`, pnpm `12.15.0`.

---

## 2. Installation Guide

### Option A: Portable Standalone CLI (Recommended for Terminal Users)
```powershell
# Clone the repository
git clone https://github.com/ramiglitch/HalloGlitch.git
cd HalloGlitch
git checkout custom

# Synchronize runtime dependencies with uv
uv sync

# Verify installation
uv run halloglitch --version
```

### Option B: Windows Desktop Application Installer
1. Download `HalloGlitch-Setup-<version>.exe` from the latest [GitHub Release](https://github.com/ramiglitch/HalloGlitch/releases).
2. Launch the installer.
3. Follow the on-screen prompts to install HalloGlitch into `%LOCALAPPDATA%\Programs\HalloGlitch`.

#### Windows SmartScreen Security Warning (Unsigned Builds)
Because release binaries are currently built without a costly commercial Extended Validation (EV) certificate:
1. Windows Defender SmartScreen will display:  
   *"Windows protected your PC — Microsoft Defender SmartScreen prevented an unrecognized app from starting."*
2. Click **More info**.
3. Click **Run anyway**.
4. The verified SHA-256 hash of the binary can be cross-checked against `SHA256SUMS.txt` published on GitHub Releases.

---

## 3. First-Time Setup & Provider Configuration

HalloGlitch connects to your choice of model provider. No proprietary lock-in.

### 1. Interactive Setup Wizard
Run the interactive wizard in your terminal:
```bash
uv run halloglitch setup
```
Select your primary model provider:
- **OpenRouter** (Access Claude 3.5 Sonnet, DeepSeek V3/R1, Llama 3.3, GPT-4o).
- **Anthropic Native** (Direct API access).
- **Nous Portal** (Nous Research serverless endpoints).
- **OpenAI / Codex** (GPT-4o, o1, o3-mini).
- **Custom / Local** (Ollama, vLLM, llama.cpp, LocalAI).

### 2. Manual CLI Configuration
Alternatively, configure keys directly via CLI or `.env`:
```bash
# Store API key in ~/.hermes/.env (or %LOCALAPPDATA%\hermes\.env)
uv run halloglitch config set model.provider openrouter
uv run halloglitch config set model.default anthropic/claude-3.5-sonnet

# Set API key in environment or ~/.hermes/.env:
# OPENROUTER_API_KEY=sk-or-v1-xxxxxxxxxxxx
```

---

## 4. Running HalloGlitch

### Interactive Terminal Chat
```bash
# Launch default interactive REPL
uv run halloglitch chat

# Single-query execution (answer and exit)
uv run halloglitch chat -q "Audit git changes in this directory"
```

### Modern Terminal UI (TUI)
```bash
uv run halloglitch --tui
```

### Web UI Dashboard
```bash
uv run halloglitch dashboard --port 9119
# Opens browser at http://127.0.0.1:9119 with management dashboard
```

---

## 5. Updating HalloGlitch

### CLI & Source Updates
```bash
# Check for updates and pull latest commits
uv run halloglitch update
```
The updater automatically inspects upstream commits, fast-forwards clean trees, and notifies you of changes.

### Desktop App Updates
The desktop application checks for releases on `https://github.com/ramiglitch/HalloGlitch/releases`. When an update is ready, an in-app notification prompts to apply the update and relaunch.

---

## 6. Uninstallation

### Clean CLI Uninstallation
```bash
uv run halloglitch uninstall
```
To purge all user data, sessions, and memory:
```bash
uv run halloglitch uninstall --data
```

### Desktop Application Uninstallation
- On Windows: Navigate to **Windows Settings &rarr; Installed Apps &rarr; HalloGlitch &rarr; Uninstall**.
- User configuration in `%LOCALAPPDATA%\hermes` is retained by default unless explicitly deleted.

---

## 7. Known Limitations

1. **Windows SmartScreen**: Unsigned release executables trigger standard Windows unknown publisher warnings until code-signing certificates are registered.
2. **Native Modules (node-pty)**: Desktop compilation from source on Windows requires Microsoft Visual C++ Build Tools (`node-gyp`). Prebuilt binaries ship with standard release installers.
3. **Internal Storage Paths**: Configuration and session state persist in `~/.hermes/` (`%LOCALAPPDATA%\hermes` on Windows) to maintain engine stability and upstream rebase compatibility.

---

## 8. Upstream Attribution & License

HalloGlitch is an independent downstream product identity built on the foundational open-source architecture of [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent).

Licensed under the **MIT License**:
```
Copyright (c) 2024-2026 Nous Research
Copyright (c) 2026 HalloGlitch Contributors
```
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction.
