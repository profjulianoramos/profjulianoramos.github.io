---
layout: post
title: Snowflake é uma GUI para o SSH
date:   2020-06-12 14:52:36 +0530
categories: Desktop Linux
---
Snowflake é uma GUI para o SSH que aumenta sua produtividade e torna as coisas mais divertidas. 

![snowflake](/images/snow.png)

Todos os dias eu utilizo o shell do linux e conecto servidor SSH para fazer monitoria. As vezes tenho dezenas de servidores para verificar e mesmo usando terminais em abas e painéis, a tarefa é trabalhosa, principalmente ficar se logando nos hosts, copiando arquivos via scp e monitorando os recursos das máquinas.

## Mas então, eu descobri o snowflake!
O Snowflake inclui um gerenciador de conexões, navegador de arquivos, emulador de terminal, gerenciador de recursos com análise do processador, análise de uso de disco, editor de texto, visualizador de log e ufa... autenticação de chave SSH. Provavelmente tem mais coisas, mas você terá que descobrir. 

## Instalando no Ubuntu/derivados

Abra seu terminal de comandos:

```bash
wget https://github.com/subhra74/snowflake/releases/download/v1.0.3/snowflake_1.0-3.deb /
dpkg -i snowflake_1.0-3.deb 
```


## Usando o snowflake
Vamos testar o software, fazendo uma conexão em nosso próprio host, ou seja : 127.0.0.1 

> Certifique-se que você tenha o servidor SSH instalado e funcionando.

Abra o Snowflake e clique em **new connection** preencha os campos como a primeira imagem aqui da publicação. 

Faça sua conexão. 

![snowflake conectado](/images/snow1.png)

Você já será capaz de mover arquivo para o Host e vice-versa clicando e arrastando. Simples assim. :flushed:

## Abrindo arquivos 
A aplicação também possui um editor próprio muito bom. Clique com o botão direito no arquivo que deseja editar/visualizar, selecione "Open with - internal editor". 

![snowflake editor](/images/snow2.png)

Além disto, você tem facilmente opções de renomear, excluir, copiar e etc...

## O terminal
Clicando em terminal você já tem acesso ao Shell! O mais legal, você pode abrir mais terminais e trabalhar com múltiplos comandos ao mesmo tempo. 

![snowflake](/images/snow3.png)

## Monitorando recursos
Clicando em **System monitor** você tem acesso aos recursos do Host, simples assim! 

![snow4](/images/snow4.png)

Aliás, é muito bonita a dashboard! 

Em **Disk space analyzer** você visualiza o disco do host:

![snow5](/images/snow5.png)

Na seção **Active Transfers** você monitora as transferências de dados entre sua máquina e o servidor.

Na seção **Linux Tools** você obtêm:

- Informação do sistema
- Serviços (systemd)
- Processos e portas abertas

![snow6](/images/snow6.png)


Você também pode gerar chaves criptográficas e usar algumas ferramentas de verificação de ping, porta, tracerout e dns lookup através de um simples clique. 

## Conclusão
O Snowflake é fantástico, se você usa interface gráfica e precisa trabalhar com servidores remotos. Ainda sobre seu terminal, você pode criar *snippets** que são como *alias*, no entanto, você os executa através de clique do mouse. 

Eu sempre procuro por ferramentas que me tornem mais efetivo e sem dúvida o Snowflake está em meu coração. 

## E ai, curtiu? 
Deixe o seu comentário. Sua opinião é muito importante para o meu trabalho.  

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações. 

<https://t.me/profjulianotux>


## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)