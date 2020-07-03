---
layout: post
title: 8 dicas de segurança para o SSH
date:   2020-06-10 17:03:36 +0530
categories: Servidor linux
---

O SSH é o método mais utilizado pelos Sysadmins, para acesseram seus hosts remotamente. O que pouca gente sabe, é que ele pode ser a causa de seu servidor ser comprometido. 

O protocolo SSH é muito seguro, mas isto não significa que você deva usar a configuração padrão do serviço cegamente.

![ssh](/images/sshseguro.jpg)

**Aviso importante** 
> Não siga as dicas cegamente. Leia e entenda se ela se adequa a sua necessidade. 


## O arquivo de configuração

O arquivo de configuração do SSH fica em **/etc/ssh/sshd_config**. A maioria das dicas mencionadas neste tutorial, tem como base a edição deste arquivo. Então, antes de mais nada, faça seu backup. 

### 1 - Senhas vazias

No linux é possivel você criar usuários sem senha. Se este usuário tentar acessar o SSH, ele também não precisará digitar uma senha. 

Isso é um risco a segurança. Para proibir o acesso a senhas vazias, edite no arquivo **/etc/ssh/sshd_config** a opção:

```bash
PermitEmptyPasswords no 
```

### 2 - Alterando a porta padrão

A porta SSH padrão é 22. A maioria dos scripts de ataque são escritos com esta porta. Alterar esta porta é uma camada a mais de segurança para seu servidor. 

Dentro do arquivo de configuração, altere a porta, para um número diferente, exemplo:

```bash
Port 2345
```

### 3 - Desative o login de root via SSH

O root em servidores deveria ser proibido. Uma política bem escrita com o sudo já proporciona uma segurança melhor. Para desativar o acesso do root no SSH, no arquivo de configuração, defina:

```bash
PermitRootLogin no
```

### 4 - Desative o protocolo ssh 1

Isto é somente para distribuições mais antigas. As atuais oferecem apenas suporte ao protocolo 2. Se você tem dúvidas, adicione no arquivo:

```bash
Protocol 2
```

### 5 - Tempo de inatividade

O tempo de inatividade é quanto tempo uma conexão SSH pode ficar ativa sem nenhuma atividade. O intervalo de tempo limite é contado em segundos e, por padrão, é o 0. Você pode alterá-lo para 300 para manter um intervalo de tempo limite de cnco minutos.

```bash
ClientAliveInterval 300
```

Após este intervalo o servidor SSH enviará uma mensagem ativa ao cliente. Se não receber resposta, a conexão é fechada.

Você pode também, controlar quantas vezes ele envia a mensagem ativa, antes de desconectar:

```bash
ClientAliveCountMax 2
```

### 6 - Acesso SSH apenas para usuários selecionados

Só de permissão a quem é realmente necessário. Lembre-se. Menos é mais, quando tratamos de segurança.

Você pode definir os usuários que podem fazer acesso, restringindo os demais:

```bash
AllowUsers usuario1 usuario2 
```
Você pode criar um grupo somente para usuários que usam SSH e definir:

```bash
AllowGroups ssh_grupo
```

### 7 - Desative o encaminhamento X11

O encaminhamento X11 permite que você use aplicativos GUI via SSH. O protocolo X11 não é orientado para a segurança. Se você não precisa, desabilite:

```bash
X11Forwarding no
```

### 8 - Desative login SSH baseado em senha

Um excelente medida de segurança é usar uma chave pública para seu cliente acessar o servidor SSH. Assim o cliente acessa o servidor sem senha. 

Abaixo deixo um vídeo do meu canal, que falo sobre como configurar o SSH com chave criptografada:

[![chave](http://img.youtube.com/vi/GGmJZgRCz2Y/0.jpg)](http://www.youtube.com/watch?v=GGmJZgRCz2Y "chave")

*clique na imagem e será redirecionado ao vídeo no youtube.


## Conclusão

Além destas dicas, existem outras, como autenticação em dois fatores (que exigem um tutorial próprio). Mas, estas aqui, já garantem uma camada extra de segurança ao seu servidor.

Se você gostou deste tutorial, comente, sua opinião e incentivo é importante para o meu trabalho.

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)