---
layout: post
title: Ativar ZRAM para melhorar o desempenho SWAP
date:   2020-06-12 19:55:26 +0530
categories: Desktop Linux
---

Se você utiliza linux a algum tempo, com certeza, conhece a área de troca, também chamada de SWAP. A partição swap é uma partição dedicada a ser usada quando um sistema utiliza um grande consumo de memória RAM. Quando isto ocorre, as páginas inativas são movidas da RAM para a partição swap.

![zram em uso](/images/zram.png)

O problema da swap é que ela reside em uma unidade muita mais lenta que a RAM, ou seja, seu disco rígido. Então, quando seu sistema começa a usar a S:worried:

O **zRAM** dedica uma parte da memória RAM para servir como espaço de troca. Então você deve estar se perguntando, se a SWAP entra em uso quando a memória RAM está em grande uso, reservar um espaço para isto não vai fazer com que ela entre em uso mais rápido?

Acontece, que os dados armazenados em uma partição zRAM são compactados, para que mais dados possam ser armazenados na RAM. E embora, uma pequena porcentagem do tempo da CPU seja usada para essa compactação, a troca de desempenho geralmente vale a pena. 

O zRAM está disponível em todas as distribuições linux, você precisa apenas ter permissão administrativa (root, ou sudo) para ativá-lo.

## Como ativar o zRAM

O módulo zRAM é controlado pelo systemd, portanto, não há necessidade de colocá-lo no **/etc/fstab**. 

Abra um terminal de comandos e crie o arquivo abaixo:

```bash
sudo nano /etc/modules-load.d/zram.conf
```

Neste arquivo coloque o valor:

```
zram
```

Salve e feche o arquivo.

Crie um segundo arquivo com o comando:

```bash
sudo nano /etc/modprobe.d/zram.conf
```

Neste arquivo, coloque os valores:

```
options zram num_devices=1
```

Salve e feche o arquivo.

Em seguida, precisamos configurar o tamanho da partição zRAM. Crie um novo arquivo com o comando:

```bash
sudo nano /etc/udev/rules.d/99-zram.rules
```

Nesse arquivo, coloque o valor abaixo, colocando a quantidade do tamanho para o zRAM que achar mais adequada a sua necessidade.

```bash
KERNEL=="zram0", ATTR{disksize}="1024M",TAG+="systemd"
```

Salve e feche o arquivo.


## Disabilite sua swap em disco

Acesse o arquivo **/etc/passwd** e desabilite a entrada da sua swap atual. 

Eu aproveitei e formatei a partição que eu tinha a swap.


## Crie um systemd unit

Agora, vamos criar um arquivo unit para o systemd. 

```bash
sudo nano /etc/systemd/system/zram.service
``` 

Coloque o seguinte conteúdo neste arquivo:

```bash
[Unit]
Description=Swap with zram
After=multi-user.target

[Service]
Type=oneshot 
RemainAfterExit=true
ExecStartPre=/sbin/mkswap /dev/zram0
ExecStart=/sbin/swapon /dev/zram0
ExecStop=/sbin/swapoff /dev/zram0

[Install]
WantedBy=multi-user.target
```

Habilite a unit com o comando:

```bash
sudo systemctl enable zram
```

Reinicie seu computador.

Verifique sua zram em uso:

``` 
cat /proc/swaps
```

![zram](/images/zram2.png)


## Uso só em 90%
Para que a swap só entre em uso quando o sistema atingir 90% da RAM disponível. Eu edito o arquivo **/etc/sysctl.conf** colocando os valor:

```bash
vm.swappiness=10
```


## Meu vídeo sobre desempenho no Ubuntu
Aproveite e assista lá no meu canal, meu vídeo sobre como melhorar o desempenho do ubuntu:

[![desempenho](http://img.youtube.com/vi/wA1BIJYZbXI/0.jpg)](http://www.youtube.com/watch?v=wA1BIJYZbXI "desempenho"){:target="_blank"}

## E ai, curtiu? 
Deixe seu comentário, ele é muito importante para o desenvolvimento de um blog cada vez melhor.

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)