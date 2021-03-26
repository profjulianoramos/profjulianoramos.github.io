---
layout: post
title: Introdução ao Red Hat RHCSA
date:   2021-03-26 17:49:00 +0530
categories: Curso RHCSA
---
Introdução ao Red Hat RHCSA
====

![Bem Vindo](https://developers.redhat.com/sites/default/files/styles/large/public/RHEL-helloworld.png?itok=kTPVSU3E)


Requisitos mínimos para o RHEL
---

* 512 MB RAM
* 4GB Disco
* Placa ethernet

Recomendado

* 1GB RAM
* 10GB Disco
* Placa ethernet

![Red hat](https://developers.redhat.com/sites/default/files/styles/large/public/Logo-Red_Hat-Enterprise_Linux_8-B-Standard-RGB.png?itok=keWYSR8I)

O Red Hat precisa de uma licença e um cadastro para seu download. Na opção "Developers" isto é gratuito. 

Acesse:
https://developers.redhat.com/sites/default/files/styles/large/public/Logo-Red_Hat-Enterprise_Linux_8-B-Standard-RGB.png?itok=keWYSR8I

## Mudar linguagem para PT-BR
Abra um terminal e digite:

```
# su root
# localectl list-locales | grep -i pt
# localectl set-locale pt_BR.UTF8
```

Reinicie a sessão.

## Elevar do Minimo para o GNOME Desktop

Vamos nesta etapa usar o DVD do Red Hat. Para isto coloque em sua máquina de virtualização o DVD.

Verifique no Red Hat o disco:

```
# lsblk
```

Crie o diretório para ponto de montagem:

```
# mkdir /dvdinstall
```

Agora monte:

```
# mount /dev/srv0 /dvdinstall
```

Acesse o diretório de repositório:

```
# cd /etc/yum.repos.d/
```

Crie o arquivo de repositório:

```
# vi dvdinstall.repo
```

Coloque o conteúdo:

```
[BaseOS]
name=BaseOS
baseurl=file:///dvdinstall/BaseOS
gpgcheck=0
enable=1

[AppStream]
name=AppStream
baseurl=file:///dvdinstall/AppsStream
gpgcheck=0
enable=1
```

Limpe os repositórios:

```
# yum clean all
```

Agora:

```
# yum repolist
```


Por fim:

```
# yum -y groupinstall "Server with GUI"
```

Defina o ambiente gráfico:

```
# systemctl set-default graphical.target
```

Reinicie o sistema.


Commits
- 26/03/2021 - 17:48 - Primeira atualização

**Deixe seu comentário.**

