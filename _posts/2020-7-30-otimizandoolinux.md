---
layout: post
title: Obtendo um ganho no desempenho com o noatime
date:   2020-07-30 17:09:08 +0530
categories: Desktop
---

O recurso `atime` existe há algum tempo no linux. Ele cria três registros de data e hora para cada arquivo. São registros com informação da última modificação, alteração e quando o arquivo foi acessado pela última vez.

Estes registros eram um pré-requisito para aguns aplicativos do linux, no entanto, os aplicativos modernos não precisam mais destas informações, já que o kernel linux hoje tem um novo recurso chamado `relatime`. 

Então, se você assim como eu, espreme ao máximo as configurações do linux para obter o melhor desempenho, considere desativar este recurso de data e hora. 

### Como realizar este procedimento

Abra o arquivo de configuração `fstab`:

```bash
sudo nano /etc/fstab
```

Encontre a partição que você deseja desativar o recurso e coloque: `noatime` na seção de entrada.

Exemplo da minha linha:

```bash
/dev/sdb1 /mnt/backup   ext4  defaults,noatime,user 0 0
```



**Nota:** Se você notar que algum aplicativo não está funcionando corretamente após essa alteração, pode ser necessário remover a entrada noatime do fstab e reiniciar novamente. 