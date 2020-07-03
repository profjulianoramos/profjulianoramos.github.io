---
layout: post
title: Comandos linux em uma página
date:   2020-06-16 16:24:00 +0530
categories: certificação lpi
---

Os comandos mais utilizados do mundo linux, incluindo a instalação do Arch linux, em apenas uma página.


## Comandos bash

Comando | Descrição
---|---
uname -a  | Informação do sistema e Kernel
head -n1 /etc/issue | Informação da distribuição
mount | Mostra dispositivos montados
date | Mostra data do sistema
uptime | Tempo de uso do host
whoami | Mostra seu usuário
man comando | Página de manual do comando

## Manipulação de diretórios

Comando | Descrição
---|---
pwd | Mostra o diretório atual
mkdir dir | Cria o diretório dir
cd dir | Acessa o diretório dir
cd .. | Sobe um nível de diretório
ls | Lista arquivos e diretórios


## Atalhos do bash

Comando | Descrição
---|---
CTRL-c | Para o comando atual
CTRL-z | Coloca o comando em segundo plano
CTRL-a | Vai para o inicio da linha
CTRL-e | Vai para o final da linha
CTRL-u | Corte a partir do inicio da linha
CTRL-k | Corte até o final da linha
CTRL-r | Histórico de busca
!! | Repete o último comando
!abc | Executa o comando que começa com abc
!$ | Último argumento do comando anterior


## Opções do ls

Comando | Descrição
---|---
-a | Mostra tudo, incluindo ocultos
-R | Lista recursiva
-r | Ordem reversa
-t | Classifica por última modificação
-S | Classifica por tamanho do arquivo
-1 | Um arquivo por linha
-m | Saída separada por vírgula
-Q | Saída entre "aspas"

## Variáveis do bash

Comando | Descrição
---|---
PATH | Caminho de pesquisa dos executáveis
HOME | Diretório inicial do usuário
SHELL | Shell Atual
HISTFILE | Arquivo do histórico
HISTSIZE | Tamanho do histórico


## Redirecionamento de Entrada e saída
*cmd* referência para comando.

Comando | Descrição
---|---
cmd < arquivo | Entrada de cmd como arquivo
cmd > /dev/null | Descartar saída 
cmd > arquivo | Saída padrão (stdout) para arquivo
cmd >> arquivo | Anexar stdout ao arquivo
cmd 2> arquivo | Saída de erro em arquivo (stderr)
cmd 1>&2 | Stdout e Stderr no mesmo arquivo
cmd &> arquivo | Toda saída de cmd para arquivo



## Comandos em sequência

Comando | Descrição
---|---
cmd1; cmd2 | Executa cmd1 e cmd2
cmd1 && cmd2 | Executa cmd2 se cmd1 for bem-sucedido
`cmd1 || cmd2`| Executa cmd2 se cmd1 não for bem-sucedido
cmd & | Executa cmd em um subshell

## Procurar arquivos

Comando | Descrição
---|---
grep -i | Pesquisa sem distinção de maiúsculas e minúsculas
grep -r | Pesquisa recursiva
grep -v | Pesquisa invertida
find /dir -name linux* | Procura arquivos no diretório *dir* que comecem com linux
find /dir -user juliano | Encontra arquivos que pertençam ao usuário juliano
whereis cmd | Procura pelo binário, código fonte e página de manual 

## Arquivos

Comando | Descrição
---|---
touch arquivo | Cria arquivo
cat file1 file2 | Concatena file1 com file2
less file1 | Visualiza paginando file1
file file1 | Visualiza o tipo de file1
cp file1 file2 | copia file1 para file2
mv file1 file2 | Move file1 para file2
rm file1 | Apaga file1
tail file1 | Mostra as últimas 10 linhas de file1
tail -f file1 | Mostra as últimas linhas e monitora o arquivo file1 em tempo real

## Processos

Comando | Descrição
ps | Mostra os processos
top | Mostra os processos em tempo real
kill pid | Mata o processo 
pkill nome | Mata o processo pelo nome
killall nome | Mata o processos "nome"


## Permissões

É importante que você compreenda os seguintes valores:

Permissão | Valor
---|---
Leitura (r) | 4
Escrita (w) | 2
Execução (x) | 2


### Permissão de arquivos

Comando | Permissão
---|---
chmod 775 file | Coloca permissão 775 ao file
chmod -R 600 diretorio | Coloca permissão 600 de forma recursiva no diretorio
chow user.group file | Define o dono e o grupo para file

## Permissões comuns

Código | Permissão | Descrição
---|---|---
0  | --- | Sem acesso
1 | --x | Execução
2 | -w- | Escrita
3 | -wx | Escrita/Execução
4 | r-- | Leitura
5 |r-x | Leitura/Execução
6 | rw- | Leitura / Escrita
7 | rwx | Leitura / Escrita /Execução

## Comandos de permissões

Comando | Descrição
---|---
chmod | Altera as permissões de um arquivo
chgrp | Altera o grupo de um arquivo ou diretório
chown | Altera o dono de um arquivo ou diretório



## FHS

Diretório | Definição
---|---
/bin/ | Comandos binários essenciais
/boot | Arquivos estáticos do bootlader
/dev | Arquivos de dispositivos
/etc | Arquivos de configuração do host
/home | Diretório do usuário
/lib | Bibliotecas essenciais e módulos do kernel
/media | Ponto de montagem de mídia removível
/mnt | Ponto de montagem de sistema de arquivo temporário
/opt | Aplicativos adicionais
/sbin | Binários do sistema
/srv | dados de serviços providos pelo sistema
/tmp | Arquivos temporários
/usr | Utilitário e aplicativos multi-usuário
/var | Arquivos de variáveis
/root | Diretório do usuário Root
/proc | Sistema de arquivo virtual, processos e status do sistema


## Instalação Arch

Instalação básica, com base em duas partições, sendo uma para a raíz do sistema e outra para swap.


Comando | Descrição
---|---
Download ISO image | <https://www.archlinux.org/download/>
cfdisk ou fdisk | Executar particionamento do sistema
mkfs.ext4 /dev/sda1 | Sistema de arquivos ext4
mkswap /dev/sda2 | Sistema de arquivo swap
swapon /dev/sda2 | Ativação do uso da swap
mount /dev/sda1/mnt | Montar o sistema linux básico
wifi-menu | Configurar o acesso wi-fi
pacstrap /mnt base base-devel | Instalação dos pacotes básicos do sistema
pacstrap /mnt >> /mnt/etcfstab | Gerar arquivo FSTAB
arch-chroot /mnt | /mnt definido como raíz do sistema
passwd | Defir senha do root
pacman -S grub os-prober | Instalar pacotes adicionais
mkdir /boot/grub | Opcional, necessário se a configuração do grub falhar
grub-mkconfig -o /boot/grub/grub.cfg   | Gerar arquivo de configuração do GRUB
grub-install /dev/sda | Instalação do boot loader na MBR
exit | Sair da sessão
reboot | Reiniciar


## Gerenciar pacotes Debian

Os comandos devem ser executados como root.

Comando | Descrição
---|---
dpkg -i pacote.deb | Instala um pacote
dpkg -r pacote.deb | Remove um pacote
dpkg -p pacote.deb | Remove o pacote os arquivos de configuração
dpkg -I pacote.deb | Informação sobre o pacote
apt-get update | Atualiza a lista de repositórios
apt-get upgrade | Atualiza todos os softwares
apt-get dist-upgrade | Atualiza a distribuição
apt-cache search pacote | Procura um pacote 
apt-get remove pacote | Remove o pacote e suas dependências
apt-get remove --purge pacote | Remove o pacotes, suas dependência e arquivos
apt-get -f install | Verifica as dependências automaticamente
apt-get -d pacote | Faz apenas o download do pacote
apt-get -i reinstall pacote | Reinstala o pacote
apt-get clean | Remove os pacotes que foram baixados
apt-cdrom add | Adiciona CD-ROM com pacotes ao repositório
apt-get source pacote | Faz download do código fonte do pacote

## Gerenciar pacotes Red Hat

Comandos | Descrição
---|---
rpm -i | Instala o pacote
rpm -F | Instala pacote apenas e uma versão prévia já existir
rpm -iv | Instala mostrando detalhes
rpm -U | Atualiza um pacote
rpm -q | Consulta se um pacote esta instalado
rpm -qa | Mostra todos os pacotes instalados
rpm -qf arquivo | Mostra o pacote o qual o arquivo faz parte
rpm -qi pacote | Apresenta informações detalhadas do pacote
rpm -ql pacote | Listas os arquivos pertencentes ao pacote
rpm -qd pacote | Apresenta uma lista de documentação do pacote
rpm -qc pacote | Apresenta uma lista de arquivos de configuração 
rpm -i --nodeps | Não verifica se há dependências ao instalar um pacote
rpm -e pacote | Remove o pacote






## Sobre o autor:
- [Meus cursos](https://profjulianoramos.github.io/cursos/)
- [Meu currículo](https://profjulianoramos.github.io/curriculo/)
- [Aula particular e consultoria](https://profjulianoramos.github.io/consultoria/)
- [Meu livro sobre Servidores Linux](https://www.casadocodigo.com.br/products/livro-admin-linux?_pos=1&_sid=d71091948&_ss=r){:target="_blank"}


Commits
- 16/06/2020 - 17:48 - Primeira atualização
- 16/06/2020 - 18:29 - Adicionado Permissões e FHS
- 16/06/2020 - 20:21 - Adicionado comandos instalação arch e gerenciamento de pacotes Debian
- 16/06/2020 - Mudança do título do artigo (comandos lpi --> Comandos Linux em uma página)
- 16/06/2020 - 20:51 - Adicionado pacotes RPM
- 16/06/2020 - 21:12 - Alterado erro de escrita no atalho CTRL+Z (Rogério Chagas)
- 21/06/2020 - 11:58 - Linha 186 FHS mnt estava escrito mnnt, observação de (Inseto social)
  