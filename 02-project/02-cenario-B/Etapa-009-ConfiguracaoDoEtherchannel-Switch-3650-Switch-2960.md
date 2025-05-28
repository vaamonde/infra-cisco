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
Data de atualização: 28/05/2025<br>
Versão: 0.07<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ Configurando o Etherchannel no Switch Multilayer 3650 no Cisco Packet Tracer;<br>
#02_ Configurando o Etherchannel no Switch Layer 2 2960 Lado Esquerdo no Cisco Packet Tracer;<br>
#03_ Configurando o Etherchannel no Switch Layer 2 2960 Lado Direito no Cisco Packet Tracer;<br>
#04_ Verificando as Configurações dos Etherchannel dos Switches no Cisco Packet Tracer.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do Etherchannel do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

O **STP Portfast (Porta Rápida)** faz com que uma *Porta do Switch* altere imediatamente para o estado de **Encaminhamento (Forwarding)**, ignorando os estados de **Ouvindo (Listening)** e **Aprendendo (Learning)**, esse recurso é configurado somente em Portas de Acesso (Access).

O **STP Portfast Trunk (Porta Rápida de Tronco)** tem a mesma finalidade do *STP Portfast*, mais é somente configurado em *Portas de Tronco (Trunk)* com dispositivos que **NÃO SÃO Switches**, como por exemplo: *Router (Roteadores), Server (Servidores), Bridge (Pontes), Access Point (Ponto de Acesso), Etherchannel e etc.*

O **EtherChannel** é uma tecnologia de agregação de link que agrupa vários links Ethernet físicos em um único link lógico. É usado para fornecer tolerância a falhas, compartilhamento de carga, maior largura de banda e redundância entre switches, roteadores e servidores. A tecnologia EtherChannel torna possível combinar o número de links físicos entre os switches para aumentar a velocidade geral da comunicação switch a switch.

O **EtherChannel PAgP (Port Aggregation Protocol - Protocolo de Agregação de Portas)** é um protocolo proprietário da Cisco que combina links Ethernet físicos em um único link lógico. Isso permite balanceamento de carga, tolerância a falhas e links de alta velocidade entre switches, roteadores e servidores

O **EtherChannel LACP (Link Aggregation Control Protocol)** é um protocolo que permitem agrupar vários links físicos em um único canal lógico. Isso aumenta a largura de banda e a redundância, e reduz as falhas na comunicação de dados.

O **EtherChannel Estático (Manual)** é uma configuração que combina vários links físicos em um canal lógico, sem negociação (Modo "on", sem o uso do LACP ou PAgP). Ele permite o compartilhamento de carga de tráfego e redundância em caso de falha de um ou mais links. 

**Resumo Geral entre os Protocolos Etherchannel**

|Tipo      |Protocolo     |Modos                |Disponíveis   |Compatibilidade	Características  |
|----------|--------------|---------------------|--------------|---------------------------------|
|Estático  |Nenhum        |"on"                 |Universal     |Simples, sem detecção de falha   |
|PAgP      |Cisco	        |"auto","desirable"   |Apenas Cisco  |Automático, proprietário         |
|LACP      |IEEE 802.3ad  |"passive", "active"  |Multivendor   |Mais flexível e seguro           |

**Comparação Geral entre os Protocolos Etherchannel**

|Característica         |EtherChannel Estático  |PAgP (Cisco)     |LACP (IEEE 802.3ad)|
|-----------------------|-----------------------|-----------------|-------------------|
|Protocolo              |Nenhum                 |Cisco            |IEEE 802.3ad       |
|Compatibilidade        |Universal              |Apenas Cisco     |Multivendor        |
|Detecção de falhas     |❌ Não detecta         |✅ Sim           |✅ Sim             |
|Balanceamento de carga |✅ Sim                 |✅ Sim           |✅ Sim             |
|Negociação automática  |❌ Não                 |✅ Sim           |✅ Sim             |
|Melhor uso             |Links fixos e estáveis |Redes 100% Cisco |Ambientes mistos   |

## PRIMEIRA ETAPA: Configurando o Etherchannel no Switch Multilayer 3650 no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Acessando o Range de Interface GigabitEthernet de Ligação com o Switch Layer 2960
    interface range GigabitEthernet 1/0/1 - 2

      !Configurando o Grupo do Etherchannel em modo Ativo
      channel-group 1 mode active

      !Saindo das Interfaces GigabitEthernet
      exit

    !Configurando a Interface Virtual do Grupo 1 do Etherchannel
    interface Port-channel 1

      !Configurando o Modo de Switching da Interface Etherchannel
      switchport

      !Configurando o Modo Trunk da Interface Etherchannel
      switchport mode trunk

      !Iniciando a Interface Etherchannel
      no shutdown

      !Saindo da Interface Etherchannel
      exit

    !Acessando o Range de Interface GigabitEthernet de Ligação com o Switch Layer 2960
    interface range GigabitEthernet 1/0/3 - 4
      channel-group 2 mode active
      exit

    !Configurando a Interface Virtual do Grupo 2 do Etherchannel
    interface Port-channel 2
      switchport
      switchport mode trunk
      no shutdown
      end

  !Salvando as configurações da RAM para a NVRAM
  write
```

## SEGUNDA ETAPA: Configurando o Etherchannel no Switch Layer 2 2960 Lado Esquerdo no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Acessando o Range de Interface GigabitEthernet de Ligação com o Switch Multilayer 3650
    interface range GigabitEthernet 0/1 - 2
      channel-group 1 mode passive
      exit

    !Configurando a Interface Virtual do Grupo 1 do Etherchannell
    interface Port-channel 1
      switchport
      switchport mode trunk
      no shutdown
      exit

    !Acessando o Range de Interface FastEthernet de Ligação com o Switch Layer 2960
    interface range FastEthernet 0/23 - 24
      channel-group 3 mode active
      exit

    !Configurando a Interface Virtual do Grupo 3 do Etherchannel
    interface Port-channel 3
      switchport
      switchport mode trunk
      no shutdown
      end

  !Salvando as configurações da RAM para a NVRAM
  write
```

## TERCEIRA ETAPA: Configurando o Etherchannel no Switch Layer 2 2960 Lado Direito no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Acessando o Range de Interface GigabitEthernet de Ligação com o Switch Multilayer 3650
    interface range GigabitEthernet 0/1 - 2
      channel-group 2 mode passive
      exit

    !Configurando a Interface Virtual do Grupo 2 do Etherchannell
    interface Port-channel 2
      switchport
      switchport mode trunk
      no shutdown
      exit

    !Acessando o Range de Interface FastEthernet de Ligação com o Switch Layer 2960
    interface range FastEthernet 0/23 - 24
      channel-group 3 mode passive
      exit

    !Configurando a Interface Virtual do Grupo 3 do Etherchannel
    interface Port-channel 3
      switchport
      switchport mode trunkk
      no shutdown
      end

  !Salvando as configurações da RAM para a NVRAM
  write
```

## QUARTA ETAPA: Verificando as Configurações dos Etherchannel dos Switches no Cisco Packet Tracer.

```python
!Visualizando as configurações da memória RAM
show running-config | section interface

!Visualizando as configurações das Interfaces Port-Channel
show running-config | section interface Port-channel

!Listando as Interfaces do Etherchannel
!Os estados das portas podem aparecer como: P – Ativa no grupo, D – Down, I – Independente 
!(não participa do EtherChannel), S – Em espera ou U – Em uso.
show etherchannel summary

!Visualizando informações detalhadas do EtherChannel
show etherchannel port-channel

!Visualizando o status de um Port-Channel específico:
show interfaces Port-channel <ID> status

!Verificando o estado detalhado das interfaces físicas dentro do EtherChannel:
show interfaces etherchannel

!Verificando o status de cada porta membro do EtherChannel
show interfaces status

!Testando o balanceamento de carga do EtherChannel:
show etherchannel load-balance

!Testando a conexão nos Desktops da Rede com o Protocolo ICMP
ping 192.168.1.1
ping 172.16.0.33
tracert 192.168.1.1
tracert 172.16.0.33
```