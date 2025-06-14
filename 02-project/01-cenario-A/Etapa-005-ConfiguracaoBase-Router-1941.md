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
Data de atualização: 22/05/2025<br>
Versão: 0.06<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Conhecendo os Novos Recursos de Configuração do Router Cisco 1941<br>
#02_ SEGUNDA ETAPA: Automatizando a Configuração do Primeiro Router Cisco 1941.<br>
#03_ TERCEIRA ETAPA: Verificando as Configurações do Primeiro Router Cisco 1941.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração Base Router 1941 do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Config Router 1941](http://img.youtube.com/vi/I3sAYWz20KM/0.jpg)](https://www.youtube.com/watch?v=I3sAYWz20KM "Config Router 1941")

Link da vídeo aula: https://www.youtube.com/watch?v=I3sAYWz20KM

## PRIMEIRA ETAPA: Conhecendo os Novos Recursos de Configuração do Router Cisco 1941

01. Habilitando o Log de Debug no Router.

**DICA-01:** recomendado habilitar o recurso de marcação de Data/Hora detalhado no Log de Debug (Depurar).

**OBSERVAÇÃO-01:** esse recurso é utilizado para análise detalhada de logs de protocolos de roteamento no Router, esse recurso não está disponível em Switch Cisco Catalyst Layer 2 2960 ou Layer 3 3560 que utiliza versões abaixo da 15.x (versão antiga 12.x não tem esse suporte).
```bash
Router (config)# service timestamps debug datetime msec
```

02. Habilitando o Tamanho Mínimo da Senha de Usuários e Serviços.

**DICA-02:** recomendo habilitar o recurso de tamanho mínimo da senha, isso aumenta o nível de segurança na criação de senhas de usuários ou serviços no roteador.

**OBSERVAÇÃO-02:** esse recurso não está disponível em Switch Cisco Catalyst Layer 2 2960 ou Layer 3 3560.
```bash
Router (config)# security passwords min-length 8
```

03. Aumentando o Nível de Segurança contra Força Bruta (Brute Force) no Acesso Remoto.

**DICA-03:** esse recurso é recomendado para aumentar o nível de segurança junto com o serviço do SSH para proteger o Router contra Ataque de Força Bruta.

**OBSERVAÇÃO-03:** período de tempo de bloqueio configurado em segundos (block-for 1 até 65535s = 1092m ou 18h)

**OBSERVAÇÃO-04:** tentativas de falhas de conexões em quantidade (attempts 1 até 65535)

**OBSERVAÇÃO-05:** dentro do período de tempo configurado em segundos (within 1 até 65535s = 1092m ou 18h)

**OBSERVAÇÃO-06:** esse recurso não está disponível em Switch Cisco Catalyst Layer 2 2960 mais está disponível no Switch Cisco Catalyst Layer 3 3560.
```bash
Router (config)# login block-for 120 attempts 2 within 60
```

## SEGUNDA ETAPA: Automatizando a Configuração do Primeiro Router Cisco 1941.

01. Utilizando o Visual Studio Code (VSCode) para automatizar as configurações do Cisco IOS.

**OBSERVAÇÃO-08:** recomendo sempre utilizar um *Editor de Texto Profissional* para criar os scripts e automatizar as tarefas de configuração do Cisco IOS, hoje em dia é indicado utilizar o Visual Studio Code (VSCode) junto com as Extensões: *Cisco IOS Syntax e Cisco Config Highlight* para facilitar essa configuração.

**DICA-04:** o caractere: *! (exclamação)* é utilizado como um recurso de *Comentário*, sua utilização server para comentar o código de automação do Cisco IOS ou para desativar um comando para não ser executado, *RECOMENDO FORTEMENTE DOCUMENTAR TODOS OS COMANDOS E PROCEDIMENTOS DE CONFIGURAÇÃO PARA FACILITAR O ENTENDIMENTO.*

**DICA-05:** para facilitar a leitura do código, recomendo utilizar o recurso de **Indentação de Código** usando a Tecla TAB (Tabulador/Tabulação) para cada nível que você está configurando o Cisco IOS, isso facilitada a análise de erros (Debug) do código.

```bash
         --- System Configuration Dialog ---

Would you like to enter the initial configuration dialog? [yes/no]: no <Enter>

Press RETURN to get started!

Router>
```
```python
!Acessando o modo EXEC Privilegiado
enable

  !Configuração de Data/Hora Router
  clock set 19:54:00 11 February 2025

  !Acessando o modo de Configuração Global de comandos
  configure terminal

    !Configuração do nome do router
    hostname rt-01

    !Habilitando o serviço de criptografia de senhas do Tipo-7 Password 
    service password-encryption

    !Habilitando o serviço de marcação de Data/Hora detalhado nos Logs
    service timestamps log datetime msec
    service timestamps debug datetime msec

    !Habilitando o tamanho do Buffer dos Logs na Memória RAM
    logging buffered 4096 

    !Desativando a resolução de nomes de domínio
    no ip domain-lookup

    !Configuração do Banner da mensagem do dia
    banner motd #AVISO: acesso autorizado somente a funcionarios#
    
    !Habilitando o comprimento mínimo da criação das senhas do Tipo-5 ou Tipo-7
    security passwords min-length 8

    !Habilitando o uso senha do Tipo-5 Secret para acessar o modo EXEC Privilegiado
    enable secret SUA_SENHA_SEGURA

    !Criação dos usuários locais utilizando senhas do Tipo-5 ou Tipo-7 e privilégios diferenciados
    username USUÁRIO_1 secret SUA_SENHA_SEGURA
    username USUÁRIO_2 password SUA_SENHA_NÃO_SEGURA
    username USUARIO_3 privilege 15 secret SUA_SENHA_SEGURA
    
    !Configuração do nome de domínio FQDN (Fully Qualified Domain Name)
    ip domain-name SEU_DOMÍNIO.BR

    !Criação da chave de criptografia e habilitando o serviço do SSH Server local
    crypto key generate rsa general-keys modulus 1024

    !Habilitando a versão 2 do serviço de SSH Server
    ip ssh version 2

    !Habilitando o tempo de inatividade para novas conexões do SSH Server
    ip ssh time-out 60

    !Habilitando o número máximo de tentativas de conexões simultâneas no SSH Server
    ip ssh authentication-retries 2
    
    !Bloqueando tentativas de conexões simultâneas com falha de autenticação no Router
    login block-for 120 attempts 2 within 60

    !Desativando os Serviços de Descobertas de equipamentos na rede
    no cdp run
    no lldp run

    !Acessando a linha console, porta padrão de acesso Out-of-Band (Fora da Banda)
    line console 0

      !Forçando fazer login local utilizando usuário e senha locais do switch
      login local

      !Habilitando senha de acesso do Tipo-7 Password
      password SUA_SENHA_NÃO_SEGURA

      !Sincronizando as mensagens de logs na tela
      logging synchronous

      !Habilitando o tempo de inatividade de uso do console
      exec-timeout 5 30
      
      !Saindo da configuração da linha console
      exit

    !Acessando as linhas virtuais de acesso remoto do Router
    line vty 0 4

      !Forçando fazer login local utilizando usuário e senha locais do Router
      login local

      !Habilitando senha de acesso do Tipo-7 Password
      password SUA_SENHA_NÃO_SEGURA

      !Sincronizando as mensagens de logs na tela
      logging synchronous

      !Habilitando o tempo de inatividade de uso da linha virtual
      exec-timeout 5 30

      !Configuração do tipo de protocolo de transporte de entrada
      transport input ssh

      !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
      end

  !Salvando as configurações da memória RAM para a memória NVRAM
  !OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
  !salvar automaticamente o script na hora da execução, fazendo a função de
  !<Enter> no final do script.
  write

```

## TERCEIRA ETAPA: Verificando as Configurações do Primeiro Router Cisco 1941.
```bash
!Visualizando as Configurações do Running-Config (RAM)
!OBSERVAÇÃO: A ÚNICA LINHA QUE NÃO APARECE NAS CONFIGURAÇÕES DO SSH É A: crypto key generate rsa
rt-01# show running-config
  Building configuration...

  Current configuration : 1763 bytes
  !
  ...
  !
  end
rt-01#
```
```bash
!Visualizando a Data e Hora do Router
rt-01# show clock
*0:21:17.962 UTC Mon Mar 1 1993
```
```bash
!Visualizando os Logs detalhados do Router
rt-01# show logging
Syslog logging: enabled (0 messages dropped, 0 messages rate-limited,
          0 flushes, 0 overruns, xml disabled, filtering disabled)

No Active Message Discriminator.

No Inactive Message Discriminator.

    Console logging: level debugging, 11 messages logged, xml disabled,
          filtering disabled
    Monitor logging: level debugging, 11 messages logged, xml disabled,
          filtering disabled
    Buffer logging:  disabled, xml disabled,
          filtering disabled

    Logging Exception size (4096 bytes)
    Count and timestamp logging messages: disabled
    Persistent logging: disabled

No active filter modules.

ESM: 0 messages dropped
    Trap logging: level informational, 11 message lines logged
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Line Console 0
rt-01# show running-config | section include con 0
  line con 0
    password 7 08701E1D290A00191308
    logging synchronous
    login local
    exec-timeout 5 30
rt-01#
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Line VTY
rt-01# show running-config | section include line vty
  line vty 0 4
    exec-timeout 5 30
    password 7 08701E1D290A00191308
    logging synchronous
    login local
    transport input ssh
  line vty 5 15
    login
rt-01#
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente do SSH
!OBSERVAÇÃO: ÚNICA LINHA QUE NÃO APARECE NAS CONFIGURAÇÃO É A: crypto key generate rsa
rt-01# show running-config | include ip ssh
  ip ssh version 2
  ip ssh authentication-retries 2
  ip ssh time-out 60
rt-01#
```
```bash
!Visualizando as configurações do SSH Server e Versão
rt-01# show ip ssh
  SSH Enabled - version 2.0
  Authentication timeout: 60 secs; Authentication retries: 2
rt-01#
```
```bash
!Visualizando das chaves públicas RSA do SSH Server
rt-01# show crypto key mypubkey rsa
  % Key pair was generated at: 21:44:0 UTC fevereiro 4 2025
  Key name: rt-01.SEU_DOMÍNIO.INTRA
    Storage Device: not specified
    Usage: General Purpose Key
    Key is not exportable.
    Key Data:
    00005d5c  00007c53  0000627e  00007a79  00005802  00000027  000071e7  000018cb
    00003fa6  000008b2  00000428  00001fac  00002e5d  00007dbf  00007fa8  00004273
    00001673  0000237d  000006af  00000dd9  0000370c  00004c8d  00003128  4aad
  % Key pair was generated at: 21:44:0 UTC fevereiro 4 2025
  Key name: rt-01.SEU_DOMÍNIO.INTRA.server
  Temporary key
    Usage: Encryption Key
    Key is not exportable.
    Key Data:
    0000440b  0000725a  000013a6  000078ca  00004533  000027a9  000037a6  00007647
    0000708c  00001971  00006914  000026ed  00000409  000011ec  00007d10  00002fee
    00006267  000031ee  000075f1  00001bd3  00007758  00005476  0000288a  7ab7
rt-01#
```
```bash
!Visualizando as conexões ativas do SSH Server.
!OBSERVAÇÃO: ESSA OPÇÃO SÓ VAI FUNCIONAR QUANDO VOCÊ SE CONECTAR REMOTAMENTE NO SWITCH OU ROUTER.
rt-01# show ssh
  %No SSHv2 server connections running.
  %No SSHv1 server connections running.
rt-01#
```
```bash
!Visualizando os Usuários Conectados no Switch
!OBSERVAÇÃO: ESSA OPÇÃO VAI MOSTRAR O USUÁRIO LOGADO NO CONSOLE: con 0 OU NO VTY: vty 0
rt-01# show users
    Line       User             Host(s)              Idle       Location
*  0 con 0     SEU_USUÁRIO      idle                 00:00:00 

  Interface    User             Mode         Idle     Peer Address
rt-01#
```