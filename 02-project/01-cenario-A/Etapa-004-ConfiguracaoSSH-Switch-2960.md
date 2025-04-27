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
Versão: 0.05<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960<br>
#02_ SEGUNDA ETAPA: Configuração do Serviço de Acesso Remoto SSH (Secure Shell) no Cisco IOS<br>
#03_ TERCEIRA ETAPA: Testando e Acessando Remotamente do Switch Cisco Catalyst 2960.<br>
#04_ QUARTA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração SSH Switch 2960 do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Config SSH 2960](http://img.youtube.com/vi/bS1o83wWMUk/0.jpg)](https://www.youtube.com/watch?v=bS1o83wWMUk "Config SSH 2960")

Link da vídeo aula: https://www.youtube.com/watch?v=bS1o83wWMUk

## PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.

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

## SEGUNDA ETAPA: Configuração do Serviço de Acesso Remoto SSH (Secure Shell) no Cisco IOS

01. Configuração do Nome de Domínio FQDN (Fully Qualified Domain Name).

**DICA-01:** o nome de Domínio FQDN (Fully Qualified Domain Name) é utilizado pelo Serviço do SSH (Secure Shell) e outros serviços de rede como o Servidor de Autenticação Remota e Monitoramento de Switch ou Router utilizando os protocolos RADIUS (Remote Authentication Dial In User Service), TACACS (Terminal Access Controller Access-Control System) ou DNS (Domain Name Service).

**ADENDO-01** um nome de domínio, muitas vezes chamado apenas de domínio, é um nome fácil de lembrar, associado sempre a um endereço IPv4 ou IPv6 físico na Internet ou na Rede Local separado sempre por um: *. (ponto)*.
```bash
sw-01(config)# ip domain-name SEU_DOMÍNIO.INTRA
```

02. Criação/Geração da chave de criptografia do Serviço do SSH (Secure Socket Shell) Server local.

**DICA-02:** por padrão o serviço do SSH Server está desabilitado no Switch ou Router;

**DICA-03:** por padrão todas as conexões remotas utilizando o protocolo SSH são criptografadas (segura);

**OBSERVAÇÃO-01:** é recomendado utilizar módulos de criptografia de no mínimo: *1024 bits* (opções de 360 até 2048);

**OBSERVAÇÃO-02:** no Switch ou Router *Real* utilizamos o comando: *crypto key generate rsa general-keys modulus 1024* para fazer a geração da chave e inicialização do Serviço;

**OBSERVAÇÃO-03:** existe vários algorítimos de geração das chaves públicas criptografadas no SSH, o padrão é utilizar o RSA (Rivest-Shamir-Adleman);

**OBSERVAÇÃO-04:** a porta padrão de conexão do Serviço de SSH é a: *22* utilizando o Protocolo: *TCP*;

**ADENDO-01:** versões do Cisco Packet Tracer >=7.3 possui o suporte para o comando completo de geração das chaves SSH RSA nos Switches ou Router em um único comando igual aos equipamentos reais, utilizando o comando: *crypto key generate rsa general-keys modulus 1024*;

**OBSERVAÇÃO IMPORTANTE:** caso queira desativar o serviço do SSH ou remover os Módulos/Chaves Públicas RSA, digite o comando: *crypto key zeroize rsa*, caso você digite novamente o comando: *crypto key generate rsa* ele vai solicitar se você quer substituir os Módulos/Chaves Públicas RSA atuais (Do you really want to replace them? [yes/no]).
```bash
sw-01(config)# crypto key generate rsa general-keys modulus 1024
```

03. Habilitando a versão 2 do Serviço de SSH Server.

**DICA-04:** a versão: *2* do serviço do SSH Server corrigiu várias falhas de segurança existe na versão: *1.99*, recomendo sempre habilitar essa versão.

**OBSERVAÇÃO-05:** após a criação da chave RSA do SSH o serviço habilita por padrão a versão 1.99.
```bash
sw-01(config)# ip ssh version 2
```

04. Habilitando o tempo de inatividade para novas conexões do SSH Server.

**DICA-05:** configuração de inatividade é feita somente em segundos (1 até 120 segundos = 2 minutos).

**OBSERVAÇÃO-06:** essa configuração está relacionada ao tempo para se autenticar no serviço do SSH no Switch ou Router, diferente do tempo de inatividades de acesso remoto que é controlado pelas Lines VTY ou Console.
```bash
sw-01(config)# ip ssh time-out 60
```

05. Habilitando o número máximo de tentativas de conexões simultâneas no SSH Server.

**DICA-06:** essa opção aumenta o nível de segurança contra ataques de Força Bruta (Brute-Force) utilizando dicionários de usuários e senhas e várias autenticações simultâneas com falhas (Exemplo do software Hydra).

**OBSERVAÇÃO-07:** limites de conexões simultâneas vai de: 0 até 5, por padrão várias conexão simultâneas são permitidas.
```bash
sw-01(config)# ip ssh authentication-retries 2
```

06. Saindo de todos os níveis e voltando para o modo EXEC Privilegiado.

**DICA-07:** você pode usar o comando: *do write* ou o comando: *copy running-config startup-config* para salvar as configurações sem sair do Modo Exec Privilegiado.
```bash
sw-01(config)# end
sw-01#
```

07. Salvando as configurações da memória RAM (Running-Config) para a memória NVRAM (Startup-Config).

**DICA-08:** nunca esqueça de salvar as configurações.
```bash
sw-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
sw-01#
```

08. Visualizando as configurações da memória RAM (Running-Config).

**DICA-09** após a configuração do Serviço do SSH verifique se tudo está configurado de forma correta utilizando os comandos: *show*.
```bash
!Visualizando as Configurações do Running-Config (RAM)
!OBSERVAÇÃO: A ÚNICA LINHA QUE NÃO APARECE NAS CONFIGURAÇÕES DO SSH É A: crypto key generate rsa
sw-01# show running-config
  Building configuration...

  Current configuration : 1763 bytes
  !
  ...
  !
  end
sw-01#
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Line VTY
sw-01# show running-config | section include line vty
  line vty 0 4
    exec-timeout 5 30
    password 7 08701E1D290A00191308
    logging synchronous
    login local
    transport input ssh
  line vty 5 15
    login
sw-01#
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente do SSH
!OBSERVAÇÃO: ÚNICA LINHA QUE NÃO APARECE NAS CONFIGURAÇÃO É A: crypto key generate rsa
sw-01# show running-config | include ip ssh
  ip ssh version 2
  ip ssh authentication-retries 2
  ip ssh time-out 60
sw-01#
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente da Interface Vlan1
sw-01# show running-config | section include interface Vlan1
  interface Vlan1
    description Interface de SVI
    ip address 192.168.1.250 255.255.255.0
sw-01#
```
```bash
!Visualizando as configurações do SSH Server e Versão
sw-01# show ip ssh
  SSH Enabled - version 2.0
  Authentication timeout: 60 secs; Authentication retries: 2
sw-01#
```
```bash
!Visualizando das chaves públicas RSA do SSH Server
sw-01# show crypto key mypubkey rsa
  % Key pair was generated at: 21:44:0 UTC fevereiro 4 2025
  Key name: sw-01.SEU_DOMÍNIO.INTRA
    Storage Device: not specified
    Usage: General Purpose Key
    Key is not exportable.
    Key Data:
    00005d5c  00007c53  0000627e  00007a79  00005802  00000027  000071e7  000018cb
    00003fa6  000008b2  00000428  00001fac  00002e5d  00007dbf  00007fa8  00004273
    00001673  0000237d  000006af  00000dd9  0000370c  00004c8d  00003128  4aad
  % Key pair was generated at: 21:44:0 UTC fevereiro 4 2025
  Key name: sw-01.SEU_DOMÍNIO.INTRA.server
  Temporary key
    Usage: Encryption Key
    Key is not exportable.
    Key Data:
    0000440b  0000725a  000013a6  000078ca  00004533  000027a9  000037a6  00007647
    0000708c  00001971  00006914  000026ed  00000409  000011ec  00007d10  00002fee
    00006267  000031ee  000075f1  00001bd3  00007758  00005476  0000288a  7ab7
sw-01#
```
```bash
!Visualizando as conexões ativas do SSH Server.
!OBSERVAÇÃO: ESSA OPÇÃO SÓ VAI FUNCIONAR QUANDO VOCÊ SE CONECTAR REMOTAMENTE NO SWITCH OU ROUTER.
sw-01# show ssh
  %No SSHv2 server connections running.
  %No SSHv1 server connections running.
sw-01#
```
```bash
!Visualizando os Usuários Conectados no Switch
!OBSERVAÇÃO: ESSA OPÇÃO VAI MOSTRAR O USUÁRIO LOGADO NO CONSOLE: con 0 OU NO VTY: vty 0
sw-01# show users
    Line       User             Host(s)              Idle       Location
*  0 con 0     SEU_USUÁRIO      idle                 00:00:00 

  Interface    User             Mode         Idle     Peer Address
sw-01#
```

## TERCEIRA ETAPA: Testando e Acessando Remotamente do Switch Cisco Catalyst 2960.

01. Testando as Conexão do Desktop no Switch e Acessando Remoto via SSH.

a) Abrindo o Prompt de Comando do Desktop;

**DICA-10** não confunda Terminal com Command Prompt, Terminal é utilizado para se conectar no Switch ou Router utilizando o Cabo Console, já o Command Prompt (Prompt de Comando) é utilizado para testar as configurações de rede e acessar remotamente o Switch ou Router.
```bash
!Verificando o endereço IPv4 configurado no Desktop
C:\> ipconfig
FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: 
   Link-local IPv6 Address.........: FE80::2E0:8FFF:FE82:E0BB
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.1.10
   Subnet Mask.....................: 255.255.255.0
   Default Gateway.................: ::
                                     192.168.1.254

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
C:\>
```
```bash
!Verificando o endereço detalhado IPv4 configurado no Desktop
C:\> ipconfig /all
FastEthernet0 Connection:(default port)

   Connection-specific DNS Suffix..: 
   Physical Address................: 00E0.8F82.E0BB
   Link-local IPv6 Address.........: FE80::2E0:8FFF:FE82:E0BB
   IPv6 Address....................: ::
   IPv4 Address....................: 192.168.1.10
   Subnet Mask.....................: 255.255.255.0
   Default Gateway.................: ::
                                     192.168.1.254
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-00-55-9C-4C-00-E0-8F-82-E0-BB
   DNS Servers.....................: ::
                                     192.168.1.1

Bluetooth Connection:

   Connection-specific DNS Suffix..: 
   Physical Address................: 00E0.F7AA.695E
   Link-local IPv6 Address.........: ::
   IPv6 Address....................: ::
   IPv4 Address....................: 0.0.0.0
   Subnet Mask.....................: 0.0.0.0
   Default Gateway.................: ::
                                     0.0.0.0
   DHCP Servers....................: 0.0.0.0
   DHCPv6 IAID.....................: 
   DHCPv6 Client DUID..............: 00-01-00-01-00-55-9C-4C-00-E0-8F-82-E0-BB
   DNS Servers.....................: ::
                                     192.168.1.1
C:\>
```
```bash
!Testando a comunicação com o Switch utilizando o pacote ICMP (Internet Control Message Protocol)
C:\> ping 192.168.1.250           (Switch SW-01)
Pinging 192.168.1.250 with 32 bytes of data:

Reply from 192.168.1.250: bytes=32 time<1ms TTL=255
Reply from 192.168.1.250: bytes=32 time<1ms TTL=255
Reply from 192.168.1.250: bytes=32 time<1ms TTL=255
Reply from 192.168.1.250: bytes=32 time<1ms TTL=255

Ping statistics for 192.168.1.250:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0m
C:\>
```
```bash
C:\> ping 192.168.1.251           (Switch SW-02)
Pinging 192.168.1.251 with 32 bytes of data:

Reply from 192.168.1.251: bytes=32 time=12ms TTL=255
Reply from 192.168.1.251: bytes=32 time<1ms TTL=255
Reply from 192.168.1.251: bytes=32 time=9ms TTL=255
Reply from 192.168.1.251: bytes=32 time<1ms TTL=255

Ping statistics for 192.168.1.251:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 12ms, Average = 5ms
C:\>
```
```bash
!Testando o acesso remoto no Switch utilizando o protocolo Telnet (Teletype Network)
C:\> telnet 192.168.1.250         (Switch SW-01)
Trying 192.168.1.250 ...Open

[Connection to 192.168.1.250 closed by foreign host]
C:\>

C:\> telnet 192.168.1.251         (Switch SW-02)
Trying 192.168.1.250 ...Open

[Connection to 192.168.1.250 closed by foreign host]
C:\>
```
```bash
!Acessando remotamente os Switches utilizando o protocolo SSH (Secure Shell)
!OBSERVAÇÃO: -l (éli não é o número "1" (um) e sim "l" (éli) em minúsculo)
C:\> ssh -l admin 192.168.1.250   (Switch SW-01)
Password: 

AVISO: acesso autorizado somente a funcionarios

sw-01>

C:\> ssh -l admin 192.168.1.251   (Switch SW-02)
Trying 192.168.1.254 ...Open

[Connection to 192.168.1.254 closed by foreign host]
C:\>
```

## QUARTA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960.

01. Utilizando o Visual Studio Code (VSCode) para automatizar as configurações do Cisco IOS.

**OBSERVAÇÃO-08:** recomendo sempre utilizar um *Editor de Texto Profissional* para criar os scripts e automatizar as tarefas de configuração do Cisco IOS, hoje em dia é indicado utilizar o Visual Studio Code (VSCode) junto com as Extensões: *Cisco IOS Syntax e Cisco Config Highlight* para facilitar essa configuração.

**DICA-11:** o caractere: *! (exclamação)* é utilizado como um recurso de *Comentário*, sua utilização server para comentar o código de automação do Cisco IOS ou para desativar um comando para não ser executado, *RECOMENDO FORTEMENTE DOCUMENTAR TODOS OS COMANDOS E PROCEDIMENTOS DE CONFIGURAÇÃO PARA FACILITAR O ENTENDIMENTO.*

**DICA-12:** para facilitar a leitura do código, recomendo utilizar o recurso de **Indentação de Código** usando a Tecla TAB (Tabulador/Tabulação) para cada nível que você está configurando o Cisco IOS, isso facilitada a análise de erros (Debug) do código.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: SEU_USUÁRIO
Password: SUA_SENHA

sw-02> enable
Password: SUA_SENHA_SEGURA

sw-02#
```

```python
!Acessando o modo de Configuração Global de comandos
configure terminal

  !Configuração do nome de domínio FQDN (Nome de Domínio Totalmente Qualificado)
  ip domain-name SEU-DOMÍNIO.INTRA

  !Criação da chave de criptografia e habilitar o serviço de SSH Server local
  crypto key generate rsa general-keys modulus 1024

  !Habilitando a versão 2 do serviço de SSH Server
  ip ssh version 2

  !Habilitando o tempo de inatividade para novas conexões do SSH Server
  ip ssh time-out 60

  !Habilitando o número máximo de tentativas de conexões simultâneas no SSH Server
  ip ssh authentication-retries 2

  !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
  end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```