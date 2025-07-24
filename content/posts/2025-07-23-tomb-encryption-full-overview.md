---
title: "Tomb: A Simple and Secure Linux Encryption Tool"
date: 2025-07-23
author: Henry Briseno
tags: ["encryption", "linux", "security", "privacy", "tomb"]
categories: ["Security", "Tools"]
description: "An overview of Tomb, a CLI-based encryption tool for GNU/Linux that provides simple, powerful, and scriptable file encryption using LUKS and GnuPG."
---

## What is Tomb?

**Tomb** is a free and open-source encryption tool for GNU/Linux that allows users to create encrypted storage containers (called *tombs*) and protect their keys with GnuPG. It’s designed to be **scriptable**, **lightweight**, and **secure**, making it ideal for privacy-focused users who prefer the terminal.

Created by [Dyne.org](https://www.dyne.org/software/tomb/), Tomb uses **LUKS (Linux Unified Key Setup)** for strong encryption and **GnuPG** for key management.

---

## Key Features

- 🔐 **Strong encryption** using LUKS and dm-crypt  
- 🔑 **GnuPG integration** for securing keys with public-key cryptography  
- 📦 **Portable containers** that can be safely backed up or moved  
- 🧪 **Scriptable CLI interface**, perfect for automation  
- 🔒 **Key and data separation** — keys can be stored offline  
- 🧹 **Self-destruct and forget options** to erase keys or wipe data  

---

## How Tomb Works

Tomb separates the *container* (the encrypted file) from the *key* (used to unlock it):

1. **Create a tomb (container)**:  
   `tomb dig secret.tomb -s 100`  
   This creates a 100MB encrypted file.

2. **Forge a key**:  
   `tomb forge secret.key`  
   Optionally protect the key with a GPG identity.

3. **Lock the tomb with the key**:  
   `tomb lock secret.tomb -k secret.key`  

4. **Open the tomb** (decrypt and mount):  
   `tomb open secret.tomb -k secret.key`  

5. **Close the tomb**:  
   `tomb close`  

You can now securely store private files inside the mounted volume.

---

## Basic to Advanced Usage Examples

### 🔰 Basic Usage

#### Create a Tomb Container
```bash
tomb dig secrets.tomb -s 100
```

#### Generate a Key
```bash
tomb forge secrets.key
```

#### Bind the Key to the Tomb
```bash
tomb lock secrets.tomb -k secrets.key
```

#### Open the Tomb
```bash
tomb open secrets.tomb -k secrets.key
```

#### Close the Tomb
```bash
tomb close
```

---

### 🛠️ Intermediate Usage

#### Use GPG Keys to Protect the Tomb Key
```bash
gpg --gen-key
tomb forge secrets.key -g your.name@domain.com
```

#### Bury an Executable or Script
```bash
tomb bury my_script.sh -k secrets.key
```

#### Auto-Open on Login
```bash
if [ -f ~/.keys/secrets.key ]; then
  tomb open ~/vaults/secrets.tomb -k ~/.keys/secrets.key
fi
```

---

### 🧙 Advanced Usage

#### Share Tomb Between Multiple GPG Users
```bash
tomb forge team.key -g alice@example.com -g bob@example.com
```

#### Forget Tomb Key from Memory
```bash
tomb forget secrets.key
```

#### Permanently Destroy a Key
```bash
tomb bury /dev/urandom -k secrets.key
```

#### List Open Tombs
```bash
tomb list
```

#### Use Custom Mount Point
```bash
tomb open secrets.tomb -k secrets.key -d /mnt/secure
```

---

## Use Cases

- 🕵️ Personal document encryption  
- 📁 Portable encrypted USB containers  
- 🛡️ Secure backups and archiving  
- 👥 Shared encrypted storage among trusted GPG identities  
- 🔐 Keeping secrets out of cloud storage systems  

---

## Pros and Cons

**Pros:**

- Simple and lightweight
- Fully open-source
- No proprietary dependencies
- Flexible and script-friendly
- Separation of concerns (data vs key)

**Cons:**

- Command-line only (no GUI)
- GnuPG usage can be complex for new users
- Requires root privileges for some operations

---

## Installation

On Debian/Ubuntu-based systems:

```bash
sudo apt install tomb
```

On Arch Linux:

```bash
yay -S tomb
```

You can also install from source via the [Tomb GitHub repository](https://github.com/dyne/Tomb).

---

## Final Thoughts

Tomb offers a clean, minimal approach to file encryption for Linux users who are comfortable with the terminal. Its separation of key and data makes it particularly suitable for advanced users and those with strict security requirements.

While it may not be beginner-friendly, Tomb shines in its simplicity, portability, and power. If you're looking for a trusted CLI encryption tool, Tomb is definitely worth exploring.

---

*Want to learn more? Visit the official Tomb website at [https://www.dyne.org/software/tomb](https://www.dyne.org/software/tomb) or check out the [Tomb GitHub repo](https://github.com/dyne/Tomb).*
