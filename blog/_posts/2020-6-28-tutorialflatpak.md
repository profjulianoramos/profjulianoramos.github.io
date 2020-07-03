---
layout: post
title: Tutorial básico flatpak Linux
date:   2020-06-28 11:12:00 +0530
categories: desktop
---
Entenda o que é e como utilizar pacotes Flatpak em sua distribuição de Linux. 

![diagrama flatpak](/images/diagram.svg)

Este diagrama, que está inclusive na documentação oficial do flatpak em *inglês* que você pode acessar [clicando aqui](https://docs.flatpak.org/en/latest/basic-concepts.html) resume um pouco o que é este modelo de empacotamento de software para linux, chamado flatpak. Neste artigo, com base na documentação oficial, foco nos principios baśicos do uso do flatpak, para um olhar mais detalhado, acesse o conteúdo oficial.

### Runtime (Tempo de execução)

O Runtime fornece as dependências básicas usadas pelos aplicativos. Cada aplicativo deve ser construído em um Runtime e esse Runtime deve ser instalado em um sistema host para que o aplicativo seja executado (o Flatpak pode instalar automaticamente o Runtime exigido por um aplicativo). 

### Bibliotecas agrupadas
Se um aplicativo flatpak exigir uma dependência que não esteja em seu Runtime, ela poderá estar acoplada ao pacote. Isso fornece aos desenvolvedores de softwares a flexibilidade em relação às dependências que eles usam.

Os desenvolvedores podem incluir no pacote:
- Bibliotecas que não estão disponíveis no seu runtime
- Versões diferentes de uma biblioteca executada em seu runtime
- Versão corrigida de bibliotecas


### Sandboxes
Com o flatpak cada aplicativo é criado através de um ambiente isolado, chamado de "sandbox". Cada *sandbox* contém um aplicativo e seu tempo de execução. Por padrão, o aplicativo pode acessar apenas o conteúdo de seu ambiente.

Por necessidade, alguns recursos que estão dentro do "sandbox" podem ser exportados para fora. Estes arquivos, incluem ítens como o ```.desktop``` arquivo e o ícone do app.


### O comando flatpak
O Comando ```flatpak```é o comando padrão deste sistema de gerenciamento de pacotes. Os comandos de instalação e de remoção, são respectivamente: ```flatpak install``` e ```flatpak uninstall```.


O Flatpak identifica cada aplicativo e runtime utilizado em três partes, exemplo: ```com.empresa.app```. 

Em `app` o desenvolvedor `empresa` pode definir o nome, podendo ter assim, vários apps. 

### Flatpak para usuário ou sistema?

O Flatpak pode ser instalado para apenas o ambiente de um usuário, ou para todo o sistema.

O mesmo princípio se aplica aos repositórios. Se eles forem adicionados para todo o sistema, todos os usuários vão utilizá-lo, enquanto um repositório para um usuário, é usado somente por aquele usuário definido.

Para testes de aplicativos, é uma boa prática instalar apenas em seu usuário, neste caso, utilize ```--user``` como opção ao comando ```flatpak```.

### Listar os repositórios

Para listar os seu repositórios, execute:

```bash
flatpak remotes
```
A saída do comando indica se o repositório é de usuário ou de sistema.

### Adicionar um repositório

A maneira mais simples de se instalar um repositório é usando um arquivo ```.flatpakrepo``` , já que eles incluem todas as informações do repositório e a sua chave GPG.

Exemplo:

```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo 
```

Neste caso, ```flathub``` é o nome local que é dado ao repositório. O ```URL``` aponta para o endereço remoto e ```--if-not-exists``` impede que o comando produza uma saída duplicada.

### Removendo um repositório

Para remover um repositório no flatpak execute:

 ```bash
 flatpak remote-delete flathub
 ```

### Procurar um app em seus repositórios

Para procurar um app em seus repositórios, utilize:

```bash
flatpak search gimp
```

O retorno se positivo, trará o ID do aplicativo: org.gimp.GIMP

Então, basta instalar com:

```bash
flatpak install flathub org.gimp.GIMP
```

### Executando seus aplicativos

Você executa um aplicativo, através da opção ```run```:

```bash
flatpak run org.gimp.GIMP
```

### Atualizando um aplicativo

Para atualizar todos seus aplicativos, utilize:

```bash
flatpak update
```

### Listar meus aplicativos

Para listar os aplicativos instalados, execute:

```bash
flatpak list
```
Para listar apenas os aplicativos instalados:

```bash
flatpak list --app
```

### Remover um aplicativo

Para remover, utilize:

```
flatpak uninstall org.gimp.GIMP
```

### Referência
<https://docs.flatpak.org/en/latest/>




### Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 28/06/2020 - 11:45 - Upload da publicação.