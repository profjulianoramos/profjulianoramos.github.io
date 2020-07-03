---
layout: post
title: Instalando o packet tracer no linux
date:   2020-06-28 15:01:00 +0530
categories: desktop
---

O **Packet Tracer** é um programa educacional gratuito que permite a você simular uma rede de computadores, através de equipamentos e configurações presentes em situações reais. O programa apresenta uma interface gráfica simples, com suportes multimídia (gráfica e sonora) que auxiliam na confecção das simulações.

*Via wikipédia, a enciclopédia livre* 
<https://pt.wikipedia.org/wiki/Packet_Tracer>


![packet tracer linux](/images/packet.png)

### Instalação do packet tracer
Em meus testes a versão 7.2.2 funcionou perfeitamente no Ubuntu 20.04 e no Linux Mint 20. 

Para instalar o packet tracer no linux Mint e Ubuntu faça download neste link:

<https://archive.org/download/packettracer7.2.2ubuntusetup/PacketTracer-7.2.2-ubuntu-setup.run>

Coloque permissão para o arquivo e o execute:

```bash
chmod +x PacketTracer-7.2.2-ubuntu-setup.run
sudo ./PacketTracer-7.2.2-ubuntu-setup.run
```

Prossiga normalmente com o instalador. Ele vai criar um diretório em ```/opt/pt```.

Instale a dependência:

```bash
sudo add-apt-repository ppa:linuxuprising/libpng12
sudo apt update
sudo apt install libpng12-0
```

Agora, execute pelo terminal :

```bash
packettracer 
```


### Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 28/06/2020 - 15:14 - Upload da publicação.
