# [Fish Shell on Windows (WSL)](#fish-shell-on-windows-wsl)

<br>

<div align="center">
	
[![](https://img.shields.io/badge/🇧🇷%20Português-clique%20aqui-009c3b?style=for-the-badge)](./README-pt.md)

</div>

### A complete setup guide — from a blank terminal to a beautiful, productive shell

> **Before you start:** Create a System Restore Point for your C:/ drive. Always do this before modifying Windows system settings.

---

## What You'll End Up With

Before

![ugly cmd](https://user-images.githubusercontent.com/66394117/167328153-b031a76a-1d4e-4005-862f-e6ff7cd2cd85.gif)

After

![final result](https://user-images.githubusercontent.com/66394117/167418650-5297e4d5-2dbc-4cb6-8732-c7611a86c2db.gif)



## Overview

**Fish** (Friendly Interactive Shell) is one of several command-line interpreters — alongside bash, zsh, and PowerShell — that sit between you and the operating system. What sets Fish apart is that autocompletion and inline suggestions work out of the box, with zero configuration.

→ [Learn more at fishshell.com](https://fishshell.com/)

Since Fish is a Unix shell, it doesn't run natively on Windows. You'll need **Windows Subsystem for Linux (WSL)** to bridge that gap — that's what this guide covers.

## [Part 1 — WSL & Ubuntu](#part-1--wsl--ubuntu)

### Step 1 · Install WSL

Open **Command Prompt** as Administrator and run:

```sh
wsl --install
```

> **Tip:** If `Ctrl+V` doesn't paste in the terminal, use the right mouse button instead.

This command will:
- Enable the **WSL** and **Virtual Machine Platform** components
- Download and install the latest **Linux kernel**
- Download and install the **Ubuntu** distribution

Once it finishes, **restart your machine**.

> If `wsl --install` shows the help menu instead of installing, WSL is already present — skip to Step 2.  
> If the automatic installation fails, follow [Microsoft's manual install guide](https://docs.microsoft.com/en-us/windows/wsl/install).

---

#### WSL 2 — Hyper-V Requirement

WSL 2 (the recommended version) requires Hyper-V / Virtualization support. Check whether it's enabled in Task Manager under the **Performance** tab.

![Task Manager Virtualization](https://github.com/user-attachments/assets/7853037c-1688-4fad-abee-0b3382aef30c)

If it shows **Disabled**, restart and enable it in your BIOS — usually found under **Advanced** or **CPU Configuration**.

> No Hyper-V? You can still install WSL 1, though WSL 2 is strongly recommended.

---

### Step 2 · Configure Ubuntu

Open **Ubuntu** from the Start Menu. If it doesn't appear, find your installed version in the [Microsoft Store](https://aka.ms/wslstore) and click **Open**.

Wait for the initial setup to finish, then create a **username** and **password** when prompted.

![Ubuntu first run](https://user-images.githubusercontent.com/66394117/167333051-7444d201-00e5-4d95-8395-56771fa941d7.png)

---

### Step 3 · Install Fish

Open **cmd** and run the command `bash` or `wsl` to access your **Linux (Ubuntu)** environment


Add the Fish repository, update your package list, and install:

```sh
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt update && sudo apt upgrade
sudo apt install fish
```

> If `apt-add-repository` returns "not found command" run `sudo apt install software-properties-common`

<br>

That's it — Fish is installed. Launch it by running `fish` in **Linux Terminal (bash or wsl)**
<br>

## [Part 2 — Terminal Appearance](#part-2--terminal-appearance)

### Step 1 · Install Windows Terminal

Ditch the default terminal. Install [**Windows Terminal**](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) from the Microsoft Store for a modern, tabbed experience.

---

### Step 2 · Install Oh My Fish

Oh My Fish (omf) is the plugin and theme manager for Fish. First, make sure Git is available:

```sh
sudo apt install git
```

Then install omf:

```sh
curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish
```

→ [Oh My Fish documentation](https://github.com/oh-my-fish/oh-my-fish)

---

### Step 3 · Install a Theme

This guide uses [**bobthefish**](https://github.com/oh-my-fish/theme-bobthefish) — a powerline-style theme with Git integration and a clean layout. Browse all available themes [here](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md).

```sh
omf install bobthefish
```

---

### Step 4 · Configure the Theme

Open the Fish config folder in Windows Explorer:

```sh
cd ~/.config/fish/ && explorer.exe .
```

Open `config.fish` and replace its contents with the following, then save:

```fish
if status is-interactive
    set -g theme_display_git_default_branch yes
    set -g theme_title_display_process yes
    set -g theme_title_display_path no
    set -g theme_title_use_abbreviated_path no
    set -g theme_date_format "+%d/%m/%y %H:%M"
    set -g theme_display_user yes
    set -g theme_display_hostname yes
    set -g fish_prompt_pwd_dir_length 6
    set -g theme_display_jobs_verbose yes
end
```

→ [What each option does](https://github.com/oh-my-fish/theme-bobthefish#configuration)

Result:

![bobthefish theme](https://user-images.githubusercontent.com/66394117/167346691-a587fdef-f7ee-402b-bc8d-e8fbbacfd956.png)

---

### Step 5 · Install a Nerd Font

The theme uses special glyphs that require a **Nerd Font**. Without one, you'll see placeholder boxes `[]` instead of icons.

This guide uses [**SauceCodePro Nerd Font**](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/SourceCodePro). Download the variants you need:

- [Regular](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Regular.ttf)
- [Semibold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-SemiBold.ttf)
- [Bold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Bold.ttf)

Open each `.ttf` file and click **Install**.

→ [Browse all Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts)

---

### Step 6 · Configure Windows Terminal

In Windows Terminal, click the **∨** arrow next to the tab bar → **Settings** → **Open JSON file** (bottom-left corner).

![Windows Terminal settings](https://user-images.githubusercontent.com/66394117/167333056-110bbec7-9a6d-47e6-afa7-0de095224df0.png)

- Under `"profiles"` → `"defaults"`:
    - Rename "Ubuntu" to **Fish** (or your preferred name)
    - Add the theme (colorScheme) "Campbell"
    - Set the **Fish** `"guid"` as the default profile for Windows Terminal.

<br>

![JSON config demo](https://user-images.githubusercontent.com/66394117/167347842-28c7987f-f7d0-433c-a3cb-499e465e3d63.gif)

<br>

If you want your Terminal to be translucent, add `opacity` and `useAcrylic` under `"defaults"`:

```json
"defaults": {
    "font": {
        "face": "SauceCodePro Nerd Font"
    },
    "opacity": 50,
    "useAcrylic": true
},
"list": [
    {
        "colorScheme": "Campbell",
        "icon": "https://avatars.githubusercontent.com/u/11728505?s=48&v=4",
        "guid": "{51855cb2-8cce-5362-8f54-464b92b32386}",
        "name": "Fish",
        "hidden": false,
        "source": "CanonicalGroupLimited.Ubuntu_79rhkp1fndgsc"
    }
]
```

> **Note:** Transparency requires **Transparency effects** to be enabled in Windows:  
> Start → Settings → Personalization → Colors → Transparency effects **On**

---

### Step 7 · Set Fish as the Default Shell

Run this inside your WSL session to make Fish the default shell for your user:

```sh
chsh -s /usr/bin/fish
```

> You may need to restart your WSL session for the change to take effect

---

### Step 8 · Choose a Symbol Style

Pick one of the two symbol rendering modes and run the corresponding command inside Fish:

**PowerLine style:**
```fish
set -g theme_powerline_fonts yes
set -g theme_nerd_fonts no
```
![PowerLine style](https://user-images.githubusercontent.com/66394117/167333059-6ca5c91b-0427-4267-95ba-2d824b7658af.png)

**Nerd Fonts style:**
```fish
set -g theme_powerline_fonts no
set -g theme_nerd_fonts yes
```
![Nerd Fonts style](https://user-images.githubusercontent.com/66394117/167333061-ae2f1e0d-ab6b-470d-afa2-15b143d02417.png)

---

## Reference Links

| Resource | Link |
|----------|------|
| Fish Shell | [fishshell.com](https://fishshell.com/) |
| Fish on GitHub | [fish-shell/fish-shell](https://github.com/fish-shell/fish-shell) |
| Oh My Fish | [oh-my-fish/oh-my-fish](https://github.com/oh-my-fish/oh-my-fish) |
| omf Themes | [Themes Gallery](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md) |
| bobthefish | [theme-bobthefish](https://github.com/oh-my-fish/theme-bobthefish) |
| Nerd Fonts | [ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts) |
| WSL Install | [Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/install) |
| Windows Terminal | [Microsoft Store](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) |

---

*Originally written in 2022. Contributions and corrections are welcome via pull request.*
