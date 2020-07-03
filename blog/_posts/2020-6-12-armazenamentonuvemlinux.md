---
layout: post
title: Conectar gdrive, one drive, Mega e outros no Linux
date:   2020-06-12 09:56:06 +0530
categories: Desktop Linux
---

Podemos sincronizar diversos serviços de armazenamento da nuvem diretamente no nosso desktop linux, através de duas aplicações: **rcloneBrowser** e **rcloneTray**. 

![rclone](/images/rbrowser.png)

Para instalar as duas aplicações, abra seu terminal:

```bash
sudo apt-get install rclone-browser
wget https://github.com/dimitrov-adrian/RcloneTray/releases/download/v1.0.0/rclonetray_1.0.0_amd64.deb
sudo dpkg -i rclonetray_1.0.0_amd64.deb
```

## Configurar o Google Drive e One Driver
Abra o rclone browser pelo seu menu de aplicativos, clique no botão **config**.

![rclone browser](/images/rclone.png)

Tecle [n] para um novo serviço remoto.

Coloque o nome do serviço, exemplo: "Google Drive".


Na lista que aparece, selecione o número do Google Drive (13).

Em **client ID** e **client secret** você só dá enter

Escolha a 1 opção (full acess...)

Em **root_folder_id** eu uso o padrão, só enter.

Em **service_account_file** também uso o padrão, só enter.

Em **advanced config** tecle [n]

Em **auto config** confirme com [y]

Vai abrir seu Browser. Confirme o acesso no google.

Ao retornar, coloque [n] em **team drive** e confirme tudo com [y]

Clique no botão **refresh** no Rclone Browser e verá seu Google Drive. 

Faça o mesmo procedimento para o one drive e outros serviços.

## Acessando os serviços

Abra o **Rclone Tray**. Na barra de tarefas clique sobre seu ícone, escolha o serviço e clique em **mount**. Clique novamente sobre ele, escolha o serviço e selecione **Open in file Browser**.

## Serviço do MEGA

O Serviço do MEGA pode ser feito direto pela tray. Clique no ícone do Rclone Tray e selecione **New bookmark** escolha **Mega**, coloque um nome seu usuário e senha. 


## Meu vídeo sobre isto no canal


[![nuvem](http://img.youtube.com/vi/sSmLu1xzJ-Y/0.jpg)](http://www.youtube.com/watch?v=sSmLu1xzJ-Y "nuvem"){:target="_blank"}


## E ai curtiu?
Deixe seu comentário, ele é muito importante para o meu trabalho. Vamos que vamos!

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)