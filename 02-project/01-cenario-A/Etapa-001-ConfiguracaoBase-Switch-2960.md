#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 16/09/2024<br>
#Data de atualização: 22/05/2025<br>
#Versão: 0.12<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>
#Testado e homologado o Cisco Packet Tracer 8.2.x x64 e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Acessando o Modo EXEC de Comandos de Usuário no Cisco IOS<br>
#02_ SEGUNDA ETAPA: Acessando o Modo EXEC Privilegiado no Cisco IOS.<br>
#03_ TERCEIRA ETAPA: Configuração da Data e Hora no Cisco IOS.<br>
#04_ QUARTA ETAPA: Acessando o Modo de Configuração Global no Cisco IOS.<br>
#05_ QUINTA ETAPA: Configurações Básicas (Base Config) do Switch Catalyst Cisco 2960 Layer 2.<br>
#06_ SEXTA ETAPA: Configuração da Linha Console no Cisco IOS.<br>
#07_ SÉTIMA ETAPA: Salvando as Configurações Básica (Base) do Switch Cisco Catalyst 2960 Layer 2.<br>
#08_ OITAVA ETAPA: Visualizando as Configurações do Switch Cisco Catalyst 2960.<br>
#09_ NOVA ETAPA: Testando o acesso ao Switch Cisco Catalyst 2960.<br>
#10_ DÉCIMA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960 Layer 2.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração Base Switch 2960 do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Basic Switch](http://img.youtube.com/vi/qIqeQDUmKVg/0.jpg)](https://www.youtube.com/watch?v=qIqeQDUmKVg "Basic Switch")

Link da vídeo aula: https://www.youtube.com/watch?v=qIqeQDUmKVg

## PRIMEIRA ETAPA: Acessando o Modo EXEC de Comandos de Usuário no Cisco IOS.

Primeiro acesso ao modo EXEC de Comandos de Usuário *(> sinal de Maior - user EXEC commands mode)*, utilize o modo EXEC de Usuário para definir, visualizar e testar as operações do sistema do Cisco IOS. 

Em geral, os comandos EXEC de Usuário permitem que você se conecte a dispositivos remotos, altere as configurações da linha do terminal temporariamente, etc..., utilizado para executar os testes básicos e listar as informações do Cisco IOS (Internetwork Operating System).

O modo EXEC do Cisco IOS é dividido em dois níveis de acesso: **Usuário (> símbolo de Maior) e Privilegiado (# símbolo de Sustenido/Hashtag).**

**OBSERVAÇÃO-01:** sempre que você acessar o modo EXEC pela primeira vez no Switch ou Router será mostrado o nome (hostname) padrão dos equipamentos: **Switch = Switch> e Router = Router>**.
```bash
Switch>
```

## SEGUNDA ETAPA: Acessando o Modo EXEC Privilegiado no Cisco IOS.

01. Acessando o modo EXEC Privilegiado (# sinal de Sustenido/Hashtag - privileged EXEC mode).

**DICA-01:** utilizar sempre a tecla TAB para auto-completar os comandos no Cisco IOS;

**DICA-02:** se você estiver com dúvida do comando, utilizar o sinal de: ? (Interrogação) junto com o comando para mostrar as opções e informações reduzidas do comando (ajuda básica), ou para mostrar as opções ambíguas (Ambiguidade - mais de uma forma ou opção) muito comum nos comandos abreviados.

**EXEMPLO: Switch> show? | Switch> enable? | Switch# copy? | Switch# disable? | Switch# clock? | Switch(config)# service?**
```bash
!Verificando a ajuda básica dos comandos no Cisco IOS
Switch> show ?
Switch# copy ?
Switch# disable ?
Switch# clock ?
Switch(config)# service ?

!Verificando a ambiguidade de comandos no Cisco IOS
Switch# c?
clear  clock  configure  connect  copy 
```

**DICA-03** se você está estudando para a Certificação Cisco CCNAv7, é recomendado digitar os comandos completos, utilize comandos abreviados somente quando você já domina o Cisco IOS.

**EXEMPLO:** enable = en | show running-config = sh runn | interface FastEthernet0/0 = int fa0/0

Para sair do modo EXEC Privilegiado você pode digitar o comando: *disable* ou *exit*.
```bash
Switch> enable
Switch#

Switch# disable
Switch>

Switch> enable
Switch# exit
Switch>
```

## TERCEIRA ETAPA: Configuração da Data e Hora no Cisco IOS.

01. Configuração de Data/Hora em Inglês, você pode usar o Mês abreviado ou completo na configuração.

**EXEMPLO:** March ou Mar | April ou Apr | October ou Oct | November ou Nov | December ou Dec

**EXEMPLO:** Hora no formato Universal: Hora:Minutos:Segundos 00:00:00 - Data no formato: Dia Mês Completo ou Abreviado e Ano Completo: 01 March 2024

**DICA-04:** é recomendado utilizar o Protocolo NTP (Network Time Protocol) para manter sincronizado a Data e Hora no Switch ou Router.
```bash
Switch# clock set 14:00:00 10 October 2025
```

## QUARTA ETAPA: Acessando o Modo de Configuração Global no Cisco IOS.

01. Acessando o modo de Configuração Global de comandos do Cisco IOS.
	
**DICA-05:** nesse modo que é feita a maioria das configurações do Cisco IOS tanto no Switch como no Router.
```bash
Switch# configure terminal
Switch(config)#
```

## QUINTA ETAPA: Configurações Básicas (Base Config) do Switch Catalyst Cisco 2960 Layer 2.

01. Configuração do nome do Switch (configuração principal do equipamento).

**OBSERVAÇÃO-02:** essa configuração é obrigatória para o serviço de *Acesso Remoto SSH (Secure Shell)* e demais serviços de rede que utiliza nomes para o seu acesso.

**DICA-06:** utilizar nomes curtos e objetivos, não usar caracteres especiais, espaço, acentuação, nomes complexo, etc...
```bash
Switch(config)# hostname sw-01
sw-01(config)#
```

02. Habilitando o serviço de criptografia de senha do Tipo-7 Password do Cisco IOS.

**DICA-07:** senhas do Tipo-7 por padrão não são criptografadas no Cisco IOS (serviço está desabilitado por padrão no Cisco IOS sendo necessário habilitar para criptografar as senhas, caso você não habilite o serviço as senhas serão mostradas em Texto Plano no comando: *show running-config*).

**OBSERVAÇÃO-03:** senhas do Tipo-7 são fáceis de serem quebradas e não são mais usadas nos equipamentos da Cisco, nesse caso é recomendado utilizar senhas do Tipo-5 Secret.

**DESAFIO-01:** site para quebrar senhas do Tipo-7 https://packetlife.net/toolbox/type7/
```bash
sw-01(config)# service password-encryption
```

03. Habilitando o serviço de marcação de Data/Hora detalhado nos Logs do Cisco IOS.

**DICA-08:** esse recurso é utilizado nos sistemas de monitoramento, desempenho e consumo de rede, principalmente nos sistemas de auditoria de acesso ou recursos/serviços de rede e protocolos de geração de Logs nos equipamentos da Cisco.
```bash
sw-01(config)# service timestamps log datetime msec
```

**DICA-09:** esse recurso define que os logs do sistema sejam armazenados no buffer de memória RAM do equipamento, e especifica o tamanho desse buffer em 4096 bytes (4 KB).
```bash
sw-01(config)# logging buffered 4096
```

04. Desativando o serviço de resolução de nomes de domínio (serviço habilitado por padrão) no Cisco IOS.

**DICA-10:** se você desabilitar esse recurso o problema de travamento de comandos digitados fora do seu modo padrão no Cisco IOS é resolvido, mais você perde a resolução de nomes nos equipamentos, em Switch e Router esse recurso é pouco utilizado, somente quando é feito a integração com o Serviço de DNS (Domain Name Service).

**EXEMPLO:** switch# time (Translating "time"...domain server (255.255.255.255))

**DICA-11:** para desbloquear o terminal, você pressiona: *Ctrl + Shift + 6* ou espera a liberação do terminal que demora cerca de *60 segundos*.

**DICA-12:** o comando: *no* é usado para desabilitar ou remover configurações feitas no Switch ou Router da Cisco.
```bash
sw-01(config)# no ip domain-lookup
```

05. Configuração do banner da mensagem do dia no Cisco IOS.

**DICA-13:** existe vários tipos de Banners no Cisco IOS, o MOTD (Message-of-the-Day - Mensagem do Dia) é o mais utilizado.

**EXEMPLO:** banner motd (Mensagem do Dia), banner login (Mensagem de Login), banner exec (Mensagem de Modo EXEC), banner incoming (Mensagem de Entrada)

**DICA-14:** é recomendado não utilizar acentuação, textos longos ou complexos no Banner MOTD e demais Banners, pois o terminal do Cisco IOS não reconhece esses caracteres.

**DESAFIO-02:** pesquisar na Internet *Imagens ASCII Art Cisco* para colocar no Banner MOTD. Site indicado para essa configuração: http://ascii-art.de/ascii/

**OBSERVAÇÃO-04:** imagens ASCII Art no Banner *não pode ser muito grande*, recomendado ser **<= 1024 pixels**

**CUIDADO:** utilizar o mesmo *sinal de delimitador de Início e Fim* do Banner na imagem ASCII (# Sustenido/Hashtag) ou outro carácter que não apareça na imagem.
```bash
sw-01(config)# banner motd #AVISO: acesso autorizado somente a funcionarios#
```

06. Habilitando o uso de senha do Tipo-5 Secret para acessar o modo EXEC Privilegiado do Cisco IOS.

**DICA-15:** senhas do Tipo-5 por padrão utiliza criptografia forte (Algorítimo MD5) e não precisa do serviço de criptografia de senha habilitado para funcionar.

**OBSERVAÇÃO-05:** por padrão o acesso ao modo EXEC Privilegiado é liberado sem segurança, é recomendado sempre habilitar o recurso de segurança para acessar o Modo EXEC Privilegiado e o Modo de Configuração Global.
```bash
sw-01(config)# enable secret SUA_SENHA_SEGURA
```

07. Criação dos usuários locais utilizando senhas do Tipo-5 ou Tipo-7 e privilégios diferenciados.

**DICA-16:** existe 16 (dezesseis) níveis de Privilégios no Cisco IOS (0 mais baixo até 15 mais alto);

| Nível | Descrição | Permissões Principais |
| ----- | --------- | --------------------- |
| 0     | **Mínimo**  | Apenas comandos básicos: `logout`, `enable`, `disable`, `exit`, e `help`. |
| 1     | **Usuário padrão (User EXEC)** | Visualiza status básico, verifica conexões, executa `ping`, `traceroute`, e acessa comandos de diagnóstico simples. |
| 2-14  | **Intermediários (Personalizados)**  | São níveis configuráveis. Podem ser atribuídos comandos específicos para operações específicas sem liberar o modo privilegiado completo (`enable`). |
| 15    | **Administrador total (Privileged EXEC)** | Acesso total. Executa todos os comandos, incluindo configurações globais, interfaces, roteamento, segurança, manipulação de arquivos, reinicialização e atualização de firmware. |

**DICA-17:** não é recomendado criar usuários utilizando senhas do Tipo-7 (senhas fracas, fácil de quebrar);

**DICA-18:** existe a possibilidade de se autenticar no Switch utilizando os protocolos *RADIUS (Remote Authentication Dial-In User Service) ou TACACS (Terminal Access Controller Access-Control System)*;

**DICA-19:** usuários com Privilégio 15 não precisa digitar o comando: **enable** após se logar no Switch ou Router.

**OBSERVAÇÃO-06:** criação de usuários comuns para administrar o Switch, privilégio padrão recomendado: 1.
```bash
sw-01(config)# username SEU_USUÁRIO_1 secret SUA_SENHA_SEGURA
sw-01(config)# username SEU_USUÁRIO_2 password SUA_SENHA_NÃO_SEGURA
sw-01(config)# username SEU_USUÁRIO_3 privilege 15 secret SUA_SENHA_SEGURA
```

08. Desativando os Serviços de Descobertas de equipamentos Cisco na Rede.

**DICA-20:** Os comandos: *no cdp run* e: *no lldp run* desativam os protocolos CDP (Cisco Discovery Protocol) e LLDP (Link Layer Discovery Protocol), respectivamente. Ambos são protocolos de descoberta de vizinhança usados para obter informações sobre dispositivos conectados diretamente ao switch ou roteador.

**OBSERVAÇÃO-07:** O CDP é o protocolo proprietário da Cisco que permite que roteadores e switches compartilhem informações sobre si mesmos, por padrão, está ativado em todos os equipamentos da Cisco. Ele coleta informações como: modelo do dispositivo, IP, VLANs, interfaces ativas, versão do IOS, etc..

**OBSERVAÇÃO-08:** O LLDP é o protocolo padrão aberto (IEEE 802.1AB), utilizado por equipamentos de diferentes fabricantes (Cisco, HP, Juniper, Dell, etc.). Semelhante ao CDP, permite que os dispositivos descubram vizinhos e compartilhem informações.
```bash
sw-01(config)# no cdp run
sw-01(config)# no lldp run
```

## SEXTA ETAPA: Configuração da Linha Console no Cisco IOS.

01. Acessando a Linha (line) Console (Command Line Interface), porta padrão de acesso *Out-of-Band (Fora da Banda)* do Switch Cisco.

**DICA-21:** conexão feita utilizando o *Cabo Console RS232/DB9 ou USB* e software de Acesso Remoto ao Console (PuTTY, Minicom, etc...).

**DICA-22:** nos Switch Cisco Catalyst temos apenas uma porta console RS232/DB9 ou USB (novos modelos).
```bash
sw-01(config)# line console 0
```

a) Forçando fazer login local utilizando os usuários e senhas locais criados no Switch.

**DICA-23:** por padrão a configuração da Linha Console é permitir o acesso físico sem autenticação.
```bash
sw-01(config-line)# login local
```

b) Habilitando a senha de acesso do Tipo-7 Password (senha fraca).

**DICA-24:** na porta console não temos a opção de criar senhas do Tipo-5 (forte) somente Tipo-7 (fraca)

**OBSERVAÇÃO-09:** a porta console é considerada uma porta/interface física não remota ou virtual, por esse motivo ela não tem suporte a senhas do Tipo-5 Secret, pois o acesso é feito fisicamente no Switch ou Router (se você tem a possibilidade de acessar fisicamente um equipamento, o nível de segurança da criptografia não importa mais, pois é uma invasão física e não lógica).

**OBSERVAÇÃO-10:** essa configuração só será utilizada caso não exista usuários locais criados e se a opção do comando: *login local* não for configurada, nesse caso se utiliza somente a opção do comando: *login*.
```bash
sw-01(config-line)# password SUA_SENHA_NÃO_SEGURA
```

c) Habilitando o sincronismo das mensagens de Logs na tela da linha de console do Cisco IOS.

**DICA-25:** esse recurso ajuda bastante no dia-a-dia em administrar o Cisco IOS, por padrão todas as mensagens de Log tem sua saída padrão na tela, muitas vezes isso atrapalha na digitação, esse recurso permite o sincronismos entre as mensagens e a digitação dos comandos.

**OBSERVAÇÃO-11:** por padrão todas as mensagens de status ou logs do Switch são mostradas na tela.
```bash
sw-01(config-line)# logging synchronous
```

d) Habilitando o tempo de inatividade de uso da linha console do Cisco IOS.

**DICA-26:** configuração do tempo de inatividade em minutos e segundos da linha console, utilizado principalmente quando você está conectado no console e não está interagindo nas configurações, após o tempo de inatividade a seção será finalizada (logoff/logout), garantindo assim a segurança do acesso aos equipamentos.

**OBSERVAÇÃO-12:** não é recomendado deixar o tempo de inatividade muito curto e nem muito longo.
```bash
sw-01(config-line)# exec-timeout 5 30
```

e) Saindo de todos os níveis e voltando para o modo EXEC Privilegiado.

**DICA-27:** você pode utilizar a tecla de atalho: *Ctrl + Z* para sair de todos os níveis;

**DICA-28:** o comando: *exit* sai nível por nível, o comando: *end* sai de todos os níveis.

**OBSERVAÇÃO-13:** os dois comandos são utilizados principalmente em scripts de automação.
```bash
sw-01(config-line)# end
```

## SÉTIMA ETAPA: Salvando as Configurações Básicas (Base) do Switch Cisco Catalyst 2960 Layer 2.

01. Salvando as configurações da memória RAM (Running-Config) para a memória NVRAM (Startup-Config).

**DICA-29:** no Cisco IOS temos vários tipos de memórias: RAM (Random Access Memory), NVRAM (Non-Volatile Random Access Memory), Flash EEPROM (Electrically-Erasable Programmable Read-Only Memory), etc.

**DICA-30:** você pode utilizar o comando: *write*, indicado para criação de scripts e considerado obsoleto pela Cisco para salvar as configurações da RAM (running-config) para a NVRAM (startup-config).
```bash
sw-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
sw-01#
```

## OITAVA ETAPA: Visualizando as Configurações do Switch Cisco Catalyst 2960.

01. Visualizando as configurações da memória RAM (Running-Config).

**DICA-31:** no Cisco IOS temos várias opções de visualizações das configurações utilizando o comando: *show*, o principal comando utilizado em todos os equipamentos da Cisco para verificar as configurações que estão rodando no momento é o: *show running-config* (configuração que está rodando na RAM).
```bash
sw-01# show running-config
Building configuration...

Current configuration : 1763 bytes
!
...
!
end
sw-01#
```

**DICA-32:** no Cisco IOS permite filtrar a saída dos comandos show usando pipes (|) com opções como: include (incluir/mostrar), exclude (excluir/ocultar), begin (início/primeira linha) e section (sessão). Esses filtros ajudam a encontrar rapidamente partes específicas da configuração, sem precisar rolar todo o arquivo.
```bash
!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Console 0
sw-01# show running-config | section include con 0
line con 0
 password 7 08701E1D290A00191308
 logging synchronous
 login local
 exec-timeout 5 30
sw-01#
```

02. Visualizando a Data e Hora do Switch
```bash
sw-01# show clock
*0:9:24.347 UTC Mon Mar 1 1993
```

03. Visualizando os Logs do Switch
```bash
sw-01# show logging
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

04. Saindo do Modo Privilegiado do Switch
```bash
sw-01# disable
sw-01>
```

05. Saindo da conexão do Console do Switch
```bash
sw-01> exit
```

## NOVA ETAPA: Testando o acesso ao Switch Cisco Catalyst 2960.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: SEU_USUÁRIO
Password: SUA_SENHA

sw-01> enable
Password: SUA_SENHA_SEGURA

sw-01# configure terminal
sw-01(config)#
```

## DÉCIMA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960 Layer 2.

01. Utilizando o Visual Studio Code (VSCode) para automatizar as configurações do Cisco IOS.

**OBSERVAÇÃO-14:** recomendo sempre utilizar um *Editor de Texto Profissional* para criar os scripts e automatizar as tarefas de configuração do Cisco IOS, hoje em dia é indicado utilizar o Visual Studio Code (VSCode) junto com as Extensões: *Cisco IOS Syntax e Cisco Config Highlight* para facilitar essa configuração.

**DICA-33:** o caractere: *! (exclamação)* é utilizado como um recurso de *Comentário*, sua utilização server para comentar o código de automação do Cisco IOS ou para desativar um comando para não ser executado, *RECOMENDO FORTEMENTE DOCUMENTAR TODOS OS COMANDOS E PROCEDIMENTOS DE CONFIGURAÇÃO PARA FACILITAR O ENTENDIMENTO.*

**DICA-34:** para facilitar a leitura do código, recomendo utilizar o recurso de **Indentação de Código** usando a Tecla TAB (Tabulador/Tabulação) para cada nível que você está configurando o Cisco IOS, isso facilitada a análise de erros (Debug) do código.

```python
!Automação da configuração do Switch 2
enable

!Configuração de Data/Hora em inglês, você pode usar abreviado ou completo
clock set 14:00:00 21 November 2025

  !Acessando o modo de configuração global de comandos
  configure terminal

    !Configuração do nome do switch
    hostname sw-02

    !Habilitando o serviço de criptografia de senhas do Tipo-7 Password 
    service password-encryption

    !Habilitando o serviço de marcação de Data/Hora detalhado nos Logs
    service timestamps log datetime msec

    !Habilitando o tamanho do Buffer dos Logs na Memória RAM
    logging buffered 4096 

    !Desativando a resolução de nomes de domínio
    no ip domain-lookup

    !Configuração do banner da mensagem do dia
    banner motd #AVISO: acesso autorizado somente a funcionarios#

    !Habilitando o uso senha do Tipo-5 Secret para acessar o modo EXEC Privilegiado
    enable secret SUA_SENHA_SEGURA

    !Criação dos usuários locais utilizando senhas do Tipo-5 ou Tipo-7 e privilégios diferenciados
    username SEU_USUÁRIO_1 secret SUA_SENHA_SEGURA
    username SEU_USUÁRIO_2 password SUA_SENHA_NÃO_SEGURA
    username SEU_USUÁRIO_3 privilege 15 secret SUA_SENHA_SEGURA

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

      !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
      end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```