---
layout: post
title: Qual a diferença entre Soft Link e Hard Link?
date:   2020-06-19 14:30:00 +0530
categories: desktop linux
---

Um link é um mecanismo para se criar um atalho para o arquivo ou diretório original. Ele contém informações sobre outro arquivo ou diretório.

Os links podem ser de dois tipos:

- Soft Link 
- Hard Link

### Soft link

Um Soft Link (Link Suave) também conhecido como Link Simbólico ou link virtual, é um tipo especial de arquivo que aponta para uutro arquivo ou diretório no linux.

Ele funciona como um atalho do Windows. Ele contém o caminho do arquivo original e não o seu conteúdo. 

Em geral, links simbólicos são usados para vincular bibliotecas, ou para adicionar scripts a um diretório que esteja no PATH do sistema. 

### Hard Link

Hard Link é uma cópia espelhada do arquivo original. A exclusão do arquivo original não afeta nada, porque o arquivo de link físico server como uma cópia espelhada para o arquivo.

Você pode estar se perguntando:

*Não seria mais fácil eu criar uma cópia?*

Acontece que quando você copia um arquivo ou diretório, ele vai armazenar aquele estado em que foi copiado. Qualquer alteração neste arquivo ou diretório, não irá modificar a cópia. Já no link, quando você modifica um arquivo ou diretório, todos os linkados serão alterados.

Algumas características:

Soft Link | Hard Link
---|---
O link Simbólico é semelhante ao atalho do arquivo no Windows | Hard Link é uma cópia espelhada do arquivo original
O link simbólico pode ser chamado de link virtual | Hard link não tem outro nome
Links simbólicos podem ser criados em diferentes sistemas de arquivos | O link físico, só pode ser criado no mesmo sistema de arquivo
Pode-se criar um link para arquivos e diretórios | Somente arquivos podem ser vinculados
Quando o arquivo original é removido, o link desaparece, por que irá apontar para um arquivo inexistente | Nada acontece quando o arquivo original é removido


### Utilização
Para links simbólicos a sintaxe:

```bash
ln -s /caminho/do/arquivo nome_do_link
```

Para link Hard:

```bash
ln /caminho/do/arquivo nome_do_link
```

## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 19/06/2020 - 18:33 - Upload da publicação.