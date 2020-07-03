---
layout: post
title: Tutorial Markdown para iniciantes
date:   2020-06-11 09:49:13 +0530
categories: Markdown
---
**Mardown** é uma sintaxe usada para padronizar e facilitar formatação de texto na WEB, utilizada em aplicativos como o **slack** e aqui no **github**. 

![markdown](/images/markdown.png)

> O markdown funciona como um conversos de texto para o HTML.

## Por onde começar

Você pode criar um arquivo de markdown, em praticamente qualquer editor de texto simples, salvando com a extensão **.md**. Eu particularmente, trabalho no Vscode e as vezes no Typora. 

## Instalando o Typora

O typora permite editar seus texto em Markdown de uma forma mais visual. Ele é ótimo para quem esta iniciando. 

![typora](/images/typora.png)

Para instalar o Typora em seu Ubuntu, faça:

```bash
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -

sudo add-apt-repository 'deb https://typora.io/linux ./'

sudo apt-get update

sudo apt-get install typora
```

Se você usa outra distribuição, procure outros pacotes no link:

<https://typora.io/#linux>

## Usando o typora

O typora é bem simplista, ao iniciá-lo você já poderá começar a escrever suas documentações. Eu recomendo antes de tudo que você adicione o índice na lateral do aplicativo, como mostra a imagem abaixo:

![typora](/images/typora1.png)

O índice vai permitir que você navegue pela sua documentação através dos títulos e subtítulos. 

## Os atalhos do typora

Antes de começarmos a falar do **markdown** vamos conhecer alguns atalhos do typora. 

Com as teclas [ctrl+1] você aciona a opção de Título de Documento. 

[ctrl+2] você adiciona o subtítulo

[ctrl+3] você adiciona o terceiro nível de subtítulo

Como podemos ver na imagem abaixo:

![nivel de título](/images/nivel.png)

Para colocar uma palavra em negrito, você pode usar:

[crtl+b] **negrito**

Para colocar uma palavra em itálico, você pode usar:

[ctrl+i] *itálico*

Clicando com o botão direito, você abre um menu, com basicamente tudo que você precisa para formatar um documento.

![menu](/images/menu.png)

## Mas e o código markdown?

Você deve ter observado no typora que ao usar um dos atalhos de comandos, um código aparece. Por exemplo: Quando você aperta [ctrl+b] aparece ** a frente da palavra. 

Estes dois asteriscos, são o código markdown para texto em negrito. 

Ao invés de usar o atalho, digite no typora:

```markdown
**negrito**
```

Incrível não é mesmo? 

## Um pouco mais de código, por favor.

Vamos começar usando os códigos para o título:

```markdown
# Título 1 
## Título 2 
### Título 3 
#### Título 4 
##### Título 5
###### Título 6
```

Resultado :

# Título 1
## Título 2
### Título 3
#### Título 4
##### Título 5
###### Título 6



## Ênfase no documento
Para adicionar ênfase ao conteúdo que será escrito, usamos o asterisco * ou (*underline*)_:

Veja como é simples:

```markdown
**negrito**
*itálico*
```
## Links
Existem duas formas de inserir um link em Markdown. Através de um link direto ou um texto-âncora:

### Texto âncora
Utilizamos os caracteres ```[]()```, dentro da chave o texto e dentro do parêntese o link, exemplo:

```markdown
[blog do prof. Juliano](https://profjulianoramos.github.io)
```

## Link direto
Coloque o endereço URL dentro de chaves, exemplo:

```markdown
<https://profjulianoramos.github.io>
```

## Lista de ítens
Para listas não ordenadas, utilize um asterisco * na frente do ítem:

```markdown
* Item 1
* Item 2
* Item 3
```

Para listas ordenas, utilize:

```markdown
1. Item 1
2. Item 2
3. Item 3
```

As listas acima serão exibidas, desta forma:

* não ordenada 1
* não ordenada 2

1. ordenada 1
2. ordenada 2

## Imagens
O código para inserir uma imagem no conteúdo é semelhante ao código de inserir links-âncora. Adicionando apenas um ponto de exclamação a frente, exemplo:

```markdown
![título da image](URL da imagem)
```

## Citação (Quote)
Para transformar um bloco de texto em uma citação, ou comentário, coloque o caractere > a frente, exemplo:

```markdown
> A vida é boa e sempre vai dar certo
```

## Colocando código no texto
Há dois modos de adicionar trechos de código em markdown. O primeiro é colocar o código em uma linha, e o outro, é colocar em múltiplas linhas.

Para colocar um código em uma linha utilize o acento grave ` no ínicio e final do código:

```markdown
`código aqui`
```

Para múltiplas linhas, coloque três acentos graves:

```markdown
código aqui
código na segunda linha
código na terceira linha
```

Você pode específicar que tipo de linguagem é o código, assim ele coloca uma sintaxe de acordo, exemplo:

```markdown
```php
este é um código php``` 
```

Aqui está uma lista de [linguagens suportadas](http://pygments.org/languages/).

## Tabela
Escolha o título da coluna e use | para delimitar a coluno.
Depois utilize hífen - na segunda linha para indicar que acima está o título. As demais linhas, são separadas com | . 

Exemplo:

```markdown
Título | valor
--- | ---
Exemplo 1 | R$ 500
Exemplo 2 | R$ 1.000
Exemplo 3 | R$ 2.0000
```

Veja o resultado:

Título | valor
--- | ---
Exemplo 1 | R$ 500
Exemplo 2 | R$ 1.000
Exemplo 3 | R$ 2.0000

## Conclusão
Eu utilizo praticamente todos os dias **markdown** e ele me torna mais produtivo, além disto, os textos ficam incríveis, mantendo um padrão profissional de formatação. Este blog por exemplo é inteiramente escrito em markdown. 

## E ai, curtiu?
Curtiu esta publicação? Encontrou algum erro? sua opinião é muito importante para o desenvolvimento do meu trabalho. Deixe seu comentário. 

## Estou no Telegram
Agora tenho um grupo no telegram, para um bate papo mais direto sobre linux, aplicativos, servidores e certificações.

<https://t.me/profjulianotux>




## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)