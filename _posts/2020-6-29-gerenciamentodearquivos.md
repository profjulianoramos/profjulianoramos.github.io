---
layout: post
title: Gerenciamento de arquivos LPIC-1 101-500
date:   2020-06-29 10:008:00 +0530
categories: Certificação LPI
---

A estrutura de diretórios do linux começa pela **raíz** que é uma barra (/) semelhante ao C:\ do Windows.  Para navegar pelos diretórios usamos o comando **cd** exemplo: **cd /tmp**.

Para voltar um diretório usamos:

```
# cd ..
```

Para voltar 2 níveis de diretórios:

```
# cd ../../
```

Para ir direto para o diretório home do seu usuário:

```
# cd ~
```

Para listarmos os arquivos de um diretório usamos o comando **ls**, com a opção -a, podemos verificar arquivos ocultos:

```
# ls -a
```

Arquivos ocultos começam com . (ponto). Outra opção comum é -l, que mostra uma lista detalhada, podemos usar em conjunto com o -a para um melhor resultado:

```
# ls -la
```

Outra opção interessante é usar o -h para ver os valores em kbyte, mbyte e etc...

```
# ls -lha
```

Para ir listando todos os subdiretórios de um diretório, podemos usar o -R de recursivo:

```
# ls -R /etc/
```

Para listar somente arquivos que tenha a extensão .txt usamos o caractere curinga asterisco. Exemplo:

```
# ls *.txt
```

Digamos que você tenha uma lista com varios arquivos chamados: aula1, aula2, aula3 e etc... Você pode definir quais listar usando:

```
# ls -l aula[123]
```

Para mostrar todos e menos o aula1,aula2 e aula3, uso:

```
# ls -l aula[!123]
```

Para ver do 10 ao 20:

```
# ls -l aula[10-20]
```

Fazer uma sequencia específica:

```
# ls -l aula{10,20,30}
```

#### Copia de arquivos

O comando **cp** permite que você copie arquivos, exemplo: 

```
# cp origem destino
```

Exemplo 2 :

```
# cp /etc/passwd /tmp
```

Ver detalhes da cópia, usamos:

```
# cp -v /etc/passwd /tmp
```

Para perguntar se deseja sobrescrever um arquivo, use o hábito sempre de usar: -i , exemplo:

```
# cp -i /etc/passwd /tmp
```

Caso já tenha o arquivo ele te pergunta se deseja ou não sobrescrever o arquivo, por padrão, ou seja, sem a opção -i, ele sobrescreve sempre.

#### Copiando diretórios

O cp não copia por padrão diretórios, mas podemos resolver isto usando a opção de recursividade:

```
# cp -r diretorio /tmp/
```

#### Mover e renomear um arquivo

Usamos o comando **mv** para mover um arquivo e também para renomeá-lo, exemplo:

```
# mv diretorio /tmp
# mv arquivo /tmp
# mv arquivo arquivo2
```

Observe que não usamos -r (recursivo) no mv para diretórios. 

#### Criando arquivo de texto vazio

Usamos o comando **touch** para criar um arquivo vazio, exemplo:

```
# touch arquivo.txt
```

Também podemos alterar a data e hora de alteração de um arquivo. Se você usar **ls -l arquivo.txt** vai poder visualizar a hora de modificação do arquivo. Para mudar a data do último acesso:

```
# touch -a arquivo.txt
```

Para alterar a data da ultima modificação:

```
# touch -m arquivo.txt
```

Podemos definir uma data qualquer, exemplo:

```
# touch -t 201701011000 arquivo.txt
```

Alterei para Ano 2017, Mês 01, Dia 01, hora 10:00 tempos anteriores só mostra o ano, ignorando a hora.

#### Remover arquivos e diretórios

O comando é o **rm** exemplo:

```
# rm arquivo
```

Remove o arquivo sem perguntar, se você quer que ele pergunte, use:

```
# rm -i arquivo
```

Para remover diretório, usamos a recursividade:

```
# rm -r diretório
```

#### Remover diretório vazio

Para remover diretório vazio, pode-se usar o comando **rmdir** na prática, acabamos sempre usando o **rm**.

#### Criar um diretório

Usamos para a criação de um diretório o comando: **mkdir** exemplo:

```
# mkdir diretorio
```

Se você desejar criar um diretório com outro diretório use -p  ou --parents que tem mesmo efeito.

```
# mkdir -p diretorio/diretorio2/diretorio3
```

#### Procurar arquivos e diretórios

Para procurarmos arquivos e diretórios usamos o comando:

```
# find /home -name aula1.txt
```

No comando acima ele vai procurar o arquivo1.txt dentro do diretório /home. Para vermos todos que começam com aula, usamos:

```
# find /home -name aula*
```

Para restringir por um usuário específico:

```
# find /home -user juliano -name aula1
```

Agora só vai procurar arquivo1 do usuário juliano. Para procurarmos arquivos por data de modificação:

```
find ./ -ctime -1
```

Neste caso, estou procurando a partir do meu diretório atual (./) arquivos modificados no último dia.

### Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 29/06/2020 - 10:00 - Upload da publicação.