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
Versão: 0.04<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Router Cisco 1941.<br>
#02_ SEGUNDA ETAPA: Configuração da Interface LAN do Router no Cisco IOS.<br>
#03_ TERCEIRA ETAPA: Testando e Acessando Remotamente do Router Cisco 1941.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração Interface LAN Router 1941 do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Config IPv4 LAN](http://img.youtube.com/vi/0l1erzh1-8Q/0.jpg)](https://www.youtube.com/watch?v=0l1erzh1-8Q "Config IPv4 LAN")

Link da vídeo aula: https://www.youtube.com/watch?v=0l1erzh1-8Q

## PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Router Cisco 1941.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: SEU_USUÁRIO
Password: SUA_SENHA

rt-01> enable
Password: SUA_SENHA_SEGURA

rt-01# configure terminal
rt-01(config)#
```

## SEGUNDA ETAPA: Configuração da Interface LAN do Router no Cisco IOS.

01. Acessando a Interface GigabitEthernet 0/0 da LAN.

**DICA-01:** é recomendado utilizar a Interface GigabitEthernet 0/0 ou outra Interface para as Configurações da Rede Local LAN (Local Area Network).
```bash
rt-01(config)# interface gigabitEthernet 0/0
```

A) Configuração da Descrição da Interface GigabitEthernet 0/0 da LAN.

**DICA-02:** sempre utilizar o comando: *description* nas Interfaces para efeito de documentação.

**OBSERVAÇÃO-01:** documentação de Interface facilita o processo de identificação e função dela na topologia de rede, configuração obrigatória em Switch ou Router.
```bash
rt-01(config-if)# description Interface de Gateway da Rede LAN
```

B) Configuração do Endereçamento IPv4 da Interface GigabitEthernet 0/0 da LAN.

**OBSERVAÇÃO-02:** configuração do endereço IPv4 deve ser: *IPv4 + Máscara de Rede Completa (ClassFull)*, não utilizar CIDR (Classes Inter-Domain Routing) nas configurações.

**OBSERVAÇÃO-03:** essa Interface será o endereço de Gateway da Topologia da Rede LAN.
```bash
rt-01(config-if)# ip address 192.168.1.254 255.255.255.0
```

C) Inicializando a Interface GigabitEthernet 0/0 da LAN.

**DICA-03:** por padrão todas as Interfaces dos Roteadores estão no status: *desligada (Shutdown)*.

**OBSERVAÇÃO-04:** por padrão todas as Interfaces dos Roteadores estão com o status: *Administratively Down (Desligada Administrativamente)*.
```bash
rt-01(config-if)# no shutdown
```

D) Saindo de todos os níveis e voltando para o modo EXEC Privilegiado.

**DICA-04:** somente no modo EXEC Privilegiado você tem o comando: *copy* para salvar as configurações.
```bash
rt-01(config-if)# end
rt-01#
```

E) Salvando as configurações da memória RAM (Running-Config) para a memória NVRAM (Startup-Config)

**DICA-05:** nunca esqueça de salvar as configurações.
```bash
rt-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
rt-01#
```
02. Visualizando as configurações da memória RAM (Running-Config).

**DICA-06** após a configuração da Interface GigabitEthernet 0/0 da LAN, verifique se tudo está configurado de forma correta utilizando os comandos: *show*.
```bash
!Visualizando as Configurações do Running-Config (RAM)
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
!Fazendo um Filtro na Visualização do Running-Config somente da Interface GigabitEthernet 0/0
rt-01# show running-config | section include interface GigabitEthernet0/0
  interface GigabitEthernet0/0
    description Interface de Gateway da Rede LAN
    ip address 192.168.1.254 255.255.255.0
    duplex auto
    speed auto
rt-01#
```
```bash
!Visualizando informações detalhadas da Interface GigabitEthernet 0/0
rt-01# show interface gigabitEthernet 0/0
GigabitEthernet0/0 is up, line protocol is up (connected)
  Hardware is CN Gigabit Ethernet, address is 0060.7030.2701 (bia 0060.7030.2701)
  Description: Interface de Gateway da Rede LAN
  Internet address is 192.168.1.254/24
  MTU 1500 bytes, BW 1000000 Kbit, DLY 10 usec,
     reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA, loopback not set
  Keepalive set (10 sec)
  Full-duplex, 100Mb/s, media type is RJ45
  output flow-control is unsupported, input flow-control is unsupported
  ARP type: ARPA, ARP Timeout 04:00:00, 
  Last input 00:00:08, output 00:00:05, output hang never
  Last clearing of "show interface" counters never
  Input queue: 0/75/0 (size/max/drops); Total output drops: 0
  Queueing strategy: fifo
  Output queue :0/40 (size/max)
  5 minute input rate 0 bits/sec, 0 packets/sec
  5 minute output rate 0 bits/sec, 0 packets/sec
     0 packets input, 0 bytes, 0 no buffer
     Received 0 broadcasts, 0 runts, 0 giants, 0 throttles
     0 input errors, 0 CRC, 0 frame, 0 overrun, 0 ignored, 0 abort
     0 watchdog, 1017 multicast, 0 pause input
     0 input packets with dribble condition detected
     0 packets output, 0 bytes, 0 underruns
     0 output errors, 0 collisions, 1 interface resets
     0 unknown protocol drops
     0 babbles, 0 late collision, 0 deferred
     0 lost carrier, 0 no carrier
     0 output buffer failures, 0 output buffers swapped out
rt-01#
```
```bash
!Visualizando as configurações das Interfaces do Router
rt-01# show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol 
GigabitEthernet0/0     192.168.1.254   YES NVRAM  up                    up 
GigabitEthernet0/1     unassigned      YES NVRAM  administratively down down 
Vlan1                  unassigned      YES unset  administratively down down
rt-01#
```
```bash
!Visualizando informações de roteamento
rt-01# show ip route
Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
       D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
       N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
       E1 - OSPF external type 1, E2 - OSPF external type 2, E - EGP
       i - IS-IS, L1 - IS-IS level-1, L2 - IS-IS level-2, ia - IS-IS inter area
       * - candidate default, U - per-user static route, o - ODR
       P - periodic downloaded static route

Gateway of last resort is not set

     192.168.1.0/24 is variably subnetted, 2 subnets, 2 masks
C       192.168.1.0/24 is directly connected, GigabitEthernet0/0
L       192.168.1.254/32 is directly connected, GigabitEthernet0/0

rt-01#
```

## TERCEIRA ETAPA: Testando e Acessando Remotamente do Router Cisco 1941.

01. Testando as Conexão do Router no Desktop e Acessando Remoto via SSH.

a) Abrindo o Prompt de Comando do Desktop;

**DICA-07** não confunda Terminal com Command Prompt, Terminal é utilizado para se conectar no Switch ou Router utilizando o Cabo Console, já o Command Prompt (Prompt de Comando) é utilizado para testar as configurações de rede e acessar remotamente o Switch ou Router.
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
!Testando a comunicação com o Router utilizando o pacote ICMP (Internet Control Message Protocol)
C:\> ping 192.168.1.254           (Router RT-01)
Pinging 192.168.1.254 with 32 bytes of data:

Reply from 192.168.1.254: bytes=32 time<1ms TTL=255
Reply from 192.168.1.254: bytes=32 time<1ms TTL=255
Reply from 192.168.1.254: bytes=32 time<1ms TTL=255
Reply from 192.168.1.254: bytes=32 time<1ms TTL=255

Ping statistics for 192.168.1.254:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms

C:\>
```
```bash
!Testando o acesso remoto no Router utilizando o protocolo Telnet (Teletype Network)
C:\> telnet 192.168.1.254         (Router RT-01)
Trying 192.168.1.254 ...Open

[Connection to 192.168.1.254 closed by foreign host]
C:\>
```
```bash
!Acessando remotamente o Router utilizando o protocolo SSH (Secure Shell)
!OBSERVAÇÃO: -l (éli não é o número "1" (um) e sim "l" (éli) em minúsculo)
C:\> ssh -l admin 192.168.1.254   (Router RT-01)

Password: 

AVISO: acesso autorizado somente a funcionarios

rt-01#
```