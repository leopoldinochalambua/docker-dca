# Principais comandos e açções do git

## Instalação do git

```bash
sudo apt install git
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui gitk gitweb git-cvs
  git-mediawiki git-svn
The following NEW packages will be installed:
  git
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,166 kB of archives.
After this operation, 18.9 MB of additional disk space will be used.
Get:1 http://ao.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.10 [3,166 kB]
Fetched 3,166 kB in 4s (821 kB/s)                      
Selecting previously unselected package git.
(Reading database ... 273022 files and directories currently installed.)
Preparing to unpack .../git_1%3a2.34.1-1ubuntu1.10_amd64.deb ...
Unpacking git (1:2.34.1-1ubuntu1.10) ...
Setting up git (1:2.34.1-1ubuntu1.10) ...
```

Verificando a instalação. 
```bash
paulo@dev:dcker-dca$ git --version 
git version 2.34.1
paulo@dev:dcker-dca$ 
```

### Configuração Inicial do Git

Agora que você tem o Git em seu sistema, você deve fazer algumas coisas para personalizar o ambiente Git. Você fará isso apenas uma vez por computador e o efeito se manterá após atualizações. Você também pode mudá-las em qualquer momento rodando esses comandos novamente.

O Git vem com uma ferramenta chamada [git config] que permite ver e atribuir variáveis de configuração que controlam todos os aspectos de como o Git aparece e opera. Estas variáveis podem ser armazenadas em três lugares diferentes:

* /etc/gitconfig: válido para todos os usuários no sistema e todos os seus repositórios. Se você passar a opção --system para git config, ele lê e escreve neste arquivo.
* .gitconfig ou ./git/config: Somente para o seu usuário. Você pode fazer o Git ler e escrever neste arquivo passando a opção --global.
* config no diretório Git (ou seja, .git/config) de qualquer repositório que você esteja usando: específico para este repositório.

Cada nível sobrescreve os valores no nível anterior, ou seja, valores em .git/config prevalecem sobre /etc/gitconfig.

No Windows, Git procura pelo arquivo .gitconfig no diretório $HOME (C:\Users\$USER para a maioria). Ele também procura por /etc/gitconfig, mesmo sendo relativo à raiz do sistema, que é onde quer que você tenha instalado Git no seu sistema.

## Sua Identidade

A primeira coisa que você deve fazer ao instalar Git é configurar seu nome de usuário e endereço de e-mail. Isto é importante porque cada commit usa esta informação, e ela é carimbada de forma imutável nos commits que você começa a criar:

> git config --global user.name "leopoldinopaulo"
```bash
paulo@dev:~$ git config --global user.name "leopoldinopaulo"
```

> git config --global user.email meuemail@exemplo.com
```bash
paulo@dev:~$ git config --global user.email "exemplo@hotmail.com"
```

> Nesta sessão deve ser colocado um email valido, de preferência o mesmo que se usado para o GitHub, que veremos mais tarde.

> git config --global core.editor
```bash
paulo@dev:~$ git config --global core.editor geany
```
Agora que a sua identidade está configurada, você pode escolher o editor de texto padrão que será chamado quando Git precisar que você entre uma mensagem. Se não for configurado, o Git usará o editor padrão, que normalmente é o Vim. 

Reiterando, você precisará fazer isso somente uma vez se tiver usado a opção [--global], porque então o Git usará esta informação para qualquer coisa que você fizer naquele sistema. Se você quiser substituir essa informação com nome diferente para um projeto específico, você pode rodar o comando sem a opção [--global] dentro daquele projeto.

Muitas ferramentas GUI o ajudarão com isso quando forem usadas pela primeira vez.

A linha abaixo mostra o resultado dessas configurações
```bash
paulo@dev:dcker-dca$ git config --global user.name "leopoldionpaulo"
paulo@dev:dcker-dca$ git config --global user.email "leopaulo227@hotmail.com"
paulo@dev:dcker-dca$ git config --global core.editor geany
paulo@dev:dcker-dca$ git config --list
user.name=leopoldionpaulo
user.email=example@hotmail.com
core.editor=geany
```
Vamos marcar as baranch como main
```bash
paulo@dev:dcker-dca$ git config --global init.defaultBranch main
```

Deste ponto podemos criar um repositório com o comando `git init`

```bash
paulo@dev:docker-dca$ ls -a
 .    files    'pics&md'       README.md   Vagrantfile
 ..   LICENSE   provision.sh   .vagrant
paulo@dev:docker-dca$ git init 
Initialized empty Git repository in /home/paulo/projetos/devop/docker-dca/.git/
paulo@dev:docker-dca$ ls -a
 .    files   LICENSE    provision.sh   .vagrant
 ..   .git   'pics&md'   README.md      Vagrantfile
```
Apois editar o codigo podemos usar o comando `git status` para ver se o git já esta a monitorar o projeto.

```bash
paulo@dev:docker-dca$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.vagrant/
	LICENSE
	README.md
	Vagrantfile
	files/
	pics&md/
	provision.sh

nothing added to commit but untracked files present (use "git add" to track)
```
Podemos ver que ainda não temos nenhum commt e que tem arquivos que o git ainda não está a monitorar. Ele informa como **untracked**

Para que o git possa fazer isso o comando `git add` é usado com o nome do arquivo a ser adicionado, caso sejam muitos arquivos podemos usar um pont ou asteristico.

Reepare que tem um diretório oculto que não é ecessario estar trakeado, para isso vamos criar um arquivo para que o git ignore esse diretório.

```bash
paulo@dev:docker-dca$ vim .gitignore
vim .gitignore
.vagrant
~
~
```

Usando o comando `git status` novamente veja que o diretório já não esta presente.

```bash
paulo@dev:docker-dca$ git status 
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	.gitignore
	LICENSE
	README.md
	Vagrantfile
	files/
	pics&md/
	provision.sh

nothing added to commit but untracked files present (use "git add" to track)
```




