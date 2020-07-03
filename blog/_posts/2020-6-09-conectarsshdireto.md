---
layout: post
title: Conectar SSH em um diretório específico
date:   2020-06-10 17:03:36 +0530
categories: Servidor linux
---

Se você assim como eu está sempre em busca de ser mais efetivo em suas ações, este tutorial, apesar de ser uma dica simples, ajuda nesta melhora da produtividade.

## Pré-requisito

Conhecimento básico em conexão remota usando o SSH.

## Ação prática

Suponha que você tem um host de IP: 192.168.1.7 e você deseja acessá-lo para manipular arquivos que estão no diretório:

```bash
/home/juliano/financeiro/adm2/santander/app
```

Você pode acessar o host e o devido local executando:

```bash
# ssh -t juliano@192.168.1.7 \
'cd /home/juliano/financeiro/adm2/santander/app ; bash'
```

Simples assim:

![gif animada](/images/ssh.gif)


Se você sempre acessa este host e este diretório, pode ser ainda mais produtivo criando um pequeno script:

```bash
#!/bin/bash

echo "Digite um usuario:"

read usuario


echo "Digite um IP"

read ip


ssh -t $usuario@$ip \ 
'cd /home/juliano/financeiro/adm2/santander/app ; bash'

```


Salve com o nome que desejar. Conceda permissão de execução:

~~~bash
chmod +x script.sh
~~~

E seja seja mais feliz.

![gif animada2](/images/ssh2.gif)


## Conclusão
>A busca pela efetividade deve ser constante. Realize pequenas ações todos os dias que o torne mais produtivo. Lembre-se: Tudo pode ser melhorado e aprimorado. - Vamos que vamos!

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)