Autor: Robson Vaamonde<br>
Procedimentos em TI: http://procedimentosemti.com.br<br>
Bora para Prática: http://boraparapratica.com.br<br>
Robson Vaamonde: http://vaamonde.com.br<br>
Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
LinkedIn Robson Vaamonde: https://www.linkedin.com/in/robson-vaamonde-0b029028/<br>
Github Procedimentos em TI: https://github.com/vaamonde<br>
Data de criação: 16/05/2024<br>
Data de atualização: 27/04/2025<br>
Versão: 0.08<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.<br>
#02_ SEGUNDA ETAPA: Backup das Configurações do Cisco IOS do Primeiro Switch Cisco Catalyst Layer 2 2960<br>
#03_ TERCEIRA ETAPA: Backup das Configurações do Cisco IOS do Primeiro Router Cisco 1941.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do Backup Restore  do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Backup Restore](http://img.youtube.com/vi/0aw2uGtnBJw/0.jpg)](https://www.youtube.com/watch?v=0aw2uGtnBJw "Backup Restore")

Link da vídeo aula: https://www.youtube.com/watch?v=0aw2uGtnBJw

## PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.

```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: SEU_USUÁRIO
Password: SUA_SENHA

sw-01> enable
Password: SUA_SENHA_SEGURA

sw-01#
```

## SEGUNDA ETAPA: Backup das Configurações do Cisco IOS do Primeiro Switch Cisco Catalyst Layer 2 2960

02. Visualizando a versão do Cisco IOS e informações do Hardware do Switch Layer 2 2960.

**DICA-01:** o comando: *show version* é utilizado para verificar a versão de hardware e do Cisco IOS do Switch ou Router.

**DICA-02:** atualmente a versão utilizada nos hardware da Cisco é a 15.x (ou superior, dependendo do modelo)

**OBSERVAÇÃO-01:** as informações de Memória RAM em equipamentos da Cisco estão em: *Kbytes* ou em: *Bytes*, sendo necessário fazer a conversão para: *MBytes* para facilitar a leitura.

**OBSERVAÇÃO-02:** esse comando também mostrar as informações referente a *Configuração do Registro de Inicialização* do equipamento para efeito de manutenção ou Reset.

```bash
sw-01# show version
  ...
  Switch uptime is 39 minutes
  System returned to ROM by power-on
  System image file is "flash:c2960-lanbasek9-mz.150-2.SE4.bin"
  ...
  cisco WS-C2960-24TT-L (PowerPC405) processor (revision B0) with 65536K bytes of memory.
  65536KB / 1000 = 65MB (65MB de Memória RAM)
   1 Virtual Ethernet interface
  24 FastEthernet interfaces
   2 Gigabit Ethernet interfaces
  ...
  64K bytes of flash-simulated non-volatile configuration memory.
  Configuration register is 0xF
sw-01#
```

03. Visualizando as informações da inicialização do Switch Layer 2 2960.

**DICA-03:** o comando: *show boot* é utilizado para verificar os arquivos de configuração de inicialização e qual binário do Cisco IOS está habilitado no Switch.

**OBSERVAÇÃO-03:** essas informações são importante para o processo de quebra de senha do Switch se necessário.

```bash
sw-01# show boot
  BOOT path-list      : 2960-lanbasek9-mz.150-2.SE4.bin    (Binário do Cisco IOS)
  Config file         : flash:/config.text                 (Arquivo de Inicialização do Cisco IOS)
  Private Config file : flash:/private-config.text         (Arquivo de Segurança da Inicialização)
sw-01#
```

04. Visualizando as informações do Flash Card (Memória de Massa) do Switch Layer 2 2960.

**DICA-04:** a memória de massa (Flash Card) em Switch geralmente são Chips soldados ou módulos internos.

**OBSERVAÇÃO-04:** diferente do Router, a memória Flash em Switch não pode ser acessada sem desmontar (Abrir) o equipamento (Caixa).

```bash
sw-01# show flash:
  64016384 bytes total (59344171 bytes free)
sw-01#

sw-01# dir flash:
  64016384 bytes total (59344171 bytes free)
  64016384 Bytes Total / 1000 = 64 MB
  59344171 Bytes Free  / 1000 = 60 MB
sw-01#
```

05. Salvando as configurações da memória RAM para a memória NVRAM.

**DICA-05:** nunca esqueça de salvar as configurações.

```bash
sw-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
sw-01#
```

06. Salvando as configurações da memória NVRAM para a memória FLASH.

**DICA-06:** deixar sempre um backup das configuração na Memória FLASH.

```bash
sw-01# copy startup-config flash: 
  Destination filename [startup-config]?
  1758 bytes copied in 0.416 secs (4225 bytes/sec)
sw-01#

sw-01# dir flash:
  5  -rw-        1758          <no date>  startup-config
sw-01#
```

07. Salvando as configurações da memória NVRAM para o Servidor TFTP.

**DICA-07:** o serviço de TFTP (Trivial File Transfer Protocol) utiliza o Protocolo: *UDP* na Porta Padrão: *69*, por padrão está ativo no Servidor do Cisco Packet Tracer, precisando apenas habilitar o endereço IPv4 ou IPv6.

**OBSERVAÇÃO-05:** o protocolo UDP (User Datagram Protocol) não é confiável, porque ele não exige confirmação de recebimento.

**OBSERVAÇÃO-06:** o protocolo TFTP foi escolhido pela Cisco para ser o sistema padrão de Atualização e Backup dos Switch e Router.

```bash
!Verificando o Status do Serviço do Servidor TFTP
!OBSERVAÇÃO IMPORTANTE: RECOMENDO, NESSE CENÁRIO REMOVER TODOS OS ARQUIVOS NO TFTP
!PARA FACILITAR A ANALISE DOS BACKUPS ENVIADOS.
Server-01
  Services
    TFTP
      Service: ON (Enable)
        <Remove File>

!Pingando o Servidor de TFTP
sw-01# ping 192.168.1.1

!Verificando o Arquivo Startup-Config da NVRAM
sw-01# dir nvram:
  238  -rw-        1679          <no date>  startup-config
  1679 bytes total (237588 bytes free)
    1679 Bytes Total / 1000 = 1,7 KB
  237588 Bytes Free  / 1000 = 238 KB
sw-01#

!Copiando o arquivo de configuração da NVRAM para o Servidor TFTP
sw-01# copy startup-config tftp:
  Address or name of remote host []? 192.168.1.1
  Destination filename [sw-01-confg]?
  Writing startup-config...!!
  [OK - 1758 bytes]
  1758 bytes copied in 0.013 secs (135230 bytes/sec)
sw-01#

!Verificando o Backup no Servidor TFTP
Server-01
  Services
    TFTP
      File
```

08. Salvando a imagem do Cisco IOS do Switch Layer 2 2960 para o Servidor TFTP.

**DICA-08:** as imagens do Cisco IOS estão no formato: *BIN (binário)* e compactadas (m=RAM | z=zip)

**OBSERVAÇÃO-07:** não é aconselhável alterar o nome da imagem, ela segue um padrão de nomenclatura que é recomendado pela Cisco.

**EXEMPLO-01:** 2960-lanbasek9-mz.150-2.SE4.bin <br>
A) Primeira parte: 2960 plataforma/família do equipamento;<br>
B) Segunda parte: lanbasek9 indicação do package/funcionalidade do IOS;<br>
C) Terceira parte: compactação da Imagem m=RAM | z=zip;<br>
D) Quarta parte: 150-2.SE4 versão do IOS;<br>
E) Quinta parte: .bin extensão do arquivo binário do Cisco IOS).<br>

**CUIDADO:** como o Cisco IOS é uma sub-derivação do *Unix/BSD* (Berkeley Software Distribution), ele também é Case Sensitive (faz diferença de Maiúscula/Minúscula).

```bash
!Verificando o Binário do Cisco IOS do Switch
sw-01# dir flash:
  1  -rw-     4414921          <no date>  2960-lanbasek9-mz.150-2.SE4.bin
sw-01#

sw-01# copy flash: tftp:
  Source filename []? 2960-lanbasek9-mz.150-2.SE4.bin
  Address or name of remote host []? 192.168.1.1
  Destination filename [2960-lanbasek9-mz.150-2.SE4.bin]?
  Writing 2960-lanbasek9-mz.150-2.SE4.bin...
  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  [OK - 4670455 bytes]
  4670455 bytes copied in 0.057 secs (6587503 bytes/sec)
sw-01#

!Verificando o Backup no Servidor TFTP
Server-01
  Services
    TFTP
```

09. Salvando as configurações do Running Config (RAM) ou Startup Config (NVRAM) no VSCode.

**DICA-09:** esse é o método mais simples de backup das configurações do Switch ou Router

**OBSERVAÇÃO-08:** recomendo sempre utilizar um *Editor de Texto Profissional* para não modificar a estrutura do arquivo de configuração no momento de copiar e colar, não utilizar, por exemplo: MS Word, Wordpad, etc..., esses editores de Texto modificam as codificações dos arquivos prejudicando no processo de automação dos scripts.

**DICA-10:** copiar as informações do Running Config (RAM) ou Startup Config (NVRAM) a partir da primeira: *! (exclamação)* até a última linha com o comando: *end*.

```bash
!Visualizando as Configuração da RAM
sw-01# show running-config

!Utilize *BARRA DE ESPAÇO* para descer até a última linha do arquivo de configuração (MORE)
!Selecione a partir da primeira ! (exclamação) do Running-Config
!Não Selecione a linha: Current configuration : 1799 bytes

!
version 15.0
...
end

!Copiar o conteúdo com o botão direito do mouse e selecionar: Copy
!Salvar o Conteúdo no VSCode: Ctrl + V (ou botão direito colar).

!Saindo do modo EXEC Privilegiado
sw-01# disable

!Saindo da conexão do SSH do Switch
sw-01> exit
```

**OBSERVAÇÃO IMPORTANTE:** no comando: show running-config algumas opções não aparece no arquivo de configuração como as linhas:<br> 
A) crypto key generate rsa general-keys modulus 1024;<br>
B) no caso das senhas do Tipo-5 (secret) ou Tipo-7 (password) elas estão criptografadas, na hora de fazer uma restauração (restore) será necessário alterar as senhas;<br>
C) outra detalhe está relacionado as Interfaces de Rede que o comando: no shutdown não está no arquivo sendo necessário;<br>
D) adicionar no backup a configuração de data e hora, etc...<br>
E) sempre é necessário fazer ajustes no processo de restauração de backups nos Switches ou Routers da Cisco.

## TERCEIRA ETAPA: Backup das Configurações do Cisco IOS do Primeiro Router Cisco 1941.

01. Visualizando a versão do Cisco IOS e informações do Hardware do Router.

**DICA-11:** em roteadores esse comando fornece informações de licenciamento do hardware.

**OBSERVAÇÃO-09:** igual no Switch, esse comando fornece informações de inicialização do IOS do Router, utilizado principalmente para manutenção ou Quebra de Senha do equipamento.

**OBSERVAÇÃO-10:** em roteadores não temos o comando: *show boot*, essa opção só existe no Switch Cisco Catalyst Layer 2 ou 3.

```bash
rt-01# show version
  ROM: System Bootstrap, Version 15.1(4)M4, RELEASE SOFTWARE (fc1)
  cisco1941 uptime is 18 minutes, 32 seconds
  System returned to ROM by power-on
  System image file is "flash0:c1900-universalk9-mz.SPA.151-1.M4.bin"
  Last reload type: Normal Reload
  ...
  Cisco CISCO1941/K9 (revision 1.0) with 491520K/32768K bytes of memory.
  Processor board ID FTX152400KS
  2 Gigabit Ethernet interfaces
  DRAM configuration is 64 bits wide with parity disabled.
  255K bytes of non-volatile configuration memory.
  249856K bytes of ATA System CompactFlash 0 (Read/Write)
  249856KB / 1000 = 250MB (250MB de Memória RAM Disponível)
  ...
  Configuration register is 0x2102
rt-01#
```

02. Visualizando informações do Flash Card (Memória de Massa) do Router 1941.

**DICA-12:** em roteadores temos vários módulos de memória Flash Card, utilizado principalmente como Redundância caso algum Flash Card tenha problema.

**OBSERVAÇÃO-11:** o acesso a memória Flash em roteadores é feita utilizando módulos externos, geralmente não são soldados nos modelos antigos, modelos atuais está vindo chipado (soldado).

```bash
rt-01# show flash:
  [33849219 bytes used, 221896413 available, 255744000 total]
  249856K bytes of processor board System flash (Read/Write)
rt-01#

rt-01# dir flash0:
  255744000 bytes total (221896413 bytes free)
  255744000 Bytes Total = 256MB
  33847587 Bytes Used = 34MB
  221896413 Bytes Available = 222MB
rt-01#
```

03. Fazendo o Backup das Configurações e do Cisco IOS para o TFTP.

**DICA-13:** procedimento é igual do Switch Cisco Catalyst Layer 2 2960.

```bash
!Salvando as configurações da memória RAM para memória NVRAM
rt-01# copy running-config startup-config
  Destination filename [startup-config]? 
  Building configuration...
  [OK]
rt-01#

!Salvando as configurações da memória NVRAM para a memória FLASH
rt-01# copy startup-config flash: 
  Destination filename [startup-config]? 
  1453 bytes copied in 0.416 secs (3492 bytes/sec)
rt-01#

!Salvando as configurações da memória NVRAM para o Servidor TFTP

!Pingando o Servidor de TFTP
rt-01# ping 192.168.1.1

!Verificando o Arquivo Startup-Config da NVRAM
rt-01# dir nvram:
  238  -rw-        1349          <no date>  startup-config
rt-01#

!Copiando o arquivo de configuração da NVRAM para o Servidor TFTP
rt-01# copy startup-config tftp:
  Address or name of remote host []? 192.168.1.1
  Destination filename [rt-01-confg]?
  Writing startup-config...!!
  [OK - 1453 bytes]
  1453 bytes copied in 0 secs
rt-01#

!Salvando a imagem do Cisco IOS do Router 1941 para o Servidor TFTP
rt-01# copy flash: tftp:
  Source filename []? c1900-universalk9-mz.SPA.151-4.M4.bin
  Address or name of remote host []? 192.168.1.1
  Destination filename [c1900-universalk9-mz.SPA.151-4.M4.bin]? 
  Writing c1900-universalk9-mz.SPA.151-4.M4.bin...
  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  [OK - 33591768 bytes]
  33591768 bytes copied in 0.605 secs (5829746 bytes/sec
rt-01#

!Saindo do modo EXEC Privilegiado
rt-01# disable

!Verificando os Backups no Servidor TFTP
Server-01
  Services
    TFTP
```