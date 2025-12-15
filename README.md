# 🐟 My Fish Shell Setup — Developer + Cybersecurity Edition

> A complete Fish shell configuration focused on **aesthetics**, **productivity**, and **developer functionality**.  
> Optimized for Ubuntu users who want a clean terminal experience and strong command-line workflow.

---

## ✨ Overview

This setup turns Fish into a powerful and elegant shell environment.  
It balances **appearance**, **speed**, and **functionality** — ideal for developers, ethical hackers, and system engineers.

**Features:**
- ⚡ Fast, lightweight, and responsive prompt (powered by Tide)
- 🎨 Beautiful theme and syntax highlighting
- 🧠 Auto-suggestions, directory shortcuts, and fuzzy finder integration
- 💻 Developer-ready environment (Neovim, Git, Node.js support)
- 💬 Custom greeting and optional system summary (via `neofetch`)

---

## 🧩 Prerequisites

Make sure you have:
```bash
sudo apt update
sudo apt install fish curl git -y
```

## Step 1: Set Fish as Your Default Shell
```bash
echo /usr/bin/fish | sudo tee -a /etc/shells
chsh -s /usr/bin/fish
```
---
## Step 2: Install Fisher (Plugin Manager)
```bash
curl -sL https://git.io/fisher | source && fisher install jorgebucaran/fisher
```
---
## Step 3: Install Essential Plugins
```bash
fisher install IlanCosman/tide@v6       # modern prompt
fisher install jethrokuan/z             # quick directory navigation
fisher install jorgebucaran/fish-nvm    # Node.js version manager
fisher install franciscolourenco/done   # desktop notifications for long cmds
fisher install PatrickF1/fzf.fish       # fuzzy finder integration
```
---
## Step 4: Configure Tide
```
tide configure
```
- Recommended choices:
  - Style: Lean
  - Prompt separator: Slanted
  - Icons: Yes
  - Display: Git info, current dir, jobs
- Can re-run this anytime with:
```bash
tide configure
```
---
## Step 5: Fish Configuration
- Edit your Fish config file:
```bash
nano ~/.config/fish/config.fish
```
- Add this content:
```bash
# ===========================
#  Appearance & Functionality
# ===========================

# Greeting
function fish_greeting
    clear
    set_color cyan
    echo "Welcome back, nivoric 🧠 — "(date)
    set_color normal
end

# Syntax highlighting
set -g fish_autosuggestion_enabled 1
set -g fish_color_autosuggestion brblack
set -g fish_color_command green
set -g fish_color_param white
set -g fish_color_error red
set -g fish_color_valid_path --underline

# Vi keybindings
fish_vi_key_bindings

# Environment
set -x EDITOR nvim
set -x VISUAL nvim

# Aliases
alias ll="ls -alF"
alias la="ls -A"
alias l="ls -CF"
alias gs="git status"
alias gc="git commit"
alias gp="git push"
alias gl="git pull"

# FZF integration
if type -q fzf
    set -x FZF_DEFAULT_OPTS '--height 40% --layout=reverse --border'
end
```
---
## Step 6 (Optional): Noefetch greeting
- Install neofetch on your system, if you don't have:
```bash
sudo apt install neofetch -y
```
- Then modify your `fish_greeting`:
```bash
function fish_greeting
    clear
    neofetch
    echo (set_color green)"Welcome back, nivoric 🧠 - Ready to build and hack"
end
```
---
## Step 7: Verify
- Restart your terminal - you should see:
  - A clean prompt with Tide
  - Autosuggestions as you type
  - FZF fuzzy search
  - Beautiful syntax colors
  - A friendly greeting
---
## License
MIT License © 2025 nivoric
