---
layout: post
title: Remover snap do Ubuntu 20.04
date:   2020-06-10 10:36:12 +0530
categories: ubuntu
---


Antes de mais nada, você sabe o que é um snap?

>Snappy é um software de implantação e um sistema de gerenciamento de pacotes construído pela canonical. Os pacotes oferecidos por esta aplicação chamam-se "snap". O objetivo desta tecnologia é oferecer os paco
tes em "contêiner", já com suas dependências, rodando assim em praticamente qualquer distribuição de linux. Este modo de operação também torna o software mais seguro e em caso de uma atualização ruim, você terá a versão antes da atualização pronta a ser utilizada.


## Por que remover o snap?
Antes de responder esta pergunta, quero informar que isto não deve ser para todos. Além das vantagens que coloquei sobre o snap, ele é responsável pela aplicação "Livepatch" do Ubuntu, que permite atualizações constantes nos pacotes e no Gnome oferecidas pela Canonical, além de oferecer diversos aplicativos (alguns exclusivos) a este tipo de pacote. 

Aliás, este é o ponto que alguns usuários e eu inclusive, optei por não usar SNAP no meu sistema. O primeiro ponto é que ao ativar o Livepatch, você tem uma porta aberta diretamente com a Canonical e eu particularmente, gosto de monitorar minhas atualizações e executá-las quando desejo. 

Outro ponto, é que os pacotes snaps estão amarrados a "snap store", se você olhar em seu gerenciador de processos. Vai perceber que só este processo, ainda que você não tenha nenhum pacote snap está consumindo uma média de 400 - 480MB de sua memória RAM. Para muitos isto pode parecer pouco, mas me incomoda bastante. 

Meu sistema sem SNAP após o boot, diminuiu de 1.9GB de RAM para 1.2GB de RAM. 

## Como posso remover totalmente o snap

Execute os comandos abaixo e reinicie o seu sistema. 

```bash
# sudo apt remove --purge snapd gnome-software-plugin-snap
# sudo apt autoremove
# sudo rm -rf /var/cache/snapd
# sudo rm -rf ~/snap
```

## E agora, onde encontro os meus softwares? 
Você ainda tem todo o repositório (pacotes .deb) a sua disposição. E poderá visitar os sites oficiais das aplicações, como por exemplo: spotify, skype, telegram e fazer download dos pacotes oferecidos por eles.

## Conclusão
Snap é uma nova tecnologia que veio para ficar, no entanto, o seu consumo alto de recurso e uma política não muito interessante para com os desenvolvedores de software por parte da canonical, faz com que muitos usuários desistam de usar esta tecnologia. O meu objetivo aqui não é criticar o SNAP ou quem utiliza, mas sim, trazer soluções e alternativas para o dia a dia no mundo linux.

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)