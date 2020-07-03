---
layout: post
title: Aprenda a usar o TMUX
date:   2020-06-10 17:03:36 +0530
categories: desktop linux
---

Com o TMUX você pode criar várias sessões de terminal que podem ser abertas (anexadas) e fechadas (desanexadas) ou exibidas simultaneamente, tudo em uma única janela, aumentando assim sua produtividade.

![tmux](/images/tmux.png)

## Instalar o tmux

O tmux esta disponível em praticamente todos os repositórios de distribuições Linux. Então, você pode facilmente realizar sua instalação pela sua loja de aplicativos.

No caso do Ubuntu/derivados, podemos instalar pelo terminal:

```bash
sudo apt install tmux
```



## Os primeiros passos
O tmux melhora sua produtividade. Mas no começo ele pode parecer complicado. Vamos conhecer as funcionalidades básicas deste software, para que você possa evoluir de forma gradativa na sua utilização.

## Criando uma sessão tmux
Abra um terminal e use o comando:

```bash
profjulianoramos@certificacoesnetbr:-$ tmux
```

Observe que na parte inferior do seu terminal, terá algo como uma barra de tarefas verde. 

![tmux janelas](/images/tmux2.png)

O asterisco mostra a janela que esta ativa.

Vamos criar algumas janelas para você alternar. Você deve chamar a central de comandos tmux com : **[ctrl+b]** e depois tecle **c**. 

Observe na barra de tarefas que algo chamado **1:bash** foi adicionado.

![tmux3](/images/tmux3.png)

Adicione mais uma janela. 

> O tmux em alguns casos renomeia a janela para o nome da aplicação que você está executando. 

## Alternando as janelas

Veja como alternar as janelas:

Anterior | Próximo | n(0,1,2,3 etc.)
--- | ---| ---| 
[ctrl+b]+p | [ctrl+b] + n | [ctrl+b]+0 


## Alternar usando a lista de janelas

Outra opção interessante é através do comando:

**[ctrl+b]** + w 

Você terá uma visão geral das suas sessões. Podendo alternar com as setas do teclado.

## Nomear ou renomear janelas

Você pode nomear sua janela atual usando a combinação:

**[ctrl+b}** + , 

![tmux4](/images/tmux4.png)

## Criando painéis no tmux

A criação de painéis no tmux é uma das funções que eu mais utilizo. 

Você pode criar painéis horizontais e verticais. 

Horizontal |  Vertical
--- | --- |
[ctrl+b]+% | [ctrl+b]+ "

![tmux6](/images/tmux6.png)

Você alterna entre os painéis utilizando: **[crtrl+b]** + setas do teclado.

## Aplicar zoom em um painel

Você pode ampliar o painel selecionado usando:

**[ctrl+b]** + z

A tela vai usar o tamanho máximo. Usando novamente **[ctrl+b]** + z , você volta ao esquema de painéis.

## Fechando um painel

Você pode fechar um painel, usando :

**[ctrl+b]** + x

Você será questionado se realmente deseja fechar. Outro modo, é digitando **exit** no prompt.

## Mais do que o básico

Agora que você já está se divertindo com o tmux, que tal, aprender um pouco mais. O site <https://linuxhandbook.com> disponibilizou um arquivo em pdf com diversos comandos do tmux. [clique aqui para download](https://linuxhandbook.com/wp-content/uploads/tmux_cheat_sheet.pdf).

## Conclusão

Estou sempre procurando ferramentas para melhorar minha produtividade. O tmux é fantástico, no começo pode parecer confuso, mas com o tempo, você passa a amá-lo. 



## Mais sobre o tmux no nosso canal no youtube
O Professor Cicero, fez um vídeo incrível explicando o tmux. 

[![tmux](http://img.youtube.com/vi/9kgBUO6Beak/0.jpg)](http://www.youtube.com/watch?v=9kgBUO6Beak "tmux")


## E ai, tá curtindo?
Eu quero muito saber sua opinião sobre as publicações aqui do blog, deixa um comentário, é rapidinho e ajuda muito no desenvolvimento deste projeto.

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)