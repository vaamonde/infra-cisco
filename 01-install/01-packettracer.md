#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 16/09/2024<br>
#Data de atualização: 27/03/2025<br>
#Versão: 0.05<br>
#Testado e homologado no Linux Mint 22 Wilma e 22.1 Xia x64<br>
#Testado e homologado o Cisco Packet Tracer 8.2.x x64<br>

Conteúdo estudado nessa instalação:<br>
#01_ Verificando as Informações do Sistema Operacional Linux Mint<br>
#02_ Atualização do Sistema Operacional Linux Mint<br>
#03_ Download do Cisco Packet Tracer para Linux<br>
#04_ Instalação das Dependências e Bibliotecas do Cisco Packet Tracer no Linux Mint<br>
#05_ Instalando o Cisco Packet Tracer no Linux Mint<br>
#06_ Verificando se todas as Bibliotecas do Cisco Packet foram instaladas no Linux Mint<br>
#07_ Executando o Cisco Packet Tracer pela Primeira Vez no Linux Mint<br>
#08_ Configurações Básicas do Cisco Packet Tracer no Linux Mint<br>
#09_ Download do Cisco Packet Tracer para Windows<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO INSTALAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A INSTALAÇÃO COM A SEGUINTE FRASE: *Instalação do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

Site Oficial do Netacad: https://www.netacad.com/pt-br<br>
Cursos Oficiais do Cisco Packet Tracer: https://www.netacad.com/pt-br/courses/packet-tracer<br>
Site Oficial do Dev do Cisco Packet Tracer: https://www.packettracernetwork.com/<br>
MEGA.nz do Projeto Bora para Prática: https://mega.nz/folder/Co9GHIyK#2kzNnN7XzImP01M1SyRm2g/folder/vll2iSDI

**O QUE É E PARA QUE SERVER O CISCO PACKET TRACER:** O Packet Tracer é um programa educacional gratuito que permite simular uma rede de computadores, através de equipamentos e configurações presente em situações reais. O programa apresenta uma interface gráfica simples, com suportes multimídia que auxiliam na confecção das simulações.

[![Instalação Packet Tracer](http://img.youtube.com/vi/GVG1LrHN2Cg/0.jpg)](https://www.youtube.com/watch?v=GVG1LrHN2Cg "Instalação Packet Tracer")

Link da vídeo aula: https://www.youtube.com/watch?v=GVG1LrHN2Cg

## 01_ Verificando as Informações do Sistema Operacional Linux Mint<br>

**OBSERVAÇÃO IMPORTANTE:** Linux Mint 22.x é derivado do Ubuntu Desktop 24.04.x Noble Numbat

```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#verificando as versões e codinome do sistema operacional
sudo cat /etc/os-release
sudo cat /etc/lsb-release

#verificando a versão do ambiente gráfico Cinnamon
sudo cinnamon --version

#modo gráfico para verificar as informações de sistema operacional e hardware
Menu
  Informações do Sistema
```

## 02_ Atualização do Sistema Operacional Linux Mint<br>
```bash
#atualizando o sistema operacional via MintUpdate (Recomendado)
A) Atualização do sistema utilizando o MintUpdate;
B) Atualização do sistema utilizando o Apt;

#atualizando o sistema operacional via Terminal
Terminal: Ctrl + Alt + T

#recomendo utilizando o comando: apt - o comando: apt-get é considerado obsoleto
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
sudo apt clean
```

## 03_ Download do Cisco Packet Tracer para Linux<br>

Link Oficial do Netacad: https://www.netacad.com/pt-br/courses/packet-tracer<br>
Link Oficial do Packet Tracer Network: https://www.packettracernetwork.com/<br>
Link do Mega.nz do Bora para Prática: https://mega.nz/folder/Co9GHIyK#2kzNnN7XzImP01M1SyRm2g/folder/vll2iSDI<br>

**DICA:** RECOMENDO VOCÊ FAZER UMA CONTA NO *NETACAD DA CISCO* NO CURSO GRATUITO DO **CISCO PACKET TRACER* DISPONÍVEL NA PLATAFORMA NO LINK: Link: https://skillsforall.com/pt/learningcollections/cisco-packet-tracer?courseLang=pt-BR

PARA CRIAR UMA CONTA NO NETACAD ACESSE O LINK: https://id.cisco.com/signin/register

## 04_ Instalação das Dependências e Bibliotecas do Cisco Packet Tracer no Linux Mint<br>

**OBSERVAÇÃO IMPORTANTE:** NO LINUX MINT 22.x QUE É BASEADO NO UBUNTU 24.04.x A BIBLIOTECA DO MESA: *libgl1-mesa-glx* FOI DESCONTINUADA, SENDO NECESSÁRIO FAZER SUA INSTALAÇÃO MANUAL PARA ATENDER AS DEPENDÊNCIAS DO CISCO PACKET TRACER VERSÃO 8.2.x

**OBSERVAÇÃO:** Antes de baixar a Biblioteca acesse o mirror para verificar qual versão está disponível para download: http://mirrors.edge.kernel.org/ubuntu/pool/universe/m/mesa/

```bash
#Link direto do download da Biblioteca *Libgl1-Mesa-GLX no Linux Mint 22.x* (Link atualizado em: 25/01/2025)<br>
wget http://mirrors.edge.kernel.org/ubuntu/pool/universe/m/mesa/libgl1-mesa-glx_23.0.4-0ubuntu1~22.04.1_amd64.deb

#instalando a Biblioteca Libgl1-Mesa-GLX
#opção do comando dpkg: -i (install), * (all/tudo)
sudo dpkg -i libgl1-mesa-glx*.deb
```

**OBSERVAÇÃO IMPORTANTE:** NO LINUX MINT 22.x QUE É BASEADO NO UBUNTU 24.04.x A BIBLIOTECA DO SSL: *libssl e libcrypto* FOI DESCONTINUADA, SENDO NECESSÁRIO FAZER SUA INSTALAÇÃO MANUAL PARA ATENDER AS DEPENDÊNCIAS DO CISCO PACKET TRACER VERSÃO 8.2.x.

*OBSERVAÇÃO:* Antes de baixar a Biblioteca acesse o mirror para verificar qual versão está disponível para download: http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/

```bash
#Link direto do download da Biblioteca LibSSL no Linux Mint 22 (Link atualizado em: 27/03/2025)
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.24_amd64.deb

#instalando a Biblioteca LibSSL
#opção do comando dpkg: -i (install), * (all/tudo)
sudo dpkg -i libssl1.1_1.1.1*.deb

#INSTALANDO AS DEPENDÊNCIAS DO CISCO PACKET TRACER NO LINUX MINT 22.x
#opção da contra barra (\): criar uma quebra de linha no terminal
sudo apt install libqt5networkauth5 libqt5script5 libqt5scripttools5 libqt5texttospeech5 libqt5positioning5 \
libqt5qml5 libqt5webchannel5 libqt5qmlmodels5 libqt5quick5 libqt5webenginecore5 libqt5webenginewidgets5 git \
vim python3 libqt5websockets5 libqt5multimedia5 libqt5xml5t64 libqt5sql5t64
```

## 05_ Instalando o Cisco Packet Tracer no Linux Mint<br>
```bash
#instalar o Cisco Packet Tracer em modo Gráfico no Linux Mint 22.x
01) Na pasta de Download, clicar duas vezes no Instalador do Cisco Packet Tracer;
02) Na tela do Gdebi clique em: <Instalar Pacote>.
    (Digite a sua senha para instalar o pacote clique em: <Autenticar>)
    Software adicional deve ser instalado: <Continuar>
03) Na tela: Software License Agreement clique em: <Next>
04) Marque a opção: do you accept the terms of this EULA?: <Yes> clique em: <Next>
```

**OBSERVAÇÃO IMPORTANTE:** Se você utilizar o *Gdebi* para instalar o Cisco Packet Tracer e apresentar uma falha no final da instalação, recomendo utilizar o comando: **dpkg** para forçar a instalação em modo Terminal (UTILIZAR ESSE PROCEDIMENTO SOMENTE SE TIVER FALHA NA INSTALAÇÃO EM MODO GRÁFICO).

```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#instalando o Cisco Packet Tracer via linha de comando no Linux Mint 22.x
#opção do comando dpkg: -i (install), * (all/tudo)
sudo dpkg -i CiscoPacketTracer*.deb
  Na tela de: Configurando PacketTracer pressione Enter em: <OK>
  Na tela de: Do you accept the terms of this EULA? selecione: <Sim> e <Enter>
```

## 06_ Verificando se todas as Bibliotecas do Cisco Packet Tracer foram instaladas no Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#verificando as dependência do binário do Cisco Packet Tracer
#opção do comando ldd: -v (verbose)
sudo ldd -v /opt/pt/bin/PacketTracer

#filtrando as dependências não encontradas do Cisco Packet Tracer
#opção do redirecionador |: Conecta a saída padrão com a entrada padrão de outro comando
sudo ldd /opt/pt/bin/PacketTracer | grep "not found"
```

## 07_ Executando o Cisco Packet Tracer pela Primeira Vez no Linux Mint<br>
```bash
#execução do Cisco Packet Tracer via Menu do Linux Mint
Menu
  Busca Indexada: Packet Tracer
    Would you like to run multi-user when application starts? <Yes>

#execução do Cisco Packet Tracer via Terminal do Linux Mint
Terminal: Ctrl + Alt + T
  packettracer

#se autenticação do Netacad no Cisco Packet Tracer
Sign in using one of the following options:
  (ON) Keep me logged in (for 3 months)
  Login server: Worldwide
  <Cisco Network Academy>

#verificando a versão do Cisco Packet Tracer
Help
  About
    Version: 8.2.2.x
```

## 08_ Configurações Básicas do Cisco Packet Tracer no Linux Mint<br>
```bash
#habilitando recursos importantes no Cisco Packet Tracer
Options
  Preferences
    Interface
      (OFF) Show Device Model Labels (DISABLE)
      (OFF) Show Device Name Labels (DISABLE)
      (ON) Align logical workspace objects (ENABLE)
      (ON) Enable Cable Length Effects (ENABLE)
      (ON) Align physical workspace objects (ENABLE)
    Show/Hide
      (ON) Show Wireless Boundary (ENABLE)
      (ON) Show Wireless Color Gradient (ENABLE)
  <Close>
```

## 09_ Download do Cisco Packet Tracer para Microsoft Windows<br>

Link Oficial do Netacad: https://www.netacad.com/pt-br/courses/packet-tracer<br>
Link Oficial do Packet Tracer Network: https://www.packettracernetwork.com/<br>
Link do Mega.nz do Bora para Prática: https://mega.nz/folder/Co9GHIyK#2kzNnN7XzImP01M1SyRm2g/folder/vll2iSDI<br>

**DICA:** RECOMENDO VOCÊ FAZER UMA CONTA NO NETACAD DA CISCO NO CURSO GRATUITO DO CISCO PACKET TRACER DISPONÍVEL NA PLATAFORMA NO LINK:  https://skillsforall.com/pt/learningcollections/cisco-packet-tracer?courseLang=pt-BR

PARA CRIAR UMA CONTA NO NETACAD ACESSE O LINK: https://id.cisco.com/signin/register

```bash
#baixando o Cisco Packet Tracer pelo Netacad
Legacy Netacad
  Resources
    Download Packet Tracer
      Windows Desktop Version 8.2.x English
        Selecionar: 64 Bit Download

#instalando o Cisco Packet Tracer no Windows 10
Explorador de Arquivos
  Pasta Download
    Clicar duas vezes no software: CiscoPacketTracer*.exe

Deseja permitir que este aplicativo faça alterações no seu dispositivo?
  <Sim>

Setup - Cisco Packet Tracer 8.2.x-64Bit
  License Agreement
    (ON) I accept the agreement
  <Next>
  Select Destination Location
    Caminho Padrão
  <Next>
  Select Start Menu Folder
    Caminho Padrão
  <Next>
  Select Additional Tasks
    (ON) Create a desktop shortcut
    (ON) Create a Quick Launch shortcut
  <Next>
  Ready to Install
  <Install>
  Completing the Cisco Packet Tracer 8.2.x 64Bit Setup Wizard
    (OFF) Launch Cisco Packet Tracer
<Finish>

#executando o Cisco Packet Tracer no Windows
Clicar no Ícone no Desktop: Cisco Packet Tracer
  Would you like to run multi-user when application starts? <Yes>

Alerta de Segurança do Windows
  (ON) Redes privadas, como minha rede doméstica ou corporativa
  (ON) Redes públicas, como as de aeroportos e cafeterias
<Permitir acesso>

#habilitando recursos importantes no Cisco Packet Tracer
Options
  Preferences
    Interface
      (OFF) Show Device Model Labels (DISABLE)
      (OFF) Show Device Name Labels (DISABLE)
      (ON) Align logical workspace objects (ENABLE)
      (ON) Enable Cable Length Effects (ENABLE)
      (ON) Align physical workspace objects (ENABLE)
    Show/Hide
      (ON) Show Wireless Boundary (ENABLE)
      (ON) Show Wireless Color Gradient (ENABLE)
  <Close>
```