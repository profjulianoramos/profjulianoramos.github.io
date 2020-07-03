---
layout: post
title: 2 - Certificação LPIC-1 - Preparando o ambiente
date:   2020-06-10 16:57:10 +0530
categories: Certificação lpi
---

Nossa segunda videoaula do curso gratuito preparatório da certificação LPIC-1 prova 101 já está disponível no site. No vídeo agrupo alguns pequenos vídeos, que gravei em dias diferentes, no entanto, estão todos em sequência. O Objetivo do vídeo é criar um laboratório para começarmos os nossos estudos.

## Virtualbox no Windows e no Linux

No Microsoft Windows o processo de instalação é bem simples. Você precisa apenas fazer o download e executar o instalador. Link para download:


<https://download.virtualbox.org/virtualbox/6.1.10/VirtualBox-6.1.10-138449-Win.exe>


No linux (ubuntu, debian) e derivados. Abra um terminal e execute:

```bash
sudo apt-get install virtualbox
```

## O Debian
Utilizaremos em nossa máquina virtual o Debian (somente modo texto), escolhi esta distro como base ao nosso estudo, por quê ela vai executar consumindo 50MB de RAM (somente linha de comando).

Link para download:

<https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-10.4.0-amd64-netinst.iso>


## O Centos
Como a certificação LPIC-1 101-500 exige também conhecimento em .RPM, vamos usar o Centos. 

Link para download:

<http://centos.itsbrasil.net/8.1.1911/isos/x86_64/CentOS-8.1.1911-x86_64-boot.iso>

## Preparando no virtualbox

Abra o virtualbox e clique no botão novo:

![botaonovo](/images/1virtualbox.png)

Coloque o nome da máquina, escolha o tipo de sistema operacional e clique em próximo:

![tipodesistema](/images/2virtualbox.png)

Defina o tamanho da memória RAM. Pode deixar 1024 para a instalação, mas depois, com 300MB roda de boa. 

![memoriaram](/images/3virtualbox.png)


Crie agora o seu disco virtual:

![hd](/images/4virtualbox.png)

Escolha o tipo como **VDI (Virtualbox Disk Image)**. Escolha **Dinamicamente alocado**:

![hdvirtual](/images/5virtualbox.png)

Defina o tamanho do disco:

![virtualbox](/images/6virtualbox.png)

Eu coloquei 50GB, porém, o sistema Debian após instalado, vai usar, cerca de 1,5GB do seu HD real. 

Clique na máquina criada e vá em configurações - Armazenamento e no CD, selecione (Escolher uma imagem de disco):

![imagem](/images/7virtualbox.png)

Aponte para a imagem do Debian que você fez o Download.


## Assista a nossa segunda aula 

[![aula2](http://img.youtube.com/vi/3w5RX7AAjDI/0.jpg)](http://www.youtube.com/watch?v=3w5RX7AAjDI "aula2")

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)