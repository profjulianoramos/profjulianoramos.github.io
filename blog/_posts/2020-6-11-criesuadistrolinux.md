---
layout: post
title: Crie sua distro baseada em Debian
date:   2020-06-11 15:51:23 +0530
categories: Customização personalização 
---

Neste primeiro tutorial sobre este assunto, vamos usar o software LB Build criado pela própria comunidade Debian, para customizar a distro. 

![lbuild](/images/lb.png)



# Pré-requisitos

1.  Debian
2.  Versão atualizada do Live-build
3.  Bash
4.  Internet

## Licença de uso

O linux utiliza a licença GPL, o que permite a qualquer um criar um remaster ou distribuição própria. É necessário preocupar-se com as licenças de software que você irá usar em seu sistema.

## Drivers proprietários

Nunca instale drivers proprietários em seu remaster. Por padrão pode ocorrer diversos erros, sendo assim, o ideal é que o usuário final instale estes drivers caso necessário. 

## Qual Debian utilizar?

É recomendado utilizar a versão **Stable** do Debian. 

## Distribuição ou Remasterização.

Normalmente uma remasterização tem uma finalidade específica para um público específico. Exemplo: Uma distro para sua empresa com as ferramentas de uso padrão. 

Já uma distribuição, tem um público maior (usuário final), neste caso você precisa pesquisar por programas que serão adicionados, personalização de interface, configuração de repositório e etc...

## Live Build

Live-Build é criado pela própria comunidade Debian. Sendo um conjunto de scripts para criar imagens do sistema live.

## O que tem em uma imagem live?

- Imagem do kernel linux - Geralmente chamada de vmlinuz
- Imagem do disco RAM inicial - initrd (O live build cria esta etapa)
- Imagem do sistema (Squashfs) é uma compactação da imagem - Sendo somente leitura.
- Bootlooader - Software para iniciar e selecionar um kernel e outras opções.

## Download e instalação do Debian

Debian - versão mínima (netinstall)

Link direto para download:

<https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-10.3.0-amd64-netinst.iso>

Instalar em uma máquina virtual - Recomendo: Virtualbox. 

Coloca entre 30 e 50GB de HD virtual -  Em rede, coloca em modo bridge - na instalação do Debian, em seleção de software, deixe marcado apenas:

- Utilitário de sistema padrão
- Servidor SSH

Verifique o IP da máquina virtual instalada e para facilitar as ações (como ter opção de copiar e colocar) acesse esta máquina via SSH, exemplo:

```# ssh live@192.168.10.100```

## Repositório adicional

Adicionar em `/etc/apt/sources.list`o repositório:

deb http://ftp.br.debian.org/debian/ buster main contrib non-free

Atualize a lista de repositórios:

```# apt-get update```

## Instalação do live-build

```# apt-get install live-build live-manual live-config schroot```

## Criando o diretório de trabalho

```# mkdir /home/live/live```

Acesse o diretório criado e execute o comando:

```# lb config```

Observe que será criado três diretórios:

- auto
- config
- local

Agora execute o comando `lb build`mas detalhe: 

**Este comando não funciona via SSH por causa do diretório path do chroot.** 

```# lb build```

Este comando vai gerar uma imagem hibrida do sistema. A primeira vez que executamos este comando o processo demora, por que é feito download da imagem no site do debian. 

Quando concluir, você terá algo como : live-image-amd64.hybrid.iso nos seu diretório. 

Você pode copiar esta imagem para seu sistema host e testá-la com o virtualbox. Para puxá-la com o scp, use o comando:

```# scp live-image-amd64.hybrid.iso juliano@192.168.10.40:/tmp```

Você pode testar no virtualbox esta imagem, que vai estar funcionando apenas o modo live. As opções (install e graphical install) ainda não foram habilitadas.

## O diretório cache

A partir de agora não será mais necessário fazer o download de todos os pacotes no site do debian, já que estão informações estão no diretório **cache**. 

Para limpar o projeto anterior e iniciarmos de fato a criação de nossa remasterização, utilize o comando:

```# lb clean```

Este comando vai limpar os arquivos e a imagem hibrida, gerada anteriormente.

## Permitir a instalação do Debian

``` # lb config --debian-installer live```

A configuração fica no arquivo **/config/binary**.

## Permitir a instação em modo gráfico

```# lb config --debian-installer-gui true``` 

No comando abaixo devemos colocar o nome do instalador, referente a distribuição debian que estamos usando. No meu caso:

```lb config --debian-installer-distribution buster```

## Permitir ou não o memtest

O memtest é uma opção para ativar o teste de memória no grub. Uma opção, não muito utiizada que vamos desabilitar:

```lb config --memtest none```

### Finalizar imagem

```# lb clean``` 

``` # lb build```

Observe que o tempo será bem mais rápido do que a primeira vez, já que os arquivos estão em cache, ele somente vai baixar os arquivos do instalador do debian. 

## Definindo os repositórios padrão

Para definir os repositórios que serão padrão na live e após sua instalação, como por exemplo, os repositórios non-free (que contém software proprietário), utilize:

```# lb config --archive-areas "main contrib non-free"```

Para persistir após a instalação:

```# lb config --parent-archive-areas "main contrib non-free"```

Habilitar por padrão o repositório de segurança (security):

```# lb config --security true```

## Comandos essenciais

Definir o tipo de sistema da imagem:

```# lb config --parent-distribution buster``

Habilitar para que os indices sejam atualizados automaticamente (apt-get update):

```lb config --apt-indices true```

Definir o gestor de pacotes padrão:

```lb config --apt apt```

Definir a arquitetura do sistema:

```lb config --architectures amd64```

Definir a imagem que usuaremos na live:

```lb config --binary-images iso-hybrid```

Definir o nome da imagem:

```lb config --image-name remaster```

Definir o autor da imagem:

```lb config --iso-publisher "Juliano <profjulianoramos@gmail.com>"```

Definir um shell interativo durante o processo de compilação, para alguma alteração na imagem live:

```lb config --interactive shell```

## Adicionando interface gráfica

Crie um arquivo de lista para os aplicativos que irá instalar:

```# nano config/package-lists/grafica.list.chroot```

Adicione os nomes dos pacotes. Vamos usar o xfce4:

```
xfce4
xfce4-indicator-plugin
xfce4-power-manager
xfce4-battery-plugin
xfce4-datetime-plugin
xfce4-mount-plugin
xfce4-netload-plugin
xfce4-wavelan-plugin
xfce4-screenshooter
xfce4-sensors-plugin
xfce4-smartbookmark-plugin
xfce4-timer-plugin
xfce4-whiskermenu-plugin
xfce4-goodies
```

Crie outra lista com softwares diversos:

```# nano config/package-lists/diversos.list.chroot```

```
gdebi
file-roller
lsb-release
build-essential
module-assistant
linux-headers-amd64
gedit
vlc
mugshot
ristretto
nemo
unrar-free
rar
file-roller
p7zip
unzip
gnome-system-tools
ssh
net-tools
gnome-calculator
gcc
quota
engrampa
libuser
bash-completion
telnet
evince
pulseaudio-equalizer
cups
hplip
accountsservice
mugshot
apt-transport-https
network-manager
network-manager-gnome
net-tools
```

Execute o comando:

```
lb clean
```

Para limpara as outras configurações e crie a iso :

```
lb build
```


## Ainda existe muito a se fazer
Em um próximo tutorial, vamos abordar, como instalar os pacotes, sem a necessidade de uma lista de repositório, assim como, criar uma personalização global para nossa interface. 

## E ai o que achou?
Curtindo aqui o blog? Deixe seu comentário. 

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)