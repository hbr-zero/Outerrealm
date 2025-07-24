---
title: "Ranger File Manager Cheat Sheet"
date: 2025-07-23
draft: false
tags: ["ranger", "terminal", "file manager", "cli", "linux"]
categories: ["cheatsheets", "linux"]
description: "A quick-reference cheat sheet for using Ranger, the terminal-based file manager."
---

# 🗂️ Ranger File Manager Cheat Sheet

## 🧭 Navigation
| Key | Action |
|-----|--------|
| `j` | Move down |
| `k` | Move up |
| `h` | Go to parent directory |
| `l` | Enter directory or open file |
| `gg` / `G` | Top / bottom of list |
| `H` / `L` | Back / Forward in history |
| `~` | Go to home directory |
| `/` | Search |
| `n` / `N` | Next / previous search result |
| `Ctrl+f` / `Ctrl+b` | Page down / up |

## 📁 File Operations
| Key | Action |
|-----|--------|
| `yy` | Yank (copy) selected file |
| `dd` | Cut (delete into buffer) |
| `p`  | Paste from buffer |
| `pp` | Paste into current directory |
| `x`  | Swap marked file with top of buffer |
| `r`  | Rename file |
| `cw` | Change name (like rename) |
| `a`  | Create new file |
| `A`  | Create new directory |
| `D`  | Delete file/directory |
| `:bulkrename` | Batch rename with `$EDITOR` |

## 🔖 Bookmarks
| Key | Action |
|-----|--------|
| `m<key>` | Set bookmark (e.g. `ma`) |
| `' <key>` | Go to bookmark (e.g. `'a`) |
| `` ` `` | Jump to the last directory |

## 🔍 Preview and Sorting
| Key | Action |
|-----|--------|
| `zi` | Toggle file preview |
| `zh` | Toggle hidden files |
| `or` | Reverse sort |
| `os` | Sort by size |
| `ot` | Sort by modified time |
| `on` | Sort by name (default) |

## ⚙️ Commands and Shell
| Key / Command | Action |
|---------------|--------|
| `:` | Enter command mode |
| `!` | Run shell command |
| `:open_with` | Open file with specific application |
| `:cd <path>` | Change directory |
| `:set <option>` | Change configuration |
| `:help` | View Ranger documentation |

## 🛠️ Custom Keybind Example

To open PDFs with Zathura:

```bash
echo "map zp shell zathura %f" >> ~/.config/ranger/rc.conf
```

## 🧩 Other Useful Features
| Key | Action |
|-----|--------|
| `space` | Mark/unmark files |
| `v` | Toggle visual mode |
| `Tab` | Toggle preview window focus |
| `u` | Undo last operation |
| `Ctrl+u` | Toggle user interface elements |
| `?` | Show keybindings help |
