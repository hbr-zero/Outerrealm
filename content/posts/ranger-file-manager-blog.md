---
title: "Ranger: A Terminal-Based File Manager You’ll Love"
date: 2025-07-23
draft: false
tags: ["terminal", "file manager", "linux", "cli", "productivity"]
categories: ["tools", "linux"]
description: "Explore the features, usage, and customization of Ranger, a powerful terminal-based file manager for Linux power users."
---

![Ranger File Manager](https://raw.githubusercontent.com/ranger/ranger/master/screenshots/screenshot1.png)

## What Is Ranger?

[Ranger](https://github.com/ranger/ranger) is a terminal-based file manager with a minimalistic and efficient interface. It provides a **vi-like keybinding** system, multi-pane directory views, and customizable behavior, making it a favorite among Linux power users and terminal lovers.

## Why Use Ranger?

- 🧭 **Navigation Made Easy**: Use familiar Vim-style keys to move between files.
- 🖼️ **Previews**: See file previews right in the terminal, including text and images (with `w3m` or `ueberzug`).
- 🛠️ **Customizable**: Fully scriptable with Python and extensive config options.
- ⚡ **Lightweight**: No GUI overhead — just fast and responsive terminal UI.

## Installation

### On Debian/Ubuntu:

```bash
sudo apt update
sudo apt install ranger
```

### On Arch Linux:

```bash
sudo pacman -S ranger
```

### On macOS (via Homebrew):

```bash
brew install ranger
```

### From Source:

```bash
git clone https://github.com/ranger/ranger.git
cd ranger
sudo make install
```

## Getting Started

To start Ranger:

```bash
ranger
```

Basic keybindings:

- `h` / `l`: Navigate left/right in the directory hierarchy
- `j` / `k`: Move down/up
- `gg` / `G`: Go to top/bottom
- `:q`: Quit Ranger
- `yy` / `dd`: Yank/cut file
- `p` / `P`: Paste
- `:shell <command>`: Run shell commands

## Preview Support

Install `w3m`, `ueberzug`, or `catimg` for image previews.

Example (Debian):

```bash
sudo apt install w3m
```

To enable preview support:

```bash
ranger --copy-config=scope
```

Then edit `~/.config/ranger/scope.sh` to configure preview behavior.

## Configuration

Generate default configs:

```bash
ranger --copy-config=all
```

You’ll get:

- `rc.conf` – keybindings and general behavior
- `scope.sh` – file preview rules
- `commands.py` – custom commands in Python

Example: open PDFs with `zathura`:

```bash
echo 'map zp shell zathura %f' >> ~/.config/ranger/rc.conf
```

## Tips and Tricks

- Press `z` then `i` to toggle file previews.
- Press `:bulkrename` to open selected files in `$EDITOR` for batch renaming.
- Use bookmarks: press `m` + key to mark a directory, `'` + key to jump.

## Integration with Other Tools

- Use Ranger as the file picker in `vim` or `neovim` by mapping it to a key.
- Integrate with `lf` (another file manager), `tmux`, or even your window manager.

## Conclusion

Ranger offers a powerful, keyboard-driven file management experience from your terminal. Once you get used to it, you may never want to go back to GUI file managers.

> ✨ Pro tip: Combine Ranger with `fd`, `ripgrep`, or `fzf` for a blazing-fast workflow.

---

**Resources:**

- 📘 [Ranger GitHub](https://github.com/ranger/ranger)
- 📄 [Man Page](https://linux.die.net/man/1/ranger)
- 🎥 [Demo Video](https://asciinema.org/a/373821)
