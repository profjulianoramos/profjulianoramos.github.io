---
layout: post
title: Lendo logs no linux com o Journalctl
date:   2020-06-18 14:44:10 +0530
categories: certificação lpi
---

O **journalctl** pode ajudá-lo a a solucionar problemas, quando seu serviço não iniciar. 

![systemd](/images/systemd.png)

Se você utiliza uma distribuição linux atual, provavelmente, já está familiarizado com o **SystemD**. Quando algum serviço não inicializar, o systemD tem uma excelente ferramenta para a leitura de logs, o que já adianta muito o caminho para a solução do problema. Afinal, como você vai buscar uma solução, se não sabe o que ocasiona o erro?

## O comando básico
Para uma saida inicial de log, use o comando:

```bash
journalct
```

Observe que a saída mostra o mês, o dia do mês e a hora. 

![log](/images/log.png)

Saída de erros vão ser apresentadas em vermelho. Na minha saída, eu observei um erro:

![log erro](/images/log2.png)

Então, corri no google para pesquisar sobre a mensagem apresentada. Neste caso em especial, descobri que meu pendrive (conectado a máquina) não possui um cache de disco (write-back) e o sistema "entendeu" que ele era um dispositivo SCSI (sdx) por isto, o erro/aviso.

Ufa, não tem nada de errado com minha unidade, mas foi interessante aprender mais sobre isto, obrigado Journalctl. 

## Logs da inicialização

Se você deseja listar apenas os logs do processo de boot, execute:

```bash
journalctl -b
```

### Logs de boots anteriores

Algo muito legal no journalctl é a capacidade de se explorar logs de boots anteriores. A inicialização atual é referenciada como (0) zero. Então, para visualizarmos log de um boot anterior, usamos:

```bash
journalctl -b -1
```

Você pode ver outro, com -2,-3 e etc...

### Quantos boots meu sistema realizou?

Você pode executar o comando:

```bash
journalctl --list-boots
```

![log de boot](/images/log3.png)


### Visualizar por hora

Você também pode usar o journalctl para visualizar as entradas de log por hora. Para ver as entradas da última hora, execute:

```bash
journalctl --since "1 hour ago"
```

Você pode especificar uma data e hora, na sintaxe --since, colocando no formato "Ano-Mês-Dia-Hora-Minuto-Segundo".

## Vendo log de um serviço específico

Você pode obter informação de um serviço:

```bash
journalctl -u ssh.service
```

## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)

Commits
- 18/06/2020 - 15:09 - Upload da publicação.
