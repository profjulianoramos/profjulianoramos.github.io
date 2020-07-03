---
layout: post
title: Quebrar senhas com John the Ripper
date:   2020-06-16 13:49:00 +0530
categories: servidor linux
---
Você tem certeza de que seus usuários estão trabalhando com senhas seguras em seus servidores linux? Se não. Deixe o "estripador" responder.

![passwords](/images/password.jpg)

> Eu demonstrarei o uso da ferramenta como um meio de testar as senhas de seus usuários em um servidor interno. O uso desta ferramenta fora desta intenção pode ter implicações legais. 

## A instalação
John the Ripper, pode ser instalado em praticamente todas as distribuições, no caso do Debian/Ubuntu e derivados, abra um terminal e digite:

```bash
sudo apt-get install john -y
```

Precisamos também de uma lista de palavras, para o John testar. No google encontrei com facilidade várias listas deste tipo. Mas existe uma no repositório.

```bash
sudo apt-get install wportuguese
```

## Mesclar o arquivo shadow com passwd

O primeiro passo é unir o arquivo shadow com passwd. Para isto, executamos:

```bash
/usr/sbin/unshadow /etc/passwd /etc/shadow > /tmp/crack.senhas.db
```

Agora, execute o comando:

```bash
john /tmp/crack.senhas.db
```

Este comando leva um bom tempo, hora do café. Apertando alguma tecla ele vai informando o status e se já conseguiu quebrar alguma senha.

## Meus usuários e suas senhas 123...

Crie um usuário com senha do tipo "123456" acreditem, eu tinha alguns destes. O John pegou em 15 segundos. Quando o John terminar de executar, ele vai criar um log. Você visualiza com:

```bash
john --show /tmp/crack.senhas.db
```

## Conclusão
Use esta ferramenta com responsabilidade. Ela é importante para garantirmos uma melhor segurança para nossos servidores. Usar de forma irresponsável, pode garantir a você, sérios problemas.


Commits:
- Edição do texto: 16/06/2020 - 14:00
- Editado erro na refência do arquivo crack.senhas.db - 16/06/2020 - 14:19 (leitor Marcos, informou).



## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)