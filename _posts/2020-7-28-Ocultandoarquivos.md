---
layout: post
title: Ocultando arquivos sem ponto no linux
date:   2020-07-10 13:12:08 +0530
categories: Desktop
---

Você sabia que é possivel ocultar arquivos em seu gerenciador de arquivos (GUI) sem que eles tenham ponto. Aliás, não só arquivos, diretórios também. 

Para fim de teste, vou criar em meu diretório **HOME** o diretório **Ocultos**. 

```bash
mkdir ~/Ocultos
```

Agora, dentro deste diretório, vou criar dois arquivos e um diretório, sem usar o ponto à frente, como somos acostumados, quando criamos arquivos ocultos.

```bash
touch arquivo1
touch arquivo2
mkdir diretorio
```

Para ocultar estes arquivos e o diretório, vou criar um arquivo com o nome **.hidden** e adicionar os nomes deles dentro:

```bash
nano ~/Ocultos/.hidden
arquivo1
arquivo2
diretorio
```

![ocultar](/blog/images/ocultos.gif)


Os arquivos são visiveis com um simples `ls`. Porém no gestor de arquivos eles ficam ocultos. 



Commit: 2020-07-28 19:50:08 +0530 upload da publicação.

