---
layout: post
title: Arquivos zip no linux
date:   2020-06-27 13:34:00 +0530
categories: desktop
---


Zip sem sombras de dúvidas é um dos formatos mais conhecidos dos usuários Windows para compactação de arquivos. Seria ao equivalente ao Gzip, que nós do Mundo Linux, tanto utilizamos.

Unzip é um utilitário que está presente em praticamente todas as distribuições de linux.

Mas vamos mostrar a instalação em algumas delas:

Ubuntu / Debian / Mint
```bash
sudo apt-get install unzip
```

Centos / Red Hat
```bash
sudo yum install unzip
```

Fedora
```bash
sudo dnf install unzip
```

Para obter detalhes sobre o unzip utilize:

```bash
unzip -v
```

### Criar um zip de arquivos
A sintaxe é simples:

```bash
zip arquivos.zip arquivo1 arquivo2 arquivo3
```

### Descompactar
Para descompactar, utilize:

```bash
unzip arquivo.zip
```

### Remover um arquivo do zip
Para remover um arquivo presente no zip, você pode fazer:

```bash
zip -d arquivo.zip arquivo1
```

### Adicionar novos arquivo a um zip
Depois de criado um arquivo zip, você pode adicionar mais arquivos a ele, usando:

```bash
zip -u arquivo.zip arquivo4 
```

### Mover um arquivo do zip
Você pode mover (retirar) um arquivo do zip, usando:


```bash
zip -m arquivo.zip arquivo3
```

### "Zipar" um diretório
Para usar o zip de forma recursiva, use a opção -r:

```bash
zip -r arquivo.zip diretório
```

### Excluir arquivos do zip
Para excluir um arquivo do zip, utilize:

```bash
zip -x arquivo.zip arquivo2
```

### Unzip em outro diretório
Para descompactar em um diretório diferente, use:

```bash
unzip arquivo.zip -d /tmp
```
Neste caso, será descompactado em /tmp

### Listar arquivos de um zip
Para listar arquivos de um zip, utilize:

```bash
unzip -l arquivo.zip
```


## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 27/06/2020 - 13:32 - Upload da publicação.
- 27/06/2020 - 13:36 - Alteração do título
