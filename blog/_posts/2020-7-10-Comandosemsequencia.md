---
layout: post
title: Comandos em sequência no linux
date:   2020-07-10 13:12:08 +0530
categories: Servidor
---

Segue uma dica rápida para quem está iniciando na linha de comando do Linux: Aprenda a executar vários comandos em sequência, em uma única linha.

Você pode executar da seguinte maneira:

```bash
clear; date; ls
```

No exemplo acima os três comandos serão executados. Indiferentemente se algum falhar. Ou seja, quando você usa, ponto e virgula, os comandos vão seguindo, mesmo que algum comando não seja executado corretamente. 


Outra forma, de se executar comandos em sequência é usando: 

```bash
ls /tmp/qualquercoisa.txt && echo $SHELL
```
Neste caso, o segundo comando só é executado se o primeiro tiver sucesso. Como eu não tinha o arquivo **qualquercoisa.txt** o segundo comando não foi executado. 

Para finalizar, temos esta opção:

```
ls /tmp/qualquercoisa.txt || echo $SHELL
```

Neste caso o segundo comando só é executado comando o primeiro falha. Então, como eu não tinha o arquivo **qualquercoisa.txt** o comando ```echo $Shell``` foi executado. Porém se o primeiro comando tivesse sido sucesso, o segundo comando não seria executado.

### Conclusão
Aprender o Shell é um pré-requisito para que você se torne um administrador de sistemas linux. Se você está iniciando no linux, tente realizar suas tarefas (como instalar, remover e atualizar programas) pela linha de comando, evite as aplicações GUI. 

Commit: 2020-07-10 13:12:08 +0530 upload.