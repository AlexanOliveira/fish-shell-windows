# Installing Fish on Windows (WSL) - A Complete step by step for Beginners (or not)

[{ Versão em Português }](https://github.com/AlexanOliveira/fish-shell-windows/blob/main/README-pt.md)

#### When you finish this Tutorial, you'll go from this:
![ugly cmd](https://user-images.githubusercontent.com/66394117/167328153-b031a76a-1d4e-4005-862f-e6ff7cd2cd85.gif)

#### To this:
![final_627913e0199a88007600ec03_565928](https://user-images.githubusercontent.com/66394117/167418650-5297e4d5-2dbc-4cb6-8732-c7611a86c2db.gif)

<br>

## About
**Fish** is a command interpreter; one of several translators between User and Operating System known as **shell**, such as: cmd, PowerShell, bash, zsh, etc..

One of the best things of **Fish** is that the AutoComplete and AutoSuggestion features are factory-installed, ready to use with no need to install or configure.

[Click here](https://fishshell.com/) to learn more about **Fish Shell**

Since **Fish** is a shell for **Unix**, that means, it doesn't work on standard Windows, so you will need to install **Windows Subsystem for Linux (WSL)**
<br>

## [IMPORTANT](#important)
Before proceeding with this tutorial, create a **System Restore Point** (C:/) - **ALWAYS** do that when installing or changing Windows settings.
<br>

### WSL 2 Prerequisite

To install the latest and best version of WSL (WSL 2), your machine needs to support Hyper-V. In some cases, Windows 11 may have it enabled by default. To check, open the Task Manager.

![image](https://github.com/user-attachments/assets/7853037c-1688-4fad-abee-0b3382aef30c)

If it's disabled, restart your machine and access the BIOS to enable it. The Hyper-V/Virtualization setting is usually found under **Advanced** or **CPU Configuration**.

> Note: If you don’t have Hyper-V, you can still install WSL version 1.

# Installation

#### Microsoft Documentation
- [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install)
- [Install WSL (manually)](https://docs.microsoft.com/en-us/windows/wsl/install)
<br>

### 1) Installing WSL (Windows Subsystem for Linux)
Open **Command Prompt (cmd)** as Administrator and run the command below.
>Note: If `wsl --install` returns the **HELP Menu**, this means you already have wsl installed - go to the [next step](https://github.com/AlexanOliveira/fish-shell-windows/edit/main/README.md#2-configuring-ubuntu)

	wsl --install
>*Note: If* <kbd>Ctrl + v</kbd> *doesn't work in the terminal, press the* <kbd>right mouse button</kbd> *to paste.*

<br>

`wsl --install` will execute the following actions:
- Enables the **WSL** and **Virtual Machine Platform** components
- Downloads and install the latest **Linux Kernel**
- Downloads and installs the **Ubuntu** Linux distribution

After complete installation, **Restart your Computer**


>Note: If the auto installation fails, install [manually](https://docs.microsoft.com/en-us/windows/wsl/install)

<br>



### 2) Configuring Ubuntu
Now that ***WSL*** has been installed, click on the **Start Menu** and open the "app" **Ubuntu**

>Note: If the app doesn't appear, [click here](https://aka.ms/wslstore) and search for **Ubuntu**, select the installed version and click **Start**

<br>

Wait for the installation to finish and register a ***username*** and ***password***

![1](https://user-images.githubusercontent.com/66394117/167333051-7444d201-00e5-4d95-8395-56771fa941d7.png)
<br>



### 3) Installing Fish

#### Fish Documentation
- [Official Website](https://fishshell.com/)
- [Official GitHub](https://github.com/fish-shell/fish-shell/#building)
- [Installing](https://github.com/fish-shell/fish-shell/#getting-fish)
<br>

Open **cmd** and run the command `bash` or `wsl` to access your **Linux (Ubuntu)** environment
<br>

###### Installing the Fish repository

	sudo apt-add-repository ppa:fish-shell/release-3

>Note: if `apt-add-repository` is a not found command run `sudo apt install software-properties-common`

<br>

###### Checking and Installing Updates
	sudo apt update && sudo apt upgrade
<br>

###### Installing Fish
	sudo apt install fish

### [Sets Fish as default Shell](#sets-fish-as-default-shell-on-windows-terminal)

<br>

That's it, congratulations, you have installed the **Fish Shell** on your Windows.

Now just run the command `fish` in **Ubuntu Terminal (bash or wsl)** to access your new shell
<br>
<br>



# [Configuring Terminal's Appearance](#Configuring-terminal-visual)

Now let's make your terminal look nicer.
<br>



### 1) Installing Windows Terminal

We will no longer use the old standard terminal. [Click here](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=pt-br&gl=br) and install **Windows Terminal**


- To make some modifications to **Fish**, it is necessary to install the plugin manager **Oh My Fish**

<br>



### 2) Installing Oh My Fish (omf)

#### Oh My Fish Documentation
- [Official GitHub](https://github.com/oh-my-fish/oh-my-fish)
<br>

Open **cmd** through **Windows Terminal** and run `wsl`, then `fish` to access the **Fish Shell**.
<br>

To continue we need **Git**

	sudo apt install git

###### Installing omf

	curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish
<br>



### 3) Installing the Theme

You can preview and choose another theme [by clicking here](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md)

However, in this tutorial we'll **install** and **configure** the [**bobthefish**](https://github.com/oh-my-fish/theme-bobthefish) theme

	omf install bobthefish
<br>



### 4) Configuring bobthefish Theme

Use the command below to enter the **fish** folder and open it in Windows

	cd ~/.config/fish/ && explorer.exe .

Now open the `config.fish` file, paste the codes below and then Save the file

	if status is-interactive
		# Commands to run in interactive sessions can go here
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

[Click here](https://github.com/oh-my-fish/theme-bobthefish#configuration) to learn what each command above does

###### This will be the result
![2](https://user-images.githubusercontent.com/66394117/167346691-a587fdef-f7ee-402b-bc8d-e8fbbacfd956.png)


<br>



### 5) Installing Nerd Font
#### Nerd Fonts Documentation
- [Official GitHub](https://github.com/ryanoasis/nerd-fonts)
<br>

To replace the "errors" [] with Symbols, we need to install a font from **Nerd Fonts**.
We'll install [**SourceCode Pro** (SauceCodePro NF)](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/SourceCodePro). To see more Fonts [click Here](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts)

You can install all the styles if you want. I usually install just these three:
[Regular](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Regular.ttf), 
[Semibold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-SemiBold.ttf) and 
[Bold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Bold.ttf)

After downloading, go to your **Downloads** folder in Windows and run all the **.ttf** files to install the font.

<br>

### 6) Configuring Windows Terminal

Now we can change the terminal font to fix the []

Click on the little arrow **>** Settings
![3](https://user-images.githubusercontent.com/66394117/167333056-110bbec7-9a6d-47e6-afa7-0de095224df0.png)

Click **Open JSON file** in the lower-left corner of the screen

* Inside "profiles"**>**"default" do the changes below, then Save the file:
	* Change the **name** of the "Ubuntu" you installed to **Fish** (or any other)
	* Add the theme (colorScheme) "Campbell"
	* Add the **guid** of **Fish** to be the default Windows Terminal Profile


![json terminal](https://user-images.githubusercontent.com/66394117/167347842-28c7987f-f7d0-433c-a3cb-499e465e3d63.gif)
<br>

If you want your Terminal to be translucent, add the values ​​below inside **"defaults"**
>Note: **Transparency effects** must be enabled in Windows for this to work: Start Menu **>** Settings **>** Personalization **>** Colors

```json
"defaults": {
	"opacity": 50,
	"useAcrylic": true,
	"font": {
        	"face": "SauceCodePro Nerd Font"
	}
},
"list":
[
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

###### Sets **Fish** as default **Shell** on Windows Terminal

	chsh -s /usr/bin/fish

<br>



### 7) Configuring Symbols (Font)

You can choose between two symbol styles: **PowerLine Fonts** or **Nerd Fonts**

	set -g theme_powerline_fonts yes

![5](https://user-images.githubusercontent.com/66394117/167333059-6ca5c91b-0427-4267-95ba-2d824b7658af.png)


or

	set -g theme_nerd_fonts yes

![6](https://user-images.githubusercontent.com/66394117/167333061-ae2f1e0d-ab6b-470d-afa2-15b143d02417.png)

>Note: Use `yes` to **enable** and `no` to **disable** (sets only one as YES)

<br>

# [THE END](#to-this)
<br>
