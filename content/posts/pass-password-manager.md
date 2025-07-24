---
title: "Pass: The Standard Unix Password Manager"
date: 2025-07-23
draft: false
tags: ["security", "linux", "password manager", "gpg"]
categories: ["security", "cli tools"]
---

## Introduction

In a world dominated by complex password requirements and increasing cyber threats, managing credentials securely and simply is critical. Enter **Pass**, the standard Unix password manager. It’s lightweight, command-line-driven, and relies on tried-and-true tools: **GPG** for encryption and **Git** for version control.

Pass adheres to the Unix philosophy: do one thing well. It stores each password in its own GPG-encrypted file, making it both secure and manageable with familiar tools.

---

## Installation

To get started, install Pass and GPG:

```bash
# Debian/Ubuntu
sudo apt install pass gnupg

# Fedora
sudo dnf install pass gnupg

# Arch Linux
sudo pacman -S pass gnupg

# macOS (Homebrew)
brew install pass gpg
```

---

## Initial Setup

Before using Pass, ensure you have a GPG key:

```bash
gpg --full-generate-key
```

Then initialize Pass with your GPG key ID or email:

```bash
pass init "Your Name <you@example.com>"
```

---

## Basic Usage

### Add a Password

```bash
pass insert email/gmail
```

It will prompt you to type and confirm the password. You can also pipe input:

```bash
echo "MyS3cretP@ss" | pass insert email/gmail
```

### Retrieve a Password

```bash
pass email/gmail
```

### Copy a Password to Clipboard (auto-clears after 45s)

```bash
pass -c email/gmail
```

### Remove a Password

```bash
pass rm email/gmail
```

### List Stored Passwords

```bash
pass ls
```

---

## Advanced Usage

### Organize into Folders

```bash
pass insert work/github
pass insert personal/bank
```

This keeps things tidy using a tree-like structure.

### Sync with Git

Initialize a Git repo to keep your password store versioned and backed up.

```bash
cd ~/.password-store
git init
git remote add origin git@yourserver.com:password-store.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

### Use Multiple GPG Keys

You can encrypt the store for multiple recipients:

```bash
pass init "user1@example.com" "user2@example.com"
```

### Automatically Generate Passwords

```bash
pass generate social/twitter 20
```

This generates a 20-character random password and saves it.

### Edit Encrypted Passwords

```bash
pass edit personal/bank
```

Opens the file in `$EDITOR` for advanced entries like username, URL, or notes.

### Search Passwords

```bash
pass grep bank
```

Find entries containing the word "bank".

---

## Pros and Cons

### ✅ Pros

- **Simple & Unix-friendly**: Pure CLI, scriptable, and integrates with other Unix tools.
- **Secure**: Uses GPG for encryption.
- **Portable**: Stores plain files — easy to move, sync, and backup.
- **Version Controlled**: Works seamlessly with Git.
- **Flexible**: Supports multiple identities, folders, and password templates.

### ❌ Cons

- **Command-line only**: May intimidate users unfamiliar with CLI.
- **GPG complexity**: Key management can be a hurdle.
- **No built-in password sharing**: Requires manual Git or sync setup.
- **No browser integration by default**: Requires third-party extensions or scripts.

---

## Final Thoughts

If you’re comfortable with the terminal and value simplicity, control, and security, **Pass** is a rock-solid password manager. It avoids the bloat of modern GUI tools while giving you full transparency over your credentials. With Git and GPG, you get secure, auditable, and versioned password storage — the Unix way.

Happy scripting — and stay secure!
