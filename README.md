# Alan's Dotfiles & Configuration Setup

This repository contains personal configuration files ("dotfiles") for my development environment, including settings for Terminal (Ghostty, Zsh), IDEs (VSCode, Cursor), and AI tools (OpenCode).

## 📂 Manifest

- **Terminal**
  - `terminal/zshrc`: Main shell configuration (`~/.zshrc`)
  - `terminal/starship.toml`: Starship prompt configuration (`~/.config/starship.toml`)
- **Ghostty** (Terminal Emulator)
  - `ghostty/config`: Ghostty preferences (`~/Library/Application Support/com.mitchellh.ghostty/config`)
- **VSCode**
  - `vscode/settings.json`: User settings
  - `vscode/keybindings.json`: Custom keybindings
  - `vscode/snippets/`: Code snippets
- **Cursor** (AI Editor)
  - `cursor/settings.json`: User settings
  - `cursor/keybindings.json`: Custom keybindings
  - `cursor/cursorrules`: Global AI behavior rules (`~/.cursorrules`)
  - `cursor/mcp.json`: Model Context Protocol settings (`~/.cursor/mcp.json`)
- **OpenCode**
  - `opencode/opencode.json`: OpenCode configuration (`~/.config/opencode/opencode.json`)

---

## 🤖 AI Agent Installation Instructions

**Prompt for Agent:** "You are tasked with installing the user's dotfiles from this repository. Follow the instructions below to safely merge these configurations into the current system."

### 1. Safety First (Backup)
Before overwriting any file, check if it exists and create a backup.
```bash
# Example backup logic
if [ -f "$DESTINATION" ]; then
  cp "$DESTINATION" "${DESTINATION}.backup.$(date +%s)"
fi
```

### 2. File Mapping (Repo -> System)
Use this mapping to copy files to their correct locations. Ensure parent directories exist.

| Component | Source File (in repo) | Destination System Path (Absolute) |
|-----------|----------------------|------------------------------------|
| **Zsh** | `terminal/zshrc` | `~/.zshrc` |
| **Starship** | `terminal/starship.toml` | `~/.config/starship.toml` |
| **Ghostty** | `ghostty/config` | `~/Library/Application Support/com.mitchellh.ghostty/config` |
| **VSCode** | `vscode/settings.json` | `~/Library/Application Support/Code/User/settings.json` |
| **VSCode** | `vscode/keybindings.json` | `~/Library/Application Support/Code/User/keybindings.json` |
| **VSCode** | `vscode/snippets/*` | `~/Library/Application Support/Code/User/snippets/` |
| **Cursor** | `cursor/settings.json` | `~/Library/Application Support/Cursor/User/settings.json` |
| **Cursor** | `cursor/keybindings.json` | `~/Library/Application Support/Cursor/User/keybindings.json` |
| **Cursor** | `cursor/cursorrules` | `~/.cursorrules` |
| **Cursor** | `cursor/mcp.json` | `~/.cursor/mcp.json` |
| **OpenCode** | `opencode/opencode.json` | `~/.config/opencode/opencode.json` |

### 3. Installation Script (Reference)
You may execute the following shell commands to perform the installation (assuming you are in the root of this repo):

```bash
# Ensure directories exist
mkdir -p ~/.config
mkdir -p "$HOME/Library/Application Support/com.mitchellh.ghostty"
mkdir -p "$HOME/Library/Application Support/Code/User/snippets"
mkdir -p "$HOME/Library/Application Support/Cursor/User"
mkdir -p ~/.cursor
mkdir -p ~/.config/opencode

# Terminal
cp terminal/zshrc ~/.zshrc
cp terminal/starship.toml ~/.config/starship.toml

# Ghostty
cp ghostty/config "$HOME/Library/Application Support/com.mitchellh.ghostty/config"

# VSCode
cp vscode/settings.json "$HOME/Library/Application Support/Code/User/settings.json"
cp vscode/keybindings.json "$HOME/Library/Application Support/Code/User/keybindings.json"
cp -R vscode/snippets/* "$HOME/Library/Application Support/Code/User/snippets/"

# Cursor
cp cursor/settings.json "$HOME/Library/Application Support/Cursor/User/settings.json"
cp cursor/keybindings.json "$HOME/Library/Application Support/Cursor/User/keybindings.json"
cp cursor/cursorrules ~/.cursorrules
cp cursor/mcp.json ~/.cursor/mcp.json

# OpenCode
cp opencode/opencode.json ~/.config/opencode/opencode.json
```

### 4. Verification
After copying, verify the installation by checking if the files exist at the destination paths and contain the expected content.
