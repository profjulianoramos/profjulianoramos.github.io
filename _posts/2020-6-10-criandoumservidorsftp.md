---
layout: post
title: Criando um servidor SFTP no linux
date:   2020-06-10 11:08:16 +0530
categories: Servidor Linux
---

O SFTP é um excelente método para a transferência de arquivos remotos no linux. Neste tutorial, vamos aprender a configurar este sistema seguro de compartilhamento de arquivos e conhecer sua diferença ao tradicional FTP.

## FTP ou SFTP

FTP ou File Transfer Protocol é um sistema de transferência de arquivos, muito conhecido. Porém, se você procura um pouco mais de segurança, recomendo que utilize o SFTP.

SFTP é a sigla para *Secure Transfer Protocol* ou seja, protocolo de transferência segura. Isso é possível por que o SFTP utiliza criptografia na sua transferência de arquivos, usando um método de tecnologia de impressão digital, para verificar as chaves dos hosts liberados antes de iniciar a transferência.

Além disto, você precisará liberar em seu firewall apenas a porta 22, enquanto, o FTP precisa abrir vários canais para que a comunicação ocorra.

## O passo a passo
Vamos realizar esta configuração em algumas etapas:

- Criar um grupo novo
- Criar um usuário novo e adicioná-lo a este grupo
- Instalar o SSH
- Configurar o arquivo de configuração do SSH (sshd_config)
- Especificar um diretório a ser compartilhado
- Acessar o sftp

## Criando o novo grupo

Vamos criar um grupo novo chamado de **sftpusers**:

```bash
groupadd sftpusers
```

Agora, vamos criar o nosso usuário e adicioná-lo a este grupo:

```bash
useradd -g sftpusers -d /compartilhar -s /sbin/nologin guestuser 
```

Vamos atribuir uma senha para este usuário:

```bash
passwd guestuser
```

Instale o SSH:

```bash
sudo apt-get install openssh-server
```

Edite o arquivo de configuração **/etc/sshd_config** comentando a linha Subsystem e adicionando outra :

```bash
#Subsystem      sftp    /usr/libexec/openssh/sftp-server
Subsystem       sftp    internal-sftp
```

No final do arquivo adicione:

```bash
Match Group sftpusers
        ChrootDirectory /sftp/%u
        ForceCommand internal-sftp
```

Estamos especificando que os usuários do grupo sftpusers, vão acessar seus respectivos diretórios. 

## Crie o diretório

Vamos criar o diretório para o compartilhamento (raiz):

```bash
mkdir /compartilhar
```

Vamos criar o diretório do nosso usuário guestuser:

```bash
mkdir /compartilhar/guestuser
```

Agora, vamos criar um diretório para os usuários enviarem os arquivos:

```bash
mkdir /compartilhar/guestuser/publico
```

## Adicionando as permissões
Vamos adicionar o dono e o grupo para o diretório criado:

```bash
chown guestuser:sftpusers /compartilhar/guestuser/publico
```

## Reinicie o serviço

```bash
service sshd restart
```


# Testando a conexão

Faça um teste na sua própria máquina:

```bash
# sftp guestuser@127.0.0.1
```

Você deve fornecer sua senha de acesso.

## Conclusão
Criar um servidor para compartilhar arquivos através do SFTP é uma solução rápida e segura. Sempre que possível, escolha esta opção ao FTP. 

## E ai, curtiu?
Se você gostou deste conteúdo, deseja reportar algum erro, por favor, deixe o seu comentário. Sua opinião é muito valiosa e faz o nosso projeto crescer cada vez mais.

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>


## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)
