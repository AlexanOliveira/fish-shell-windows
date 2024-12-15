# Instalando Fish no Windows (WSL) - Passo a passo completo para Iniciantes (ou não)

[{ English Version }](https://github.com/AlexanOliveira/fish-shell-windows/blob/main/README.md)

#### Ao terminar este Tutorial, você sairá disso:
![cmd feio](https://user-images.githubusercontent.com/66394117/167328153-b031a76a-1d4e-4005-862f-e6ff7cd2cd85.gif)

#### Para isso:
![final_627913e0199a88007600ec03_565928](https://user-images.githubusercontent.com/66394117/167418650-5297e4d5-2dbc-4cb6-8732-c7611a86c2db.gif)

<br>

## Sobre
**Fish** é um interpretador de comandos; um dos diversos tradutores entre Usuário e o Sistema Operacional conhecidos como **shell**, tais como: cmd, PowerShell, bash, zsh, etc..

Umas das melhores vantagens do **Fish** são as funcionalidades AutoComplete e AutoSuggestion virem instaladas de fábrica, prontas para uso sem a necessidade de instalar ou configurar nada.

[Clique aqui](https://fishshell.com/) para saber mais sbore o **Fish Shell**

Como **Fish** é um shell para **Unix**, ou seja, não funciona no Windows padrão, então será necessário instalar o **Windows Subsystem for Linux (WSL)**
<br>

## [IMPORTANTE](#importante)
Antes de seguir com o passo a passo, crie um **Ponto de Restauração do Sistema** (C:/) - faça isso **SEMPRE** que for instalar ou alterar configurações do Windows.
<br>

### Pré requisito WSL 2

Para instalar a versão mais recente e melhor do WSL (WSL 2), sua máquina precisa ter suporte Hyper-V. Há casos do Windows 11 já vir habilitado, para conferir, acesse o Gerenciador de Tarefas.

![image](https://github.com/user-attachments/assets/7853037c-1688-4fad-abee-0b3382aef30c)

Caso esteja desabilitado, reinicie sua máquina e acesse a BIOS para habilitá-la. A configuração do Hyper-V/Virtualização geralmente fica localizada em **Advanced** ou **CPU Configuration**

> Obs: se não possuir Hyper-V, você ainda pode instalar a versão 1 do WSL.

# Instalação

#### Documentações da Microsoft
- [Instalar WSL](https://docs.microsoft.com/en-us/windows/wsl/install)
- [Instalar WSL (manualmente)](https://docs.microsoft.com/en-us/windows/wsl/install)
<br>

### 1) Instalando WSL (Windows Subsystem for Linux)
Abra o **Pronpt de Comando (cmd)** como Administrador e execute o comando abaixo.
>Obs: Se `wsl --install` retornar o **HELP Menu**, isso significa que você já tem o **wsl** instalado - vá para o [próximo passo](https://github.com/AlexanOliveira/fish-shell-windows/edit/main/README.md#2-configurando-o-ubuntu)

	wsl --install
>*Obs: Caso* <kbd>Ctrl + v</kbd> *não funcione no terminal, aperte o* <kbd>botão direito</kbd> *do mouse para colar.*

<br>

`wsl --install` executará as seguintes ações:
- Habilitar os componentes **WSL** e **Virtual Machine Platform**
- Baixar e instalar o **Linux Kernel** mais recente
- Baixar e instalar a distribuição **Ubuntu** do Linux

Após a instalação ser finalizada, **Reinicie seu Computador**


>Obs: Se a instalação automática der problema, instale [manualmente](https://docs.microsoft.com/en-us/windows/wsl/install)

<br>



### 2) Configurando o Ubuntu
Agora com o ***WSL*** instalado, clique no **Menu Iniciar** e abra o "app" **Ubuntu**

>Obs: Se o app não aparecer, [clique aqui](https://aka.ms/wslstore) e pesquise por **Ubuntu**, selecione a versão instalada e depois clique em **Iniciar**

<br>

Aguarde finalizar a instalação e cadastre um ***username*** e ***senha***

![1](https://user-images.githubusercontent.com/66394117/167333051-7444d201-00e5-4d95-8395-56771fa941d7.png)
<br>



### 3) Instalando o Fish

#### Documentações do Fish
- [Site Oficial](https://fishshell.com/)
- [GitHub Oficial](https://github.com/fish-shell/fish-shell/#building)
- [Instalando](https://github.com/fish-shell/fish-shell/#getting-fish)
<br>

Abra o **cmd** e execute `bash` ou `wsl` para acessar seu ambiente **Linux (Ubuntu)**
<br>

###### Instalando o repositório do Fish

	sudo apt-add-repository ppa:fish-shell/release-3

>Obs: Se `apt-add-repository` for um "comando não encontrado", execute `sudo apt install software-properties-common`

<br>

###### Checando e Instalando atualizações
	sudo apt update && sudo apt upgrade
<br>

###### Instalando o Fish
	sudo apt install fish

### [Definindo Fish como Shell padrão](#definindo-o-fish-como-shell-padr%C3%A3o-do-windows-terminal)

<br>

É isso ai, parabéns, você instalou o **Fish Shell** no seu Windows.

Agora basta executar `fish` no **Terminal Ubuntu (bash ou wsl)** para acessar seu novo Shell
<br>
<br>



# [Configurando o Visual do terminal](#configurando-o-visual-do-terminal)

Agora vamos deixar seu terminal com um visual mais agradável.
<br>



### 1) Instalando o Windows Terminal

Não usaremos mais o antigo terminal padrão. [Clique aqui](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701?hl=pt-br&gl=br) e instale o **Windows Terminal**


- Para fazer algumas modificações no **Fish**, é necessário instalar o plugin manager **Oh My Fish**

<br>



### 2) Instalando Oh My Fish (omf)

#### Documentação do Oh My Fish
- [GitHub Oficial](https://github.com/oh-my-fish/oh-my-fish)
<br>

Abra o **cmd** pelo **Windows Termina**l e execute `wsl`, depois `fish` para acessar o **Fish Shell**.
<br>

Para continuar precisamos do **Git**

	 sudo apt install git

###### Instalando omf

	curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish
<br>



### 3) Instalando o Tema

Você pode visualizar e escolher outro tema [clicando aqui](https://github.com/oh-my-fish/oh-my-fish/blob/master/docs/Themes.md)

Porém, neste passo a passo iremos **instalar** e **configurar** o tema [**bobthefish**](https://github.com/oh-my-fish/theme-bobthefish)

	omf install bobthefish
<br>



### 4) Configurando o Tema bobthefish

Use o comando abaixo para entrar na pasta **fish** e abri-la no Windows

	cd ~/.config/fish/ && explorer.exe .

Agora abra o arquivo `config.fish`, cole os códigos abaixo e depois Salve a alteração

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

[Clique aqui](https://github.com/oh-my-fish/theme-bobthefish#configuration) para saber o que cada comando acima faz

###### Esse será o resultado
![2](https://user-images.githubusercontent.com/66394117/167346691-a587fdef-f7ee-402b-bc8d-e8fbbacfd956.png)


<br>



### 5) Instalando a Nerd Font
#### Documentação da Nerd Fonts
- [GitHub Oficial](https://github.com/ryanoasis/nerd-fonts)
<br>

Para trocar os "erros" [] por Simbolos, precisamos instalar uma fonte do **Nerd Fonts**.
Iremos instalar a [**SourceCode Pro** (SauceCodePro NF)](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/SourceCodePro). Para ver mais Fontes [clique aqui](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts)

Você pode instalar todas os estilos, se quiser. Eu constumo instalar apenas essas três:
[Regular](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Regular.ttf), 
[Semibold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-SemiBold.ttf) e 
[Bold](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/SourceCodePro/SauceCodeProNerdFont-Bold.ttf)

Após baixar, acesse sua pasta de **Downloads** do Windows e execute todos os arquivos **.ttf** para instalar a fonte.

<br>

### 6) Configurando o Windows Terminal

Agora podemos alterar a fonte do terminal para arrumar os []

Clique na setinha **>** Configurações
![3](https://user-images.githubusercontent.com/66394117/167333056-110bbec7-9a6d-47e6-afa7-0de095224df0.png)

Clique em **Abrir o arquivo JSON** no canto inferior esquerdo da tela

* Dentro de "profiles"**>**"default" faça as alterações abaixo e Salve o arquivo:
	* Alterar o **name** do "Ubuntu" que você instalou para **Fish** (ou qualquer outro)
	* Adicionar o tema (colorScheme) "Campbell"
	* Adicionar o **guid** do **Fish** para ser o Perfil padrão do Windows Terminal


![terminal json](https://user-images.githubusercontent.com/66394117/167347842-28c7987f-f7d0-433c-a3cb-499e465e3d63.gif)
<br>

Caso queira seu Terminal translúcido, adicione os valores abaixo dentro de **"defaults"**
>Obs: **Efeitos de transparência** precisa estar Ativado no Windows para funcionar: Menu Iniciar **>** Configurações **>** Personalização **>** Cores

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

###### Definindo o **Fish** como **Shell** padrão do Windows Terminal

	chsh -s /usr/bin/fish

<br>



### 7) Configurando os Simbolos (Fonte)

Você pode escolher entre dois estilos de símbolos: **PowerLine Fonts** ou **Nerd Fonts**

	set -g theme_powerline_fonts yes

![5](https://user-images.githubusercontent.com/66394117/167333059-6ca5c91b-0427-4267-95ba-2d824b7658af.png)


ou

	set -g theme_nerd_fonts yes

![6](https://user-images.githubusercontent.com/66394117/167333061-ae2f1e0d-ab6b-470d-afa2-15b143d02417.png)

>Obs: Use `yes` para **ativar** e `no` para **desativar** (deixar apenas uma como YES)

<br>

# [FIM](#para-isso)
<br>
