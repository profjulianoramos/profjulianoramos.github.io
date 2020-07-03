---
layout: post
title: Virtualização nativa no Fedora
date:   2020-06-22 06:53:12 +0530
categories: virtualização
---

O Fedora como todos os outros sistemas com kernel linux, possui suporte nativo a virtualização. Esse suporte é fornecido pela **KVM** (Máquina virtual baseada em kernel). O **QEMU** é um emulador completo que trabalha em conjunto com o KVM e permite que você crie máquinas virtuais com definição de hardware e periféricos.

Outra aplicação que faz parte deste conjunto é o **libvirt**, ele é uma camada da API que permite a administração da infraestrutura, ou seja, ele permite que você crie e administre as máquinas virtuais.

As três tecnologias, estão presentes para que você implemente seu Fedora, não necessitando a instalação de softwares de terceiro como o Vmware ou Virtualbox.

### O Boxes

O **Boxes** é uma simples ferramenta de virtualização e manipulação de máquinas virtuais remotas. Ele está presente no Fedora. Em outras distribuições de linux, ele é fácilmente instalável, tendo para download um pacote universal **flatpak**:

<https://flathub.org/apps/details/org.gnome.Boxes>


Clique em Atividades - boxes. 

![boxes](/images/boxes.png)

Para criar uma máquina virtual, clique em **+** e depois em *criar uma máquina virtual...* 

Você pode instalar de uma fonte (imagem .iso) ou realizar o Download de algumas distribuições, pela opção: Download do sistema operacional.

![download iso linux](/images/boxes.gif)

### Instalação automatizada

O Boxes possui uma opção de instalação expressa, na qual ele realiza para você a instalação do sistema operacional. Não são todos que possuem esta possibilidade. No caso do debian, ao apontar para a imagem .iso que eu tinha em meu computador, ele ofereceu esta disponibilidade:

![boxes expressa](/images/boxes1.png)

Ativando a chave, você só precisa colocar um nome de usuário, para a conta administrativa e senha. 

Clicando em **próximo** você pode personalizar o tamanho da memória e disco. Ao clicar em Criar o processo de instalação automatizado é iniciado. 

![boxes automático](/images/boxes2.png)

*Uma boa hora para um cafézinho...*

### Além do boxes

O Boxes é uma ferramenta simples e intuitiva, excelente para uso em computadores pessoais. Porém, em alguns casos, é necessário uma ferramenta com mais opções de configuração. 

Por exemplo: Eu uso máquina virtual para ministrar meu curso de LPI, em determinada aula, falo sobre LVM e neste caso preciso adicionar alguns disco rígidos virtuais para ensinar a configuração deste sistema de particionamento. O Boxes não me permite este tipo de configuração. 

### Virtual Manager Machine

Abra um terminal de comando e instale o conjunto de ferramentas de virtualização, disponível no repositório fedora:

```bash
sudo dnf install @virtualization
```
Por padrão o sistema de administração de máquinas virtuais é limitado ao usuário **root**. Mas podemos resolver isto, editando o arquivo:

```bash
sudo vi /etc/libvirt/libvirtd.conf
```

Na seção "Socket Group Ownership" descomente:

```bash
unix_sock_group = "libvirt"
```

Em "Socket permissions" descomente:

```bash
unix_sock_rw_perms = "0770"
```

Agora inicie o serviço e habilite-o para a próxima inicialização:

```bash
sudo systemctl start libvirtd
sudo systemctl enable libvirtd
```

Adicione seu usuário no grupo libvirt:

```bash
sudo usermod -a -G libvirt $(whoami)
```

Inicie o gerenciador de máquinas virtuais pelo seu menu Atividades.

### Criando uma máquina virtual

*Através de uma imagem .iso*

Clique no ícone "Criar uma nova máquina virtual":

![libvirt](/images/libv1.png)

Escolha a mídia de instalação (Imagem ISO ou CDROM)

![libvirt2](/images/libv2.png)

Clique em navegar e navegar localmente:

![libvirt3](/images/libv3.png)

Aponte para sua imagem iso e clique em abrir - avançar.

Selecione o tamanho da memória e quantas CPUs a máquina virtual vai utilizar:

![libvirt4](/images/libv4.png)

Selecione um tamanho de disco rigido. Só resta finalizar a configuração. Você pode optar em personalizar antes da instalação, para configurações mais avançadas, ou simplesmente conluir.

![libvirt5](/images/libv5.png)


## Veja também:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)


Commits
- 22/06/2020 - 08:11 - Upload da publicação.

