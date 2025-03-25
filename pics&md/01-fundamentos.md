# Links Importantes: 
1. https://www.youtube.com/watch?v=4Wk0NvDWTLQ
2. https://www.youtube.com/watch?v=SQRWc1_gqXQ
3. https://www.youtube.com/watch?v=yTUtxWlomW8
4. https://www.youtube.com/watch?v=3JgBey71_wk
5. https://www.youtube.com/watch?v=GI-KHZF0ASg
6. https://www.youtube.com/watch?v=oap6A7VxtDs
7. https://www.youtube.com/watch?v=kxcc_PaBCm4&t=133s
* https://kinsta.com/pt/base-de-conhecimento/que-e-docker/
* https://www.hostinger.com.br/tutoriais/o-que-e-docker
* https://www.cyberciti.biz/cloud-computing/use-vagrant-to-create-small-virtual-lab-on-linux-osx/ - criar lab
* https://rolfstreefkerk.com/article/how-to-create-a-flexible-dev-environment-with-vagrant-and-docker
* https://github.com/rofrano/lab-vagrant

# Capítulo 01 - Fundamentos

## O que é o Docker

Docker é uma plataforma Open Source escrita em Go (Linguagem de programação em alta performance desenvolvida pela Google) que ajuda na criação e a administração de ambientes isolados.

Com a utilização do Docker podemos gerenciar toda a infraestutura de uma aplicação, bem como garantir que ambientes de desenvolvimento, homologação e produção contenham os mesmos componentes e versões de aplicações, a fim de minimizar impactos no processo de desenvolvimento e entrega de software.

O Docker trabalha com uma virtualização a nível do sistema operacional, onde o mesmo utiliza de recursos como o kernel do sistema hospedeiro para executar seus containers. Diferente do modelo tradicional de Máquinas Virtuais, o Docker não necessita da instalação de um sistema operacional por completo, e sim apenas dos arquivos necessários para a aplicação ser executada. 

Embora o Docker e as máquinas virtuais tenham um propósito semelhante, seu desempenho, portabilidade e suporte a sistemas operacionais diferem significativamente.

A principal diferença é que os containers do Docker compartilham o sistema operacional do host, enquanto as máquinas virtuais também têm um sistema operacional convidado sendo executado no sistema host. Esse método de operação afeta o desempenho, as necessidades de hardware e o suporte do SO. Confira a tabela abaixo para uma comparação detalhada.

![Weaveworks - VM x Containers](resources/01vmvsdocker.png)

## Por que usar Docker?

Em 2013, Docker introduziu o que se tornou o padrão da indústria para containers, trouxe uma maneira simples, rápida e eficiente de executar aplicações sem a complexidade de uma máquina virtual.

Docker garante um ecossistema consistente, fazendo com que o desenvolvedor possa trabalhar sem se preocupar, por exemplo, com a abertura de tickets para uma equipe de infraestrutura provisionar um ambiente por completo, atrasando o trabalho de entrega de software.

Existem diversas engines e runtimes de containers e até é possível utilizar containers sem Docker, mas atualmente o Docker é a engine/runtime de container mais utilizada no mercado, o que torna o conhecimento do mesmo um **"Must have"** e dificilmente encontramos vagas na área de tecnologia que não pedem um conhecimento, mesmo que básico, de containers ou Docker.

## O que é um container

Um container consiste de um ambiente completo (uma aplicação e todas suas dependências, bibliotecas, binários, arquivos de configuração) em um único pacote. Ao containerizar uma plataforma de aplicação e suas dependências as diferenças em distribuições de sistemas operacionais e camadas inferiores da infraestrutura são abstraídas.

Todas as configurações e instruções para iniciar ou parar containers são ditadas pela imagem do Docker. Sempre que um usuário executa uma imagem, um novo container é criado.

É fácil gerenciar containers com a ajuda da API do Docker ou da interface de linha de comando (ILC). Se forem necessários vários containers, os usuários podem controlá-los com a Ferramenta de composição do Docker.

> Imagine que o container Docker é como se fosse um container real em um navio (servidor), todos os containeres estão lado a lado, porém seu conteúdo (ecossistema) não tem interferência de outros containers.

Podemos dizer também que um container é a unidade mínima computacional do Docker, ou seja, o menor recurso que o Docker pode fornecer.

![Container](resources/01container.png)

## Versões

O Docker possui basicamente duas versões, a versão da comunidade (Community Edition) e a versão empresarial (Enterprise Edition).

A versão Community é de uso gratuito e também tem seu código aberto.

A maioria dos sistemas Docker em produção utiliza a versão Docker Community Edition. O licenciamento anual da versão Enterprise custa cerca de **US$750** por nó, o que torna o processo inviável para algumas empresas.

> **ATENÇÃO:** Para fins da prova Docker Certified Associate **(Docker DCA)** a versão Community deve ser utilizada apenas em ambientes de desenvolvimento e não deve ser utilizada em produção. Para produção a única versão a ser utilizada é a Enterprise Edition.

A versão Enterprise conta com recursos como o **UCP** (Universal Control Plane) e o **DTR** (Docker Trusted Registry), bem como suporte da Docker Inc.

A recomendação mínima para a versão Enterprise do Docker EE é:
* 8GB de RAM para nós Managers
* 4GB de RAM para nós Workers
* 2vCPUs para nós Managers
* 10GB de espaço em disco livre para a partição `/var` em nós Managers (Minimo de 6GB Recomendado)
* 500MB de espaço em disco livre para a partição `/var` em nós workers

A recomendação para ambientes de produção do Docker EE é:
* 16GB de RAM para nós Managers
* 4vCPUs para nós Managers
* 25 a 100GB de espaço livre em disco.

### Vantagens do Docker

* Portabilidade – o principal atrativo do Docker é sua portabilidade. Ele permite que os usuários criem ou instalem um aplicativo complexo em uma máquina e tenham certeza de que funcionará nele. Os containers do Docker incluem tudo o que um aplicativo precisa com pouca ou nenhuma entrada do usuário.
* Automação – com a ajuda de cron jobs e containers Docker, os usuários podem automatizar seu trabalho facilmente. A automação ajuda os desenvolvedores a evitar tarefas tediosas e repetitivas, além de economizar tempo.
* Comunidade– O Docker tem um canal dedicado no Slack, fórum da comunidade e milhares de colaboradores em sites de desenvolvedores como o StackOverflow. Além disso, existem mais de 9 milhões de imagens de container hospedadas no Docker Hub.

### Desvantagens do Docker

* Velocidade -mesmo que executar um aplicativo por meio de um container do Docker seja mais rápido do que em uma máquina virtual, ainda é consideravelmente mais lento do que executar aplicativos nativamente em um servidor físico.
* Difícil de usar - O Docker não se destina a executar aplicativos que exijam uma interface gráfica do usuário (GUI). Isso significa que os usuários precisam estar familiarizados com a linha de comando e realizar todas as ações nela. A curva de aprendizado íngreme, as advertências específicas do sistema operacional e as atualizações frequentes tornam o domínio do Docker um desafio. Mesmo que você sinta que conhece o Docker de dentro para fora, ainda há uma orquestração a ser considerada, adicionando outro nível de complexidade.
* Segurança - O Docker é executado no sistema operacional do host. Isso significa que qualquer software malicioso oculto em containers pode chegar à máquina host.

## Instalação

Iremos instalar o Docker em máquinas virtuais para que possamos facilitar o estudo, para isto utilizaremos uma solução chamada **Vagrant** somado ao **Virtualbox**, você pode utilizar a solução de virtualização que preferir, porém eu indico que você siga exatamente como listado no curso porque caso você precise de suporte eu possa lhe ajudar.

> Lembre-se de habilitar a virtualização Intel VT-x ou AMD SVM na UEFI/BIOS.

### Instalando o Vagrant e Virtualbox 

Para instalar o Virtualbox siga os passos:

1. Acesse a página de [Downloads do Virtualbox](https://www.virtualbox.org/wiki/Downloads) e faça o download da versão coorespondente ao seu sistema operacional.
2. Execute a instalação do pacote do Virtualbox.
2.1. Para Linux execute o programa de instalação de pacotes (`sudo dpkg -i <pacote>.deb` para sistemas debian-like ou `sudo rpm -i <pacote>.rpm`)
2.2. Para Windows, clique sob o instalador e avance até o final da instalação.
2.3. Para MacOS, clique sob o instalador e avance até o final da instalação.

### Instalação virtual box pelo repositório
```bash
sudo apt install curl wget gnupg2 lsb-release -y
$ curl -fsSL https://www.virtualbox.org/download/oracle_vbox_2016.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/vbox.gpg
$ curl -fsSL https://www.virtualbox.org/download/oracle_vbox.asc|sudo gpg --dearmor -o /etc/apt/trusted.gpg.d/oracle_vbox.gpg
$ echo "deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian $(lsb_release -sc) contrib" | sudo tee /etc/apt/sources.list.d/virtualbox.list
$ sudo apt update
$ sudo apt install -y linux-headers-$(uname -r) dkms
$ sudo apt install virtualbox-7.0 -y
$ sudo usermod -aG vboxusers $USER
$ newgrp vboxusers
$ wget https://download.virtualbox.org/virtualbox/7.0.10/Oracle_VM_VirtualBox_Extension_Pack-7.0.10.vbox-extpack
$ sudo vboxmanage extpack install Oracle_VM_VirtualBox_Extension_Pack-7.0.10.vbox-extpack
```

Para o ubuntu 24 execute apenas os comandos abaixo:
```bash
sudo apt update
sudo apt upgrade
sudo apt install virtualbox
sudo apt install virtualbox-ext-pack
```

### Para Instalar o vagrant siga os passos:

1. Acesse a página de [Downloads do Vagrant](https://www.vagrantup.com/downloads.html) e faça o download da versão correspondente ao seu sistema operacional.
2. Execute a instalação do pacote do vagrant.
2.1. Para Linux execute o programa de instalação de pacotes (`sudo dpkg -i <pacote>.deb` para sistemas debian-like ou `sudo rpm -i <pacote>.rpm`)

### Introdução ao vagrant 

Vagrant é um software de código aberto para criar e manter ambientes de desenvolvimento virtuais portáteis, utilizando VirtualBox, KVM, Hyper-V, Docker containers, VMware, e AWS. Ele tenta simplificar a gerência de configuração de software das virtualizações para aumentar a produtividade do desenvolvimento.

### Instalação do vagrant base debian

1. wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
2. echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
3. sudo apt update && sudo apt install vagrant

>Para mais detalhes sobre o vagrant veja o link:
https://www.youtube.com/watch?v=yW-2dFpL2-k

2.2. Para Windows, clique sob o instalador e avance até o final da instalação.
2.3. Para MacOS, clique sob o instalador e avance até o final da instalação.
3. Após a instalação abra um terminal ou um prompt de comando e execute o comando `vagrant --version` para verificar se o pacote foi instalado com sucesso.

### Preparando o Ambiente

Após instalar o **Vagrant** e o **Virtualbox**, podemos criar um diretório com um arquivo Vagrantfile.

> O Vagrantfile é o arquivo do **Vagrant** responsável por criar nossa infraestrutura.

Caso queira utilizar os arquivos mais atualizados, basta clonar o repositório: https://github.com/caiodelgadonew/docker-dca


```bash
paulo@dev:docker-dca$ pwd
/home/paulo/projetos/devop/docker-dca
$ vim Vagrantfile
```

Adicione o conteúdo ao arquivo Vagrantfile

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby  :

machines = {
  "master"   => {"memory" => "2048", "cpu" => "2", "ip" => "100", "image" => "ubuntu/jammy64"},
  "node01"   => {"memory" => "1024", "cpu" => "2", "ip" => "110", "image" => "ubuntu/jammy64"},
  "node02"   => {"memory" => "1024", "cpu" => "2", "ip" => "120", "image" => "rockylinux/8"},
  "registry" => {"memory" => "2048", "cpu" => "2", "ip" => "200", "image" => "ubuntu/jammy64"}
}

Vagrant.configure("2") do |config|

  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}.docker-dca.example"
      machine.vm.network "private_network", ip: "10.20.20.#{conf["ip"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
        vb.customize ["modifyvm", :id, "--groups", "/Docker-DCA"]
      end
      machine.vm.provision "shell", path: "provision.sh"
      machine.vm.provision "shell", inline: "hostnamectl set-hostname #{name}.docker-dca.example"
    end
  end
end
```

Adicione também as seguintes entradas ao arquivo `hosts` da sua máquina.

```bash
# Docker
192.168.200.10  master.docker.example
192.168.200.21  node01.docker.example
192.168.200.22  node02.docker.example
192.168.200.50  registry.docker.example
```

> Em máquinas **Linux** e **MacOS** o arquivo fica localizado em `/etc/hosts`
> Em máquinas **Windows** o arquivo fica localizado em `C:\Windows\System32\drivers\etc\hosts`

## Garantindo as chaves

```bash
paulo@dev:dcker-dca$ cd files/
paulo@dev:files$ ls
key  key.pub
paulo@dev:files$ rm *
paulo@dev:files$ ssh-keygen -q -t rsa -f key -N ''
paulo@dev:files$ ls
key  key.pub
```

## Adicionando as imagens
* vagrant box add --provider virtualbox ubuntu/jammy64 
> paulo@dev:dcker-dca$ vagrant box add --provider virtualbox ubuntu/jammy64 
==> box: Loading metadata for box 'ubuntu/jammy64'
    box: URL: https://vagrantcloud.com/api/v2/vagrant/ubuntu/jammy64
==> box: Adding box 'ubuntu/jammy64' (v20240426.0.0) for provider: virtualbox
    box: Downloading: https://vagrantcloud.com/ubuntu/boxes/jammy64/versions/20240426.0.0/providers/virtualbox/unknown/vagrant.box
Download redirected to host: cloud-images.ubuntu.com
progress: 88% (Rate: 1.2m/s Estimated time remaining 0:5:22)
Download redirected to host: cloud-images.ubuntu.com
==> box: Successfully added box 'ubuntu/jammy64' (v20240426.0.0) for 'virtualbox'!

* vagrant box add --provider virtualbox rockylinux/8 
> paulo@dev:dcker-dca$ vagrant box add --provider virtualbox rockylinux/9
==> box: Loading metadata for box 'rockylinux/9'
    box: URL: https://vagrantcloud.com/api/v2/vagrant/rockylinux/9
==> box: Adding box 'rockylinux/9' (v4.0.0) for provider: virtualbox (amd64)
    box: Downloading: https://vagrantcloud.com/rockylinux/boxes/9/versions/4.0.0/providers/virtualbox/amd64/vagrant.box
Download redirected to host: dl.rockylinux.org
    box: Calculating and comparing box checksum...
==> box: Successfully added box 'rockylinux/9' (v4.0.0) for 'virtualbox (amd64)'!
progress: 23% (Rate: 2146k/s Estimated time remaining 0:6:22)
    box: Calculating and comparing box checksum...
==> box: Successfully added box 'rockylinux/8' (v9.0.0) for 'virtualbox (amd64)'!

Para não haver problemas de rede com o laboratóro crie o seguinte caminho: `sudo vim /etc/vbox/networks.conf` e cole o conteúdo abaixo.
* 10.0.0.0/8 192.168.0.0/16
* 2001::/64

## Subindo o ambiente

Para criar o ambiente do laboratório, execute o comando `vagrant up`, e o vagrant irá criar todas as máquinas virtuais bem como configurar os hostnames e endereços IP's

Vamos subir as maquinas por etapas. 
Execute o comando `vagrant up node01` e `vagrant up node02`para criar nossa infraestrutura. Vamos subir as maquinas ubunut e rocklinux, para os nossos exemplos. O comando `vagrant --version` é usado para testar e ver a versão atual no sistema.

```
paulo@dev:dcker-dca$ pwd
/home/paulo/projetos/devop/dcker-dca
paulo@dev:dcker-dca$ ls
files   LICENSE  'pics&md'   provision.sh   README.md   Vagrantfile
paulo@dev:dcker-dca$ vagrant --version
Vagrant 2.4.1
```

paulo@dev:docker-dca$ pwd
/home/paulo/projetos/devop/dcker-dca
paulo@dev:dcker-dca$ vagrant up node01
paulo@dev:dcker-dca$ vagrant up node02   

## Acesso direto as maquinas
user: vagrant
pass: vagrant

### Ver o estatus das maquinas
```bash
paulo@dev:docker-dca$ vagrant status
Current machine states:

master                    not created (virtualbox)
node01                    running (virtualbox)
node02                    running (virtualbox)
registry                  not created (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

Para se conectar as máquinas utilize o comando `vagrant ssh <host>` informando o nome do host a ser conectado, lembre-se de estar dentro da pasta com o Vagrantfile.

xala@dev:docker-dca$ vagrant ssh node01
Para desligar as máquinas execute o comando `vagrant halt`.
Para destruir o ambiente execute o comando `vagrant destroy`.

### Principais comandos do vagrant

Antes de prosseguir com as primeiras configurações, é importante conhecer alguns dos principais comandos que nos auxiliarão no uso do Vagrant. São eles:

vagrant version - Testa a integridade da instalação no sistema operacional, e mostra a versão atual do vagrant
vagrant init ---- Inicia um projeto Vagrant no diretório atual.
vagrant status -- Exibe o estado vigente da máquina virtual.
vagrant up ------ Liga a máquina virtual do ambiente.
vagrant ssh ----- Esse comando permite o acesso remoto ssh a máquina virtual.
vagrant halt ---- Desliga a máquina, ou todas as maquinas de uma vez
vagrant destroy - Remove a máquina virtual por completo.
vagrant reload -- Com o reload é possível atualizar a máquina após qualquer alteração feita no aquivo de configuração, expansão de memória por exemplo.
autocomplete ---- manages autocomplete installation on host

> Caso você queira saber mais sobre Vagrant veja o post no blog onde ele ensina como utilizar o Vagrant para subir os laboratórios de estudo, para acessar basta clicar em [Vagrant-101](https://caiodelgado.dev/vagrant-101)

## Namespaces e Cgroups

O Docker utiliza de recursos do linux como por exemplo namespaces, cgroups dentre vários outros que iremos falar futuramente para isolar os containers que serão executados.

https://etcd.dev/2021/09/20/containers-o-que-sao-namespaces-e-cgroups/

### Namespaces 

Os namespaces fazem parte do kernel do Linux desde 2002 (introduzido na versão 2.4.19 do kernel), é uma feature que permite criar e lidar com diversos contextos em um mesmo sistema, vendo propriedades globais diferentes e isoladas em cada contexto. Basicamente, os namespaces são responsáveis por gerar o isolamento de grupos de processos em seu nível lógico, como o gerenciamento de usuários, rede, etc., garantido que o container não enxergue os processos do host e vice-versa. Logo, ao criar um container, são criados namespaces como PID (Process ID) para isolar processos, NET (Network) para controlar e isolar as redes de cada container, IPC (Inter Process Communication) que permite a comunicação entre processos, etc.

O uso de containers oferece um ambiente isolado que parece uma VM completa. No entanto, não é uma VM - é um processo em execução em um servidor em algum lugar. Se por exemplo forem iniciados dois containers, haverá dois processos em execução em um único servidor em algum lugar - mas eles estão isolados um do outro.

![Namespaces](resources/01namespaces.png)
* **PID**: Process ID
* **MNT**: Mount Points O namespace de montagem é usado para isolar os pontos de montagem de forma que os processos em diferentes namespaces não possam visualizar os arquivos uns dos outros. Se você estiver familiarizado com o comando chroot, ele funciona de forma semelhante. 
* **IPC**: Comunicação Inter Processos
* **UTS**: Unix Timesharing System (Kernel e Identificadores)
* **NET**: Networking Cada computador conectado a uma rede (como a Internet) requer um endereço IP. Este é um número exclusivo que permite que os computadores se comuniquem com eficácia.

### cgroups

![cgroups](resources/01cgroups.png)

Cgroups são basicamente a tecnologia que nos permite definir limites de uso de recursos em processos Linux. Muitos recursos podem ser limitados pelo uso de Cgroups. Os cgroups fornecem os seguintes recursos:

* Limites de recursos: Você pode configurar um cgroup para limitar quanto de um determinado recurso (memória ou CPU, por exemplo) um processo pode usar.
* Priorização: Você pode controlar quanto de um recurso (CPU, disco ou rede) um processo pode usar em comparação com processos em outro cgroup quando há contenção de recursos.
* Contabilidade: os limites de recursos são monitorados e relatados no nível do cgroup.
* Controle: Você pode alterar o status (congelado, interrompido ou reiniciado) de todos os processos em um cgroup com um único comando.

Basicamente, você usa cgroups para controlar quanto de um determinado recurso-chave (CPU, memória, rede e I/O de disco) pode ser acessado ou usado por um processo ou conjunto de processos. Os cgroups são um componente-chave dos containers porque geralmente há vários processos em execução em um container que precisam ser controlados juntos. Em um ambiente Kubernetes, por exemplo, os cgroups podem ser utilizados para implementar solicitações e limites de recursos e classes de QoS correspondentes no nível do pod.

* **cpu**   : Divisão de CPU por containers.
* **cpuset**: CPU Masks, para limitar threads
* **memory**: Memória
* **device**: Dispositivos 

Os containers trabalham com cgroups (Control Groups) que fazem isolamento dos recursos físicos da máquina. Em geral os cgroups podem ser utilizados para controlar estes recursos tais como limites e reserva de CPU, limites e reserva de memória, dispositivos, etc…

**Namespaces** e **cgroups** são os blocos de construção para containers e aplicativos modernos. Ter uma compreensão de como eles funcionam é importante à medida que refatoramos os aplicativos para arquiteturas mais modernas. Os namespaces fornecem isolamento de recursos do sistema e os cgroups permitem um controle refinado e a aplicação de limites para esses recursos. Os containers não são a única maneira de usar namespaces e cgroups. Os namespaces e as interfaces cgroup são incorporados ao kernel do Linux, o que significa que outros aplicativos podem usá-los para fornecer separação e restrições de recursos.

## Instalação do Docker 

Existem duas maneiras de instalar o Docker
* 1ª - Script de conveniência --> Para ambientes de estudos e testes | Não recomendado para ambientes de produção.
"curl -fsSL https://get.docker.com -o get-docker.sh" --> Esse script instala o docker com todas as configrações padrão. Ou pode ser visto neste endereço: **https://get.docker.com/**

```bash
vagrant@node01:~$ curl -fsSL https://get.docker.com -o get-docker.sh
vagrant@node01:~$ ls -l
total 24
-rw-rw-r-- 1 vagrant vagrant 21927 Jan 28 18:06 get-docker.sh
```

* 2ª - Repositório manual ------> Método oficial e cobrado em para prova.

Iremos efetuar a instalação da maneira tradicional nas máquinas `master` e `node02` e com o script de conveniência nas máquinas `node01` e `registry`.

### Instalando Docker através do script de Conveniência.

Os passos a seguir devem ser executados nas máquinas `master` e, não esqueça de abrir um terminal novo para cada máquina e executar o comando `vagrant ssh <host>`

A Docker disponibiliza um script de conveniência, que trata-se de uma maneira simples e rápida para instalar o Docker para ambientes de desenvolvimento, este script faz a validação da distribuição Linux bem como instala os pacotes necessários para o funcionamento do Docker. 

Para instalar o Docker através do script de conveniência basta executar o comando:

```bash
$ sudo curl -fsSL https://get.docker.com | bash
```

Nos sistemas RHEL like, precisamos habilitar e iniciar o serviço após a instalação do mesmo

```bash
$ sudo systemctl enable docker
$ sudo systemctl start docker
```

Após a conclusão da instalação, podemos configurar agora nosso usuário para fazer parte do grupo `docker`, isso garantirá que possamos executar os comandos do docker sem a necessidade de elevar os privilégios.

```bash
sudo usermod -aG docker $USER
```

Vamos também instalar o recurso de `Bash Completion` através do comando:

```bash
$ sudo curl https://raw.githubusercontent.com/docker/machine/v0.16.0/contrib/completion/bash/docker-machine.bash -o /etc/bash_completion.d/docker-machine
```

### Teste de Execução

Para garantirmos que o docker foi instalado corretamente e está funcional, podemos rodar nosso primeiro container e verificar o retorno na tela.

```bash
$ docker container run --rm -it hello-world
```

### Instalando Docker no Ubuntu

Primeiramente vamos acessar a máquina `node01`

```bash
$ cd ~/docker
$ vagrant ssh node01
```

Uma vez conectado na máquina docker, execute os seguintes comandos:

## Instalação em distribuição base debian
### Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

### Add the repository to Apt sources:
sudo echo  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo docker run hello-world

```
vagrant@node01:~$ pwd
/home/vagrant
vagrant@node01:~$ sudo apt-get update  
vagrant@node01:~$ clear
vagrant@node01:~$ sudo apt-get install ca-certificates curl
vagrant@node01:~$ sudo chmod a+r /etc/apt/keyrings/docker.asc
vagrant@node01:~$ sudo echo  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
vagrant@node01:~$ cat /etc/apt/sources.list.d/docker.list 
deb [arch=amd64 signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu bionic stable
vagrant@node01:~$ sudo apt-get update                    
vagrant@node01:~$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
vagrant@node01:~$ 
```

```bash
$ sudo apt update
$ sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common bash-completion -y
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo echo  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null  
$ sudo apt update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Após a conclusão da instalação, podemos configurar agora nosso usuário para fazer parte do grupo `docker`, isso garantirá que possamos executar os comandos do docker sem a necessidade de elevar os privilégios.

```bash
$ sudo usermod -aG docker $USER
```

### Testando a instalação do docker!!

Vamos executar os comandos de testes

```bash
vagrant@node01:~$ docker system info 
Client: Docker Engine - Community
 Version:    24.0.2
 Context:    default
 Debug Mode: false
 Plugins:
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.10.5
    Path:     /usr/libexec/docker/cli-plugins/docker-buildx
  compose: Docker Compose (Docker Inc.)
    Version:  v2.18.1
    Path:     /usr/libexec/docker/cli-plugins/docker-compose

```
**As linhas acima são apenas uma amostra de que tudo está devidamente instalado**

```bash
vagrant@node01:~$ docker container run -rm -it hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete 
Digest: sha256:6352af1ab4ba4b138648f8ee88e63331aae519946d3b67dae50c313c6fc8200f
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

Vamos também instalar o recurso de `Bash Completion` através do comando:

```bash
$ sudo curl https://raw.githubusercontent.com/docker/machine/v0.16.0/contrib/completion/bash/docker-machine.bash -o /etc/bash_completion.d/docker-machine
```

Sáia do terminal e inicie uma nova sessão e o usuário já poderá executar o comando como super user.
```bash
$ exit
$ vagrant ssh master
```

### Instalando Docker no CentOS

Abra um novo terminal e acesse a máquina `node02`

```bash
$ cd ~/docker
$ vagrant ssh node02
```

Uma vez conectado na máquina docker, execute os seguintes comandos:

```bash
sudo yum install -y yum-utils curl epel-release vim bash-completion -y
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
$ sudo yum install docker-ce docker-ce-cli containerd.io
```
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

Nos sistemas RHEL like, precisamos habilitar e iniciar o serviço após a instalação do mesmo.

```bash
$ sudo systemctl enable docker
$ sudo systemctl start docker
```

Após a conclusão da instalação, podemos configurar agora nosso usuário para fazer parte do grupo `docker`, isso garantirá que possamos executar os comandos do docker sem a necessidade de elevar os privilégios.

```bash
$ sudo usermod -aG docker $USER
```

Vamos também instalar o recurso de `Bash Completion` através do comando:

```bash
$ sudo curl https://raw.githubusercontent.com/docker/machine/v0.16.0/contrib/completion/bash/docker-machine.bash -o /etc/bash_completion.d/docker-machine
```

Saia do terminal e inicie uma nova sessão e o usuário já poderá executar o comando como super user.
```bash
$ exit
$ vagrant ssh node02
```
## Componentes

Agora que rodamos nosso primeiro container, precisamos entender alguns componentes básicos da sua arquitetura e seu funcionamento.

Ao executar o container com a imagem `hello-world` o Docker fez os seguintes passos:
1. O `Docker Client` se comunicou com o `Docker Daemon`.
2. O `Docker Daemon` fez o download da imagem `hello-world` no Docker Hub.
3. O `Docker Daemon` criou um novo container, através da imagem que rodou o executável que produz o texto que vimos no terminal.
4. O `Docker Daemon` enviou o texto diretamente para o `Docker Client` que enviou para nosso terminal.
5. `--rm` é de remove, `-it` é de interativo e tty. Então ele executa o container e roda de movo interativo e no terminal depois remove.

![Componentes](resources/01componentes.png)

### Docker Client

O Docker Client é o pacote `docker-ce-cli` ele fornece os comandos do lado do cliente, como por exemplo o comando `docker container run`, que irá interagir com o Docker Daemon

### Docker Daemon 

O Docker Daemon é o pacote `docker-ce` ele é o servidor propriamente dito, que receberá os comandos através do Docker Client e fornecerá os recursos de virtualização a nível de sistema operacional.

### Docker Registry

O Docker Registry é o local de armazenamento de imagens Docker, normalmente o Docker hub, de onde o Docker Daemon receberá as imagens a serem executadas no processo de criação de um container.

## Comandos Essenciais

Iremos agora aprender alguns comandos essenciais do Docker.

O primeiro passo para entendermos os comandos do docker é visualizar sua lista de comandos, iremos falar dos seguintes comandos de gerenciamento ao longo desse material:

* `docker container`
* `docker image`
* `docker network`
* `docker system`
* `docker volume`

Basta rodar o comando `docker help` para termos a ajuda do docker e os principais comandos.

```bash
vagrant@node01:~$ docker help

Usage:  docker [OPTIONS] COMMAND

A self-sufficient runtime for containers

Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  pull        Download an image from a registry
  push        Upload an image to a registry
  images      List images
  login       Log in to a registry
  logout      Log out from a registry
  search      Search Docker Hub for images
  version     Show the Docker version information
  info        Display system-wide information
```

Para cada comando de gerenciamento acima, temos diversos subcomandos a serem executados, muitos deles são parecidos com comandos Linux como por exemplo `ls`, `rm`, dentre outros assim como no exemplo acima.

Antigamente o comando utilizado para listar containers era o comando `docker ps` que ainda existe na documentação, porém é indicado que seja utilizado o novo comando `docker container ls`.

```bash
:~$ docker container ls -a
CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                      PORTS     NAMES
91a9694e7362   hello-world   "/hello"   15 seconds ago   Exited (0) 13 seconds ago             xenodochial_mahavira
26b3db84b099   hello-world   "/hello"   41 minutes ago   Exited (0) 41 minutes ago             funny_benz
```
> O comando, ps é o abreviamento de Process Status enquanto ls é o abreviamento de List, que é a nova sintaxe de consulta no docker.

Existem diversos outros comandos que iremos ver ao longo do curso.

### Executando comandos

Antes de executar os comandos do docker, vamos conectar na máquina `node01`.

```bash
vagrant ssh node01
``` 

Para visualizar informações do ambiente, podemos utilizar o comando **docker system info** o qual exibirá informações do Docker como versão, quantidade de containers em execução, storage drivers, entre outros.
```bash
docker system info
docker info
```
_Os comandos listados acima são equivalentes._

Para listar containers, imagens, redes e volumes no docker, utilizamos o comando **docker** \<comando\> **ls**
```bash
docker container ls
docker image ls
docker network ls
docker volume ls
```
* **docker container ls** - lista os containers
* **docker image ls** - lista as imagens
* **docker network ls** - lista as redes
* **docker volume ls** - lista os volumes

Para pesquisar por uma imagem, utilizamos o comando **docker search**
```bash
vagrant@node01:~$ docker search rockylinux
NAME                            DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
rockylinux                      The official build of Rocky Linux.              226       [OK]       
rockylinux/rockylinux                                                           67                   
kasmweb/rockylinux-9-desktop    Rocky Linux 9 desktop for Kasm Workspaces   
```

Para fazer o download da imagem utilizamos o comando **docker image pull**
```bash
vagrant@node01:~$ docker pull debian
Using default tag: latest
latest: Pulling from library/debian
71215d55680c: Pull complete 
Digest: sha256:e97ee92bf1e11a2de654e9f3da827d8dce32b54e0490ac83bfc65c8706568116
Status: Downloaded newer image for debian:latest
docker.io/library/debian:latest
```

```bash
vagrant@node01:~$ docker pull rockylinux/rockylinux
Using default tag: latest
latest: Pulling from rockylinux/rockylinux
71cc2ddb2ecf: Pull complete 
Digest: sha256:fc370d748f4cd1e6ac3d1b6460fb82201897fa15a16f43e947940df5aca1a56e
Status: Downloaded newer image for rockylinux/rockylinux:latest
docker.io/rockylinux/rockylinux:latest
```

Podemos ver as imagens com o comando abaixo
```bash
vagrant@node01:~$ docker image ls 
REPOSITORY              TAG       IMAGE ID       CREATED         SIZE
debian                  latest    c978d997d5fe   2 weeks ago     117MB
hello-world             latest    d2c94e258dcb   11 months ago   13.3kB
rockylinux/rockylinux   latest    523ffac7fb2e   21 months ago   196MB
```

Para executar um container, utilizamos o comando **docker container run**
```bash
vagrant@node01:~$ docker container run -dit --name debian1 --hostname c1 debian
09eeee47fc46d44d03ecdf25476d53ddf1f69c6a6d08da756e8dce553ba5e01d

```
**Descrição do comando:**
* **docker container run  (...) debian** - Executa um container docker, sendo o último parâmetro o nome da imagem a ser utilizada  
* **-dit** - Executa um container como processo (**d** = Detached), habilitando a interação com o container (**i** = Interactive) e disponibiliza um pseudo-TTY(**t** = TTY)
* **--name** - Define o nome do container
* **--hostname** - Define o hostname do container

Agora que temos nosso primeiro container em execução, podemos listar os containers (**docker container ls**) e conectar ao mesmo através do comando **docker container attach**

```bash
vagrant@node01:~$ docker container ls 
CONTAINER ID   IMAGE     COMMAND   CREATED          STATUS          PORTS     NAMES
09eeee47fc46   debian    "bash"    55 seconds ago   Up 54 seconds             debian1
vagrant@node01:~$ docker container attach debian1 

root@c1:/# cat /etc/os-release 
PRETTY_NAME="Debian GNU/Linux 12 (bookworm)"
NAME="Debian GNU/Linux"
VERSION_ID="12"
VERSION="12 (bookworm)"
VERSION_CODENAME=bookworm
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
root@c1:/# 
```

_Note que ao se conectar ao container a **PS1** será modificada para `root@c1:/#` ._

Execute alguns comandos no container:
```bash
ip -c a
hostname
cat /etc/hosts
exit
```

```bash
root@c1:/# ip -c a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
7: eth0@if8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:11:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.17.0.2/16 brd 172.17.255.255 scope global eth0
       valid_lft forever preferred_lft forever
root@c1:/# hostname
c1
root@c1:/# cat /etc/hosts
127.0.0.1	localhost
::1	localhost ip6-localhost ip6-loopback
fe00::0	ip6-localnet
ff00::0	ip6-mcastprefix
ff02::1	ip6-allnodes
ff02::2	ip6-allrouters
172.17.0.2	c1
root@c1:/# exit
exit
```
Liste novamente os containers
```bash
vagrant@node01:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
vagrant@node01:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS                      PORTS     NAMES
09eeee47fc46   debian    "bash"    6 minutes ago   Exited (0) 29 seconds ago             debian1
```

_Note que agora o container está parado, isto aconteceu pois o processo principal do container recebeu um return code diferente de 0_

Podemos listar apenas o ID dos containers
```bash
vagrant@node01:~$ docker container ls -aq
09eeee47fc46
```

Inicie novamente o container e conecte-se ao mesmo
```bash
docker container start debian1
docker container attach debian1
```

```bash
vagrant@node01:~$ docker container start debian1 
debian1
vagrant@node01:~$ docker container attach debian1 
root@c1:/# 
```

_O comando **docker container start** inicia um container parado, o comando **docker container stop** para um container que esteja em execução_

Utilize a sequencia de teclas **_\<CTRL\> + \<P\> + \<Q\>_** para se desconectar do container sem que ele seja parado. Este comando é chamado de _Read escape sequence_.

```bash
<CTRL> + <P> + <Q>
root@c1:/# read escape sequence
vagrant@node01:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED         STATUS              PORTS     NAMES
09eeee47fc46   debian    "bash"    9 minutes ago   Up About a minute             debian1
```
_Note que agora o container ainda está com estatus **Up** oq eu significa que está em execução._

Para verificar os logs do container utilizamos o comando **docker container logs**
```bash
vant@node01:~$ docker container logs debian1
root@c1:/# docke container log debian1
bash: docke: command not found
root@c1:/# docker container log debian1
bash: docker: command not found
root@c1:/# exit
exit
```

Pare e remova o container, após isto verifique os containers existentes
```bash
docker container stop debian1
docker container rm debian1
docker container ls -a
```

```
vagrant@node01:~$ docker container stop debian1 
debian1
vagrant@node01:~$ docker container rm debian1 
debian1
vagrant@node01:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
vagrant@node01:~$ 
```

_Podemos utilizar o parâmetro **-f** no comando **docker container rm** para que o container seja removido mesmo que esteja sendo executado_

Execute um novo container
```bash
vagrant@node01:~$ docker container run -dit --name c1 --hostname server debian
2db8b19f544f67b27f1f7fce7035ea66f33109e2c2861bd921eb96c68568d911
vagrant@node01:~$ docker container ls
CONTAINER ID   IMAGE     COMMAND   CREATED          STATUS         PORTS     NAMES
2db8b19f544f   debian    "bash"    11 seconds ago   Up 9 seconds             c1
```

Crie um arquivo de teste na pasta atual para enviar ao container c1
```bash
vagrant@node01:~$ echo "Arquivo de teste docker" > /tmp/arquivo.txt
vagrant@node01:~$ docker container cp /tmp/arquivo.txt c1:tmp
Successfully copied 2.05kB to c1:tmp
```

_O comando **docker container cp** copia um arquivo da maquina host para o container ou vice-versa._

Verifique se o arquivo existe dentro do container através do comando **exec**
```bash
vagrant@node01:~$ docker container exec c1 ls -l /tmp
total 4
-rw-rw-r-- 1 1000 1000 24 Mar 24 12:57 arquivo.txt
vagrant@node01:~$ docker container exec c1 cat /tmp/arquivo
Arquivo de teste docker
```

_O comando **docker container exec** executa um comando no container e envia o retorno na saída padrão(STDOUT) da máquina, caso o container não tenha sido iniciado com a opção **-i** o retorno não será mostrado no STDOUT_

Remova o container criado anteriormente
```bash
vagrant@node01:~$ docker container ls -aq
2db8b19f544f
vagrant@node01:~$ docker container rm -f c1
c1
``` 
### script para criar containers

```bash
for i in $(seq 1 10)
> do  
> docker conatainer run -it hello-word
> done
```
> Ou escrever o codigo em apenas uma linha. for i in $(seq 1 10); do docker container run -it hello-world; done

```bash
vagrant@node01:~$ docker container ls -aq
f2bf59d9cdf9
8ac102884338
c35b521b4c45
7f77c81c3cc8
26dbf0eb8321
c861ac1bb753
ecf584884a4b
1d9c126940a2
729d9b9f0e8f
4286159e615c
```

### Apagar todos os containers de uma vez

```bash
vagrant@node01:~$ docker container rm $(docker container ls -aq)
f2bf59d9cdf9
8ac102884338
c35b521b4c45
7f77c81c3cc8
26dbf0eb8321
c861ac1bb753
ecf584884a4b
1d9c126940a2
729d9b9f0e8f
4286159e615c
```

```bash
vagrant@node01:~$ docker container ls -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
vagrant@node01:~$ 
```

### Desligando as maquinas
```bash
xala@dev:docker-dca$ vagrant halt
==> registry: VM not created. Moving on...
==> node02: Attempting graceful shutdown of VM...
==> node01: Attempting graceful shutdown of VM...
==> master: VM not created. Moving on...
````

## Conclusão
Esse material vai abordar o conteúdo official do docker, e com exemplos práticos criado ao longo do nosso material.

### Resumindo a terminologia do Docker

Contêiner: ambiente isolado e leve que pode ter seus próprios processadores, interfaces de rede, etc., mas compartilham o mesmo kernel do sistema operacional. Criado a partir de uma versão de imagem específica.

Imagem: uma imagem é basicamente um pacote executável que possui tudo o que é necessário para executar aplicativos, o que inclui um arquivo de configuração, variáveis ​​de ambiente, tempo de execução e bibliotecas.

Dockerfile: contém todas as instruções para criar uma imagem do Docker. É basicamente um arquivo de texto simples com instruções para construir uma imagem. Você também pode se referir a isso como a automação da criação de imagens do Docker.

Tag: versão de uma imagem. Cada imagem terá uma tag.

Docker Hub: repositório de imagens onde podemos encontrar diferentes tipos de imagens.

Docker Engine: o sistema que permite criar e executar contêineres do Docker.

Docker Registry: o registro do Docker é uma solução que armazena suas imagens do Docker. Este serviço é responsável por hospedar e distribuir as imagens. O registro padrão é o Docker Hub.

Docker CLI: interface de linha de comando (CLI) que permite à pessoa executar ações interagindo com Docker. Docker é executado em uma arquitetura cliente-servidor, o que significa que clientes Docker podem se conectar a hosts do Docker localmente ou remotamente. Tanto cliente quanto host do Docker (Daemon) podem ser executados no mesmo host, ou podem ser executados em hosts diferentes e se comunicar por meio de soquetes ou de uma API RESTful.

> docker container rm $(docker container ls -aq) --> Apaga e mostra todos os containers.
> docker container ls -aq | xargs docker conatiner rm --> Recebe a entrada e apaga
> docker container rm $(docker container ls -aq) -------> Apaga todos de uma vez.

### Conteúdo Official
Preparação da Máquina (Windows / Linux)
Docker DCA 01 - Instalação e Fundamentos
Docker DCA 02 - Comandos Docker e Imagens
Docker DCA 03 - Docker Images - Melhores Práticas e Multistage Build
Docker DCA 04 - Volumes
Docker DCA 05 - Volume Plugins
Docker DCA 06 - Networking
Docker DCA 07 - Compose (docker-compose)
Docker DCA 08 - Raft Consensus & Docker Swarm
Docker DCA 09 - Docker Swarm - Registry, Services e Tasks
Docker DCA 10 - Docker Swarm - Stacks
Docker DCA 11 - Monitoramento (Prometheus + Node Exporter + Grafana + Cadvisor)
Docker DCA 12 - Tools (PwD, Swarmpit, Portainer, Harbor e Docker Machine)
Docker DCA 13 - Kubernetes
Live   DCA 14 - Enterprise

## Bons estudos!

#### Jogo no docker
docker container run -it -p 8080:8080 pengbai/docker-supermario


