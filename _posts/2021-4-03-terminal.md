---
layout: post
title: Curso RHCSA - O que é terminal?
date:   2021-04-03 03:21:00 +0530
categories: Curso RHCSA
---


Inicialmente, quando não existiam os computadores pessoais (PC), nem notebooks, mas existiam os grandes mainframes rodando algum tipo de UNIX (ou outro sistema operacional proprietário e específico para o hardware), era necessário utilizar alguma coisa para que o usuário final pudesse interagir com esse mainframe central. Essa “coisa” que foi escolhida foi o **TeleTYpe** (daí o nome TTY), uma evolução das antigas TelePrinters ([Teleprinter na Wikipedia](https://en.wikipedia.org/wiki/Teleprinter)) que já eram utilizadas desde o início do século XX.

[![teletypes](http://fdta.com.br/wp-content/uploads/2016/10/teletypes-296x300.jpg)](http://www.linusakesson.net/programming/tty/)

Teletypes em 1940 ([www.linusakesson.net/programming/tty/](http://www.linusakesson.net/programming/tty/))

Inúmeros fabricantes, tipos e modelos de teletypes foram utilizados nos primórdios da computação, na década de 1960, até que foram sendo substituídos por outras coisas, como leitoras de cartões perfurados. Mas esse TeleTYpe é que era, na época, o “terminal” do computador: uma maneira de enviar e receber informações para o mainframe. Como TTY era um acrônimo para os teletypes (na época o terminal do mainframe), a sigla TTY passou a ser associada com o “terminal”: a coisa que conseguia enviar e receber informações do mainframe.

A partir da década de 1970 começarama surgir terminais de vídeo para os mainframes, sendo um dos mais famaos o VT-100 da Digital Equipment Corporation (DEC):

[![dec_vt100_terminal](http://fdta.com.br/wp-content/uploads/2016/10/DEC_VT100_terminal-300x266.jpg)](https://en.wikipedia.org/wiki/VT100)

VT-100 (https://en.wikipedia.org/wiki/VT100)

Esses equpamentos, terminais de vídeo, também eram uma forma de enviar e receber informações ao mainframe, e também eram conhecidos por terminais. Na verdade os terminais de vídeo passaram a ser os TERMINAIS de fato dos mainframes, mas a nomenclatura TTY, da época dos teletypes, continuou. O fluxo de trabalho com os terminais era o seguinte:

[![terminal_flow](http://fdta.com.br/wp-content/uploads/2016/10/terminal_flow.png)](http://www.linusakesson.net/programming/tty/)

Fluxo em um TERMINAL físico ([www.linusakesson.net/programming/tty/](http://www.linusakesson.net/programming/tty/))

O terminal, que era um teletype ou um terminal de vídeo, se conectava ao mainframe através de uma linha física, interagindo com o Kernel do UNIX (que ficava responsável pelos detalhes de baixo nível, como o baud rate, parity control, etc.) que usava um “Driver TTY” para interagir com os processos do usuário. Nessa época o terminal era uma coisa separada do mainframe.

Com a evolução e o surgimento das computadores pessoais, o modo de interação com o computador passou a ser integrado no próprio computador: o teclado, o mouse e o vídeo. Passamos para um mundo onde o teletype e os terminais de vídeo não existem mais. Assim, todos os terminais que você vê hoje em dia nos computadores UNIX/Linux, são ***TERMINAIS EMULADOS\*** por algum ***EMULADOR DE TERMINAL\***, algo que mimetiza os antigos terminais de vídeos reais (com muitas outras funções agregadas para a facilidade do usuário). Também são chamados de ***TERMINAIS VIRTUAIS\***.

Vamos fazer uma pausa nessa discussão sobre os terminais agora para introduzir outro assunto básico: o console. Depois voltaremos ao assunto dos terminais e consoles.

## 3. O que é o console?

Novamente vamos para a história. Antigamente um console era um hardware específico para o controle de um mainframe. Os terminais de antigamente (teletypes ou terminais de vídeo) não serviam para controlar o mainframe. Para isso era necessário um equipamento especial, o console, que era conectado ao mainframe para controlá-lo:

[![ibm_1620_model_1](http://fdta.com.br/wp-content/uploads/2016/10/IBM_1620_Model_1.jpg)](https://en.wikipedia.org/wiki/System_console)

Console do IBM 1620 (https://en.wikipedia.org/wiki/System_console)

Esse console (também chamado de console do sistema, console do computador, console root ou console do operador) era utilizado para a administração do mainframe. Posteriormente terminais de vídeo também passaram a ser utilizados como console e para a exibição de mensagens de importância administrativa como mensagens do Kernel, da BIOS, do Boot Loader, do processo de init ou do system logger, entre outros.

Assim, o CONSOLE passou a significar algo ***conectado diretamente ao computador ou mainframe\*** (através de portas seriais ou outros mecanismos) para receber mensagens administrativas e realizar tarefas no sistema, exceto as tarefas do usuários que continuavam a ser realizadas nos terminais de vídeo. O console funciona assim:

[![terminal_virtual1](http://fdta.com.br/wp-content/uploads/2016/10/terminal_virtual1.png)](http://www.linusakesson.net/programming/tty/)

Modo de operação do console ([www.linusakesson.net/programming/tty/](http://www.linusakesson.net/programming/tty/))

Um hardware conectado diretamente ao computador interage com o Kernel através do vídeo e o teclado; o Kernel utiliza então um emulador de terminais e um driver TTY para interagir com os processos do usuário.

Novamente, com a evolução dos computadores o CONSOLE deixou de ser algo externo conectado diretamente ao computador e passou a ser interno ao próprio sistema, acessado simplesmente com o teclado e o monitor de vídeo dos computadores/servidores atuais.

Note duas coisas importantes aqui: ***o console é a interface de administração do sistema\***, e é ele ***é acessado através de um emulador de terminais utilizando-se drivers TTY\***.

E no UNIX/Linux, onde fica o ***CONSOLE DO SISTEMA\*** responsável pela administração do computador/servidor? Já falamos que com a evolução da computação o console deixou de ser algo externo conectado ao computador e passou a ser interno ao sistema. O mesmo ocorre no Linux: o console é um sistema interno do Kernel que recebe todas as mensagens e avisos do Kernel, do sistema de logs, etc., e fornece um meio para o usuário administrar o computador. Também já falamos que como o console passou a ser interno, é acessado pelo teclado e vídeo do computador. Mas então, onde está o console no Linux?

O Linux trabalha com o conceito de ***CONSOLES VIRTUAIS\***, que são *consoles de administração logicamente separados mas acessados pelo mesmo par teclado/vídeo*. Geralmente o Linux formece 6 consoles virtuais de administração com um emulador de terminais prontos para uso, acessados atravé da combinação de teclas Alt+F1 até Alt+F6 (se o computador está em modo texto) ou Ctrl+Alt+F1 até Ctrl+Alt+F6 (se o computador está em modo gráfico).

O console não serve apenas para a administração do sistema: um usuário pode escrever um texto e enviá-lo por e-mail usando somente o console e alguns utilitários Linux mas, geralmente, quem acessa um console virtual através do teclado e vídeo do computador/servidor é o administrador do sistema.

Outro ponto interessanto do console é que ele não é obrigatório: algumas distribuições embarcadas de Linux não disponibilizam o console mas, sim, outra interface para a administração (geralmente uma interface web).

## 4. E o terminal/console na interface gráfica?

Podemos usar o Linux durante muito tempo somente na interface gráfica, nunca necessitando abrir o console ou um terminal emulado na interface gráfica. Mas as vezes isso é necessário. E isso é feito, novamente, através de emuladores de terminais que podem ser iniciados a partir da própria interface gráfica (Gnome, KDE, etc.).

Existem vários emuladores de terminais disponíveis nas interfaces gráficas (xterm, Konsole, Gnome-Terminal, Terminator, aterm, guake, MacOS Terminal, rxvt, Xfce Terminal, etc.) mas todos fazem a mesma coisa: abrem uma janela gráfica com um terminal emulado que pode ser utilizado tanto para a administração do sistema (como um console puro) como para tarefas do usuário.

Aqui vemos que o antigo terminal (teletype ou terminal de vídeo) e os consoles virtuais de administração podem ser acessados como uma coisa só através de um emulador de terminais.

Mas existe uma diferença entre o terminal emulado a partir da interface gráfica e o terminal emulado a partir dos consoles virtuais. Os terminais emulados para os consoles virtuais são gerenciados diretamente pelo Kernel usando um driver TTY.

Já os terminais emulados na interface gráfica são diferentes pois a emulação do terminal é feita no espaço do usuário e não pelo Kernel. E para manter todo o subsistema TTY do Kernel intacto, foram criados os ***PSEUDOTERMINAIS\***. A coisa funciona assim (exemplificado com o emulador xterm):

[![terminal_virtual2](http://fdta.com.br/wp-content/uploads/2016/10/terminal_virtual2.png)](http://www.linusakesson.net/programming/tty/)

Emuladores de terminais gráficos e pseudoterminais ([www.linusakesson.net/programming/tty/](http://www.linusakesson.net/programming/tty/))

Como o terminal emulado não fica no Kernel e sim no espaço do usuário, o Kernel utiliza um PSEUDOTERMINAL MASTER (PTY master) para interagir com o emulador de terminais do usuário, e utiliza os drivers TTY como um PSEUDOTERMINAL SLAVE (PTY slave) para interagir com os demais processos que o usuário inicia no terminal emulado gráfico.

Para o usuário toda essa coisa é transparente: ele não sabe se está interagindo com um emulador de terminais no espaço do usuário e um pseudoterminal no Kernel, ou se está interagindo com um emulador de terminais diretamente no Kernel. A funcionalidade é a mesma (exceto talvez por algumas coisas que podem ser configuradas no terminal gráfico, como cores, título das janelas, funcionalidades de copiar e colar, etc.).

O terminal emulado pela interface gráfica é chamado comumente de JANELA DE TERMINAL.

## 5. Linha de comando

Essa é fácil. Também conhecida como ***CLI (Command Line Interface)\***, é toda interface de interação com o usuário que aceita somente input via texto, e só retorna output via texto também. Você não pode ver um vídeo na linha de comando (quer dizer, poder até pode mas o resultado não é o que você está esperando: [Stupid Geek Tricks: Watch Movies in Your Linux Terminal Window](http://www.howtogeek.com/howto/linux/stupid-geek-tricks-watch-movies-in-your-linux-terminal-window/)).

## 6. Resumindo tudo até aqui

- ***TERMINAL\***: é algo que não existe mais, era um hardware (teletype ou terminal de vídeo) que os usuários utilizavam para se conectar ao mainframe
- ***EMULADOR DE TERMINAIS\***: é a coisa que consegue emular um terminal para que o usuário possa trabalhar, usando o próprio vídeo e teclado do computador. Pode ser o próprio Kernel ou algum outro emulador de terminais (xterm, Konsole, etc.)
- ***CONSOLE\***: também é algo que não existe mais, era um hardware que os usuários conectavam no computador para administrá-lo
- ***CONSOLE VIRTUAL\***: é a interface de administração do Linux, que transformou o antigo console em vários consoles virtuais, separados logicamente mas acessados pelo mesmo par teclado/vídeo. Utiliza o emulador de terminal do Kernel.
- ***PSEUDOTERMINAL\***: é o par de terminais master/slave que o Kernel utiliza para se comunicar com um emulador de terminais que roda no espaço do usuário, em alguma interface gráfica, e não no próprio Kernel.
- ***JANELA DE TERMINAL\***: é a apresentação na interface gráfica do emulador de terminal (Konsole, Gnome Terminal, xterm, etc.).
- ***LINHA DE COMANDO\***: é a interface que recebe comandos e inputs e retorna outputs só via texto.

Entendeu? Então veja se consegue acompanhar o seguinte raciocínio:

1. Um ***console virtual\*** é uma interface de administração acessada pelo par vídeo/teclado do computador, que apresenta uma ***linha de comando\*** para o usuário, utilizando um ***emulador de terminal próprio do Kernel\*** e ***drivers TTY\*** para interagir com os processos do usuário.
2. Uma ***janela de terminal\*** é uma janela gráfica acessada pelo vídeo/teclado do computador, que apresenta uma ***linha de comando\*** para o usuário, utilizando um ***emulador de terminal externo ao Kernel\***, e ***pseudoterminais master/slave\*** para interagir com os processos do usuário.

Veja um exemplo de meu laptop:

![janela_terminal](http://fdta.com.br/wp-content/uploads/2016/10/janela_terminal.png)

A janela acima é um print-screen de uma ***JANELA DE TERMINAL\*** em meu laptop, que apresenta uma ***LINHA DE COMANDO\*** com o prompt “[abrantesasf@laptop04 ~]$ ” (ignore esse prompt por enquanto). Eu forneci um comando para mostrar os usuários logados no sistema e o ***TERMINAL VIRTUAL\*** (emulador de terminal) utilizado. Temos a seguinte situação:

- Usuário abrantesasf logado no terminal virtual (pseudoterminal) pts/0: é o terminal da interface gráfica em si
- Usuário abrantesasf logado no terminal virtual (pseudoterminal) pts/1: é a primeira aba da janela de terminal
- Usuário abrantesasf logado no terminal virtual (pseudoterminal) pts/2: é a segunda aba da janela de terminal
- Usuário abrantesasf logado no terminal virtual tty2: mostra que além do que está visível na interface gráfica, o usuário abrantesasf também está logado no console virtual acessível pelo terminal virtual TTY2, e pode ser acessado pelo comando Ctrl+Alt+F2
- Usuário root logado no terminal virtual tty3: mostra que o usuário root também está logado em outro console virtual acessível pelo terminal virtual TTY3, e pode ser acessado pelo comando Ctrl+Alt+F3

Note que os terminais emulados pelo Kernel são chamados de TTY e os pseudoterminais utilizados pelo Kernel para interagir com um emulador de terminal externo são chamados de PTS.



Este conteúdo tem sua fonte:

http://fdta.com.br/2017/04/23/sobre-terminais-consoles-e-terminais-virtuais/



**Commits**

- 03/04/2021 - 03:32 - Primeira atualização

**Deixe seu comentário.**

