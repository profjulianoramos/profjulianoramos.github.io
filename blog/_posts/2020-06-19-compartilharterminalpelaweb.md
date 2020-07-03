---
layout: post
title: Compartilhe seu terminal pela web
date:   2020-06-19 14:30:00 +0530
categories: desktop linux
---

Muitas vezes você pode desejar compartilhar seu terminal para que alguém o ajude na solução de um problema. Se você quer fazer isto de uma forma rápida, sem depender de softwares como Teamviewer, anydesk e etc... E também, deixar a sessão apenas leitura para quem visualiza, conheça o **Streamhut**.

![remote](/images/remote.png)


### O que é o Streamhut
O Streamhut é um serviço da WEB que permite à você compartilhar seu terminal em tempo real, sem nenhum software adicional. Tudo que você precisa é da aplicação **netcat** presente em quase todas as distribuições linux.


Se você não tem o netcat, no Debian/Ubuntu é só correr:

```bash
sudo apt install netcat
```

Os casos mais comuns para você usar o Streamhut:

- Monitorar as saídas de um programa em qualquer dispositivo web
- Depurar logs com sua equipe de trabalho
- Ajudar alguém com dificuldade no shell ou em programação no geral
- Criar uma sessão de treinamento


*O Streamhut ainda está em estágio alfa, por isto, não esta pronto para ambiente de produção.*

### Compartilhar o terminal
Fique tranquilo que ao compartilhar, as pessoas vão apenas assistir sua sessão, não podendo efeturar nenhum comando remoto, ou seja, um acesso apenas leitura.

No terminal digite:

```bash
exec > >(nc stream.ht 1337) 2>&1
```

O serviço vai gerar uma URL aleatória. Copie e compartilhe com quem você desejar.


Para compartilhar apenas uma saída de comando. Execute:

```bash
echo "Muito legal esta ferramenta" | nc stream.ht 1337
```

Monitorar um processo ou programa:

```bash
(sleep 5; watch uptime) | nc stream.ht 1337
```

Neste exemplo, vou monitorar o tempo da máquina. O atraso de 5 segundos é para dar tempo de gerar a URL. 


## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 19/06/2020 - 14:48 - Upload da publicação.
- 19/06/2020 - 14:50 - Arrumei o espaço a mais no comando do nc. 