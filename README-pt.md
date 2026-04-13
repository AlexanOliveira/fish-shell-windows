# [Fish Shell no Windows (WSL)](#fish-shell-no-windows-wsl)

<br>

<div align="center">

[![](https://img.shields.io/badge/🇺🇸%20English-click%20here-0078d4?style=for-the-badge)](./README.md)

</div>

### Um tutorial completo de instalação — de um terminal padrão pra um bonitão e produtivo

> **Antes de começar:** Crie um Ponto de Restauração do Sistema (C:/) — faça isso sempre antes de instalar ou alterar configurações do Windows.

---

## O Resultado Final

Antes

![ugly cmd](https://user-images.githubusercontent.com/66394117/167328153-b031a76a-1d4e-4005-862f-e6ff7cd2cd85.gif)

Depois

![final result](https://user-images.githubusercontent.com/66394117/167418650-5297e4d5-2dbc-4cb6-8732-c7611a86c2db.gif)

## Visão Geral

O **Fish** (Friendly Interactive Shell) é um dos vários interpretadores de linha de comando — ao lado do bash, zsh e PowerShell — que fazem a ponte entre você e o sistema operacional. O diferencial do Fish é que o autocompletar e as sugestões inline já funcionam por padrão, sem nenhuma configuração.

→ [Saiba mais em fishshell.com](https://fishshell.com/)

Como Fish é um shell Unix, ele não roda nativamente no Windows. Você vai precisar do **Windows Subsystem for Linux (WSL)** — e é exatamente isso que este tutorial ensina a fazer.

## [Parte 1 — WSL & Ubuntu](#parte-1--wsl--ubuntu)

### Passo 1 · Instalar o WSL

Abra o **Prompt de Comando (cmd)** como Administrador e execute:

```sh
wsl --install
```

> **Dica:** Se `Ctrl+V` não funcionar no terminal, clique com o botão direito do mouse para colar.

Este comando vai:
- Ativar os componentes **WSL** e **Plataforma de Máquina Virtual**
- Baixar e instalar o **kernel do Linux** mais recente
- Baixar e instalar a distribuição **Ubuntu**

Ao finalizar, **reinicie o computador**.

> Se `wsl --install` exibir o menu de ajuda em vez de instalar, o WSL já está presente — pule para o Passo 2.  
> Se a instalação automática falhar, siga o [tutorial de instalação manual da Microsoft](https://docs.microsoft.com/pt-br/windows/wsl/install).

---

#### WSL 2 — Requisito Hyper-V

O WSL 2 (versão recomendada) requer suporte a Hyper-V / Virtualização. Verifique se está ativado no Gerenciador de Tarefas, na aba **Desempenho**.

![Task Manager Virtualization](https://github.com/user-attachments/assets/7853037c-1688-4fad-abee-0b3382aef30c)

Se aparecer como **Desativado**, reinicie o computador e ative nas configurações da BIOS — geralmente fica localizado em **Advanced** ou **CPU Configuration**.

> Sem Hyper-V? Você ainda pode instalar o WSL 1, mas o WSL 2 é fortemente recomendado.

---

### Passo 2 · Configurar o Ubuntu

Abra o **Ubuntu** pelo Menu Iniciar. Se não aparecer, encontre a versão instalada na [Microsoft Store](https://aka.ms/wslstore) e clique em **Abrir**.

Aguarde a instalação inicial terminar e crie um **nome de usuário** e uma **senha** quando solicitado.

![Ubuntu first run](https://user-images.githubusercontent.com/66394117/167333051-7444d201-00e5-4d95-8395-56771fa941d7.png)

---

### Passo 3 · Instalar o Fish

Abra o **cmd** e execute o comando `wsl` or `bash` para acessar o ambiente **Linux (Ubuntu)**


Adicione o repositório do Fish, atualize os pacotes e instale:

```sh
sudo apt-add-repository ppa:fish-shell/release-3
sudo apt update && sudo apt upgrade
sudo apt install fish
```

> Se `apt-add-repository` retornar "not found command", execute `sudo apt install software-properties-common`

<br>

Pronto — o Fish está instalado. Para iniciá-lo, execute `fish` no **Terminal Linux (bash ou wsl)**
<br>

## [Parte 2 — Aparência do Terminal](#parte-2--aparência-do-terminal)

### Passo 1 · Instalar o Windows Terminal

Esqueça o terminal padrão. Instale o [**Windows Terminal**](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) pela Microsoft Store para uma experiência moderna com abas.

---

### Passo 2 · Instalar o Oh My Fish

Oh My Fish (omf) é o gerenciador de plugins e temas do Fish. Primeiro, certifique-se de que o Git está disponível:

```sh
sudo apt install git
```

Em seguida, instale o omf:

```sh
curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish
```

→ [Documentação Oh My Fish](https://github.com/oh-my-fish/oh-my-fish)

---

### Passo 3 · Instalar um Tema

Este tutorial usa o [**bobthefish**](https://github.com/oh-my-fish/theme-bobthefish) — um tema estilo powerline com integração ao Git e visual limpo. Veja todos os temas disponíveis [aqui](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md).

```sh
omf install bobthefish
```

---

### Passo 4 · Configurar o Tema

Abra a pasta de configuração do Fish no Windows Explorer:

```sh
cd ~/.config/fish/ && explorer.exe .
```

Abra o arquivo `config.fish`, substitua o conteúdo pelo código abaixo e salve:

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

→ [O que cada opção faz](https://github.com/oh-my-fish/theme-bobthefish#configuration)

Resultado:

![bobthefish theme](https://user-images.githubusercontent.com/66394117/167346691-a587fdef-f7ee-402b-bc8d-e8fbbacfd956.png)

---

### Passo 5 · Instalar uma Nerd Font

O tema usa símbolos especiais que exigem uma **Nerd Font**. Sem ela, você verá caixinhas `[]` no lugar dos ícones.

Este tutorial usa a [**SauceCodePro Nerd Font**](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/SourceCodePro). Baixe as variantes que preferir:

- [Regular](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Regular.ttf)
- [Semibold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-SemiBold.ttf)
- [Bold](https://github.com/ryanoatics/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Bold.ttf)

Abra cada arquivo `.ttf` e clique em **Instalar**.

→ [Ver todas as Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts)

---

### Passo 6 · Configurar o Windows Terminal

No Windows Terminal, clique na seta **∨** ao lado da barra de abas → **Configurações** → **Abrir arquivo JSON** (canto inferior esquerdo).

![Windows Terminal settings](https://user-images.githubusercontent.com/66394117/167333056-110bbec7-9a6d-47e6-afa7-0de095224df0.png)

- Em `"profiles"` → `"defaults"`:
    - Renomeie "Ubuntu" para **Fish** (ou outro nome de sua preferência)
    - Adicione o tema (colorScheme) "Campbell"
    - Defina o `"guid"` do **Fish** como perfil padrão do Windows Terminal

<br>

![JSON config demo](https://user-images.githubusercontent.com/66394117/167347842-28c7987f-f7d0-433c-a3cb-499e465e3d63.gif)

<br>

Se quiser o terminal translúcido, adicione `opacity` e `useAcrylic` dentro de `"defaults"`:

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

> **Atenção:** A transparência exige que os **Efeitos de transparência** estejam ativados no Windows:  
> Iniciar → Configurações → Personalização → Cores → Efeitos de transparência **Ativado**

---

### Passo 7 · Definir o Fish como Shell Padrão

Execute este comando dentro da sessão WSL para tornar o Fish o shell padrão do seu usuário:

```sh
chsh -s /usr/bin/fish
```

> Pode ser necessário reiniciar a sessão WSL para a alteração ter efeito.

---

### Passo 8 · Escolher o Estilo dos Símbolos

Escolha um dos dois modos de renderização e execute o comando correspondente dentro do Fish:

**Estilo PowerLine:**
```fish
set -g theme_powerline_fonts yes
set -g theme_nerd_fonts no
```
![PowerLine style](https://user-images.githubusercontent.com/66394117/167333059-6ca5c91b-0427-4267-95ba-2d824b7658af.png)

**Estilo Nerd Fonts:**
```fish
set -g theme_powerline_fonts no
set -g theme_nerd_fonts yes
```
![Nerd Fonts style](https://user-images.githubusercontent.com/66394117/167333061-ae2f1e0d-ab6b-470d-afa2-15b143d02417.png)

---

## Links de Referência

| Recurso | Link |
|---------|------|
| Fish Shell | [fishshell.com](https://fishshell.com/) |
| Fish no GitHub | [fish-shell/fish-shell](https://github.com/fish-shell/fish-shell) |
| Oh My Fish | [oh-my-fish/oh-my-fish](https://github.com/oh-my-fish/oh-my-fish) |
| Temas omf | [Galeria de Temas](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md) |
| bobthefish | [theme-bobthefish](https://github.com/oh-my-fish/theme-bobthefish) |
| Nerd Fonts | [ryanoasis/nerd-fonts](https://github.com/ryanoasis/nerd-fonts) |
| Instalar WSL | [Microsoft Docs](https://docs.microsoft.com/pt-br/windows/wsl/install) |
| Windows Terminal | [Microsoft Store](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) |

---

*Escrito originalmente em 2022. Contribuições e correções são bem-vindas via pull request.*
