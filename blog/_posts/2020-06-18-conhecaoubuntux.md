---
layout: post
title: Conheça e teste o UbunTUX Linux
date:   2020-06-18 08:09:00 +0530
categories: ubuntux 
---

Antes de qualquer coisa, quero dizer que este projeto não tem a ambição de ser mais uma distribuição linux, nem tão pouco, estamos apenas trocando o papel de parede e dizendo se tratar de uma remasterização. Existe muita coisa sobre o capô, e queremos que você venha, explorar junto com a gente.

## Um conceito de desktop novo
Uma coisa legal em se ter um canal de linux no youtube, é que eu sempre recebo feedback das pessoas sobre as diversas distribuições que apresento. E olha que são muitas! 

Percebi, que o conceito padrão de área de trabalho, poderia ser ajustado, para ser mais produtivo. Então, chega o Raul Dipeas, que mantinha o Radix Linux e mostra uma série de scripts fantásticos, que deixam o Xubuntu muito mais divertido. 

Gravei logo um vídeo com ele explicando tudo e subi lá no canal, sucesso! E com isso, recebemos dezenas de mensagens de pessoas que gostariam de ter uma imagem pronta das modificações. 

Conversei com o Raul, e resolvemos unir o conhecimento dele em criação de distros, com a minha bagagem youtuber e também de professor universitário e de certificações Linux, para criar uma nova amostra do Xubuntu 20.04. 

![desktop](/images/desktop.png)

## Não é qualquer software 
A primeira questão, neste tipo de projeto é: O que vamos incluir e por qual motivo? Partimos então, pelo conhecimento do Raul Dipeas com o feedback dos usuários Radix, somado ao feedback dos telespectadores do meu canal, logo, tinhamos uma gama de softwares populares e alguns quase que inéditos, mas que eram estáveis, seguros e de fácil utilização.

Como exemplo a esta gama de software, vou colocar o Rclone e o Snowflake. Este primeiro (rclone) já permite que você acesse pelo gestor de arquivos, seus serviços como : 

- Google Drive
- One Drive
- Mega

Entre tantos outros. E o SnowFlake, é um cliente SSH gráfico, muito moderno e de fácil utilização.

E ambos foram publicados no canal com uma aprovação altissíma. 

![app ubuntux](/images/appubuntu.png)

## E o kernel?
O Kernel padrão do Xubuntu foi alterado para o XanMod, que traz otimizações e novos recursos. 

![xammod](/images/xmk.png)

As principais características deste kernel:


   - Kernel preventivo completo sem ticks a 500Hz com agendador de núcleo de CPU ajustado.

   - RCU Boost para melhor desempenho multitarefa e menor latência de tempo de estrutura do DRI.
  
   - Camada de blocos com várias filas ajustada com agenda
    - Melhorias de cache, Gerenciador de memória virtual e CPUFreq Governor.
   - Controle de congestionamento TCP BBR + algoritmo de gerenciamento de filas CAKE.
  - Implementação do ORC Unwinder para rastreamentos de pilha do kernel (debuginfo).
  - Patchset de terceiros disponível: suporte ao kernel, initrd e módulos do ZSTD [5.7] [5.6] [5.6-rt] , Linux claro [parcial] , Wine / Proton Fsync, substituição do PCIe ACS, BMQ Process Scheduler [5.4] [estoque desabilitado] , Aufs [5.7] [5.6] [5.4] e GCC graysky's.
    Compilação do kernel Linux em tempo real (PREEMPT_RT) disponível [5.6-rt] [5.4-rt] .
- Pacote genérico de kernel para compatibilidade com a maioria das distribuições baseadas em Debian e Ubuntu. Construído sobre o mais recente GCC 10.1 e Binutils 2.34.
- Licença GPLv2. Pode ser construído para qualquer distribuição ou finalidade.


## Além de um sistema operacional, uma formação profissional
O objetivo do nosso projeto, vai além de fornecer um excelente sistema operacional. Vamos incluir nele, um centro de aprendizado gratuito, ou seja, você vai aprender linux de um modo profissional, inclusive com cursos preparatórios para a certificação linux.

Já vai incluso no sistema, meu curso gratuito preparatório para certificação LPIC-1 e um curso específico para o UbunTUX!



## Como posso ser um usuário de teste?
Se você se interessou pelo nosso projeto UbunTUX, preencha o formulário abaixo:

<https://forms.gle/unzKDqnomPwoLi4B9>

Vamos selecionar algumas pessoas que estejam dispostas a passar feedback sobre sua experiência de uso com o sistema. Se você quer aprender algo novo, que pode ser até mesmo usado como experiência profissional voluntária, este é um ótimo começo. Mas atenção, é necessário que você tenha uma conta no GitHub. Então, vai lá e se cadastra, é rápido e gratuito.

Atualmente estamos só eu e o Raul neste projeto, que está acabando de sair do forno. Venha fazer parte.

Blog do Raul
<https://rauldipeas.github.io/>

## Vídeo no youtube sobre o Ubuntux
<http://www.youtube.com/watch?v=1nwp9AXc1ic>

## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)

Commits
- 18/06/2020 - 09:41 - Upload da publicação.
- 18/06/2020 - 10:17 - Alterei "recebo feedback das pessoas" --> "recebo feedback"
- 18/06/2020 - 10:40 - Adicionado o vídeo no youtube