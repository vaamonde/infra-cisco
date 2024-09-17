#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 16/09/2024<br>
#Data de atualização: 16/09/2024<br>
#Versão: 0.01<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>
#Testado e homologado o Cisco Packet Tracer 8.2.x x64<br>

Site Oficial do Netacad: https://www.netacad.com/pt-br<br>
Cursos Oficiais do Cisco Packet Tracer: https://www.netacad.com/pt-br/courses/packet-tracer<br>
Site Oficial do Dev do Cisco Packet Tracer: https://www.packettracernetwork.com/<br>
MEGA.nz do Projeto Bora para Prática: https://mega.nz/folder/Co9GHIyK#2kzNnN7XzImP01M1SyRm2g/folder/vll2iSDI

O QUE É E PARA QUE SERVER O CISCO PACKET TRACER: O Packet Tracer é um programa educacional gratuito que permite simular uma rede de computadores, através de equipamentos e configurações presente em situações reais. O programa apresenta uma interface gráfica simples, com suportes multimídia que auxiliam na confecção das simulações.

#01_ Verificando as Informações do Sistema Operacional Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#OBSERVAÇÃO IMPORTANTE: Linux Mint 22.x é derivado do Ubuntu Desktop 24.04.x Noble Numbat

#verificando as versões e codinome do sistema operacional
sudo cat /etc/os-release
sudo cat /etc/lsb-release

#verificando a versão do ambiente gráfico
sudo cinnamon --version

#verificando informações de hardware e processador
#opções do comando inxi: -C (cpu), -M (machine), -S (system), -f (flags), -xxx (extra 3)
sudo inxi -CMSfxxx
sudo lscpu

#modo gráfico para verificar as informações de sistema operacional e hardware
Menu
	Informações do Sistema
```

#02_ Atualização do Sistema Operacional Linux Mint<br>
```bash
#atualizando o sistema operacional via MintUpdate (Recomendado)
_ Atualização do sistema utilizando o MintUpdate;
_ Atualização do sistema utilizando o Apt;

#atualizando o sistema operacional via Terminal
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#recomendo utilizando o comando: apt - o comando: apt-get e considerado obsoleto
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
sudo apt clean
```

#03_ Download do Cisco Packet Tracer para Linux<br>
```bash
Link Oficial do Netacad: https://www.netacad.com/pt-br/courses/packet-tracer
Link Oficial do Packet Tracer Network: https://www.packettracernetwork.com/
Link do Mega.nz do Bora para Prática: https://mega.nz/folder/Co9GHIyK#2kzNnN7XzImP01M1SyRm2g/folder/vll2iSDI

DICA: RECOMENDO VOCÊ FAZER UMA CONTA NO NETACAD DA CISCO NO CURSO GRATUITO DO CISCO PACKET
TRACER DISPONÍVEL NA PLATAFORMA NO LINK: 
https://skillsforall.com/pt/learningcollections/cisco-packet-tracer?courseLang=pt-BR

PARA CRIAR UMA CONTA NO NETACAD ACESSE O LINK: https://id.cisco.com/signin/register
```

#04_ Instalando o Cisco Packet Tracer no Linux Mint<br>
```bash
#instalar o Cisco Packet Tracer em modo Gráfico no Linux Mint 22.x
01) Na pasta de Download, clicar duas vezes no Instalador do Cisco Packet Tracer;
02) Na tela do Gdebi clique em: <Instalar Pacote>.
    (Digite a sua senha para instalar o pacote)
03) Na tela: Software License Agreement clique em: <Next>
04) Marque a opção: do you accept the terms of this EULA?: <Yes> clique em: <Next>

#OBSERVAÇÃO IMPORTANTE: se você utilizar o Gdebi para instalar o Cisco Packet Tracer e apresentar
#uma falha no final da instalação, recomendo utilizar o comando: dpkg para forçar a instalação em 
#modo Terminal. UTILIZAR ESSE PROCEDIMENTO SOMENTE SE TIVER FALHA NA INSTALAÇÃO EM MODO GRÁFICO.

#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#instalando o Cisco Packet Tracer via linha de comando no Linux Mint 22.x
#opção do comando dpkg: -i (install)
sudo dpkg -i CiscoPacketTracer*.deb
	Na tela de: Configurando PacketTracer pressione Enter em: <OK>
	Na tela de: Do you accept the terms of this EULA? selecione: <Sim> e <Enter>

#OBSERVAÇÃO IMPORTANTE: NO LINUX MINT 22.x QUE É BASEADO NO UBUNTU 24.04.x A BIBLIOTECA DO MESA:
#libgl1-mesa-glx FOI DESCONTINUADA, SENDO NECESSÁRIO FAZER SUA INSTALAÇÃO MANUAL PARA ATENDER AS
#DEPENDÊNCIAS DO CISCO PACKET TRACER VERSÃO 8.2.x

#download da Biblioteca Libgl1-Mesa-GLX no Linux Mint 22.x (Link atualizado em: 11/09/2024)
wget http://mirrors.edge.kernel.org/ubuntu/pool/universe/m/mesa/libgl1-mesa-glx_23.0.4-0ubuntu1~23.04.1_amd64.deb

#instalando a Biblioteca Libgl1-Mesa-GLX
#opção do comando dpkg: -i (install)
sudo dpkg -i libgl1-mesa-glx*.deb
```

#05_ Verificando se todas as Bibliotecas do Cisco Packet foram instaladas no Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#verificando as dependência do binário do Cisco Packet Tracer
#opção do comando ldd: -v (verbose)
sudo ldd -v /opt/pt/bin/PacketTracer

#filtrando as dependências não encontrado do Cisco Packet Tracer
#opção do redirecionador |: Conecta a saída padrão com a entrada padrão de outro comando
sudo ldd /opt/pt/bin/PacketTracer | grep "not found"

#INSTALANDO AS DEPENDÊNCIAS DO CISCO PACKET TRACER NO LINUX MINT 22.x
#opção da contra barra (\): criar uma quebra de linha no terminal
sudo apt install libqt5networkauth5 libqt5script5 libqt5scripttools5 libqt5texttospeech5 libqt5positioning5 \
libqt5qml5 libqt5webchannel5 libqt5qmlmodels5 libqt5quick5 libqt5webenginecore5 libqt5webenginewidgets5 git \
vim python3 libqt5websockets5 libqt5multimedia5

#OBSERVAÇÃO IMPORTANTE: o tempo todo a Biblioteca LibSSL sofre alteração de versão, antes de baixar a versão
#acesse o site: http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/ e veja qual a versão atual, altere
#o script e faça o download.

#Resolvendo a falha das bibliotecas libssl.so.1.1 e libcrypto.so.1.1 no Linux Mint 22.x
#opção do comando dpkg: -i (install)
#opção do redirecionador |: Conecta a saída padrão com a entrada padrão de outro comando
#link de download da Biblioteca do LibSSL (atualizado no dia: 04/08/2024)
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.23_amd64.deb
sudo dpkg -i libssl1.1_1.1.1*.deb

#filtrando as dependências não encontrado do Cisco Packet Tracer
#opção do redirecionador |: Conecta a saída padrão com a entrada padrão de outro comando	
sudo ldd /opt/pt/bin/PacketTracer | grep "not found"
```