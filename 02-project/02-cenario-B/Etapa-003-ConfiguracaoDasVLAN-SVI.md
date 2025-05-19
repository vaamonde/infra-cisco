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
Data de atualização: 19/05/2025<br>
Versão: 0.06<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ Conhecendo as VLANs (Virtual LANs – Redes Locais Virtuais) no Cisco Packet Tracer;<br>
#02_ Conhecendo os Ranges das VLANs no Cisco Packet Tracer;<br>
#03_ Tipos de VLANs no Cisco Packet Tracer;<br>
#04_ Conhecendo os Tipos de Portas das VLANs no Cisco Packet Tracer;<br>
#05_ Configurando as VLANs no Switch Multilayer 3650 (CENTRO - DISTRIBUIÇÃO);<br>
#06_ Configurando as VLANs no Switch Cisco Layer 2 2960 (LADO ESQUERDO - ACESSO);<br>
#07_ Configurando as VLANs no Switch Cisco Layer 2 2960 (LADO DIREITO - ACESSO);<br>
#08_ Verificando as Configurações dos Switches e Roteadores.

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração das VLANs do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

## PRIMEIRA ETAPA: Conhecendo as VLANs (Virtual LANs – Redes Locais Virtuais) no Cisco Packet Tracer.

As **VLANs (Virtual LANs – Redes Locais Virtuais)** é uma rede logicamente independente, várias VLANs podem coexistir em um mesmo Switch, de forma a dividir uma rede local em mais de uma rede, criando domínios de Broadcast separados.

As VLANs permitem a segmentação das redes físicas, sendo que a comunicação entre máquinas de VLANs diferentes terá de passar obrigatoriamente por um **Roteador** ou outro equipamento capaz de realizar o **Roteamento**, esse equipamento será o responsável por encaminhar o tráfego entre as VLANs distintas (iguais).

As VLANs oferecem vantagens das quais se destacam: *segurança, escalabilidade, flexibilidade, redução de custos, etc.*

Um Switch com a capacidade de criar VLANs suporta dois tipos de configurações de porta: 

1. **Access Port** (porta de acesso para conexões de dispositivos finais);<br>
2. **Trunk Port** (porta de tronco para interligação de Switch, Router ou Server).

## SEGUNDA ETAPA: Conhecendo os Ranges das VLANs no Cisco Packet Tracer.

Os ranges de VLANs nos Switches Cisco são divididos em: 

A) **0 e 4095** Reservadas (Reserved - apenas para uso do sistema operacional IOS, você não pode ver ou usar essas VLANs);<br>
B) **1 Padrão/Nativa** (Default/Native - você pode usar essa VLAN, está associada por padrão em todas as Portas do Switch, você não pode deletar essa VLAN);<br> 
C) **2 até 1001 Nativas** (Normal - usadas para as VLANs Ethernet, você pode criar, usar e excluir essas VLANs, são armazenadas no arquivo **vlan.dat**);<br> 
D) **1002 até 1005 Nativa** (Normal - padrões da Cisco para Redes FDDI (Fiber Distributed Data Interface) e Token Ring, você não pode excluir essas VLANs);<br>
E) **1006 até 4094 Estendidas** (Extended elas são usadas principalmente em redes de provedores de serviços para permitir o provisionamento do número do assinante).

## TERCEIRA ETAPA: Tipos de VLANs no Cisco Packet Tracer.

Exite também dois tipos de associações de VLANs: 

A) **VLANs Estáticas** (Static - configurada manualmente na porta de rede do Switch ou do Router);<br>
B) **VLANs Dinâmicas** (Dynamic - são criadas e alteradas dinamicamente via Software como por exemplo o VMPS (VLAN Management Policy Server)).

## QUARTA ETAPA: Conhecendo os Tipos de Portas das VLANs no Cisco Packet Tracer.

Uma Porta de **Acesso (access)**, permite associar uma porta do Switch a uma VLAN, as portas do tipo acesso são usadas para conectar dispositivos finais (Desktop, Notebook, Impressoras, Access Point, etc), por padrão, todas as portas dos Switches estão associadas na *VLAN Padrão/Nativa 1*, que transporta os dados sem marcação (Untagged VLAN).

Por padrão todas as *Portas de Rede dos Switches Catalyst Cisco estão* configuradas no **Modo Dinâmico Automática** (switchport mode dynamic auto), nessa configuração a Interface tenta passar para o **Modo Trunk** se a outra extremidade também estiver configurada como **Dynamic Desirable** ou como **Trunk**. Caso contrário, permanece como **Modo Access**.

## QUINTA ETAPA: Configurando as VLANs no Switch Multilayer 3650 (CENTRO - DISTRIBUIÇÃO)
```python
!Acessando o modo de Configuração Global de Comandos
configure terminal

  !Criando as VLANs Standard (Padrão) no Switch Multilayer 3650
  !DICA-01: por padrão é recomendado trabalhar nos Switches Catalyst ou Multilayer a faixa de VLANs 
  !Standard (padrão de 2 até 1001)
  vlan 10

    !Configurando o nome da VLAN Standard
    !DICA-02: a configuração do nome da VLAN facilita na administração e auditoria com o comando: 
    !show vlan brief
    !OBSERVAÇÃO-01: para criar uma nova VLAN não é necessário sair do modo de configuração de VLAN 
    !com o comando exit, pode digitar no mesmo nível a nova VLAN que você está criando.
    name FIN

  vlan 20
    name EST
  vlan 30
    name FAT 
  vlan 40
    name GER
  vlan 50
    name Server
  vlan 60
    name Wireless
  vlan 99
    name SVI-Switches
    exit

  !Configurando a Interface de Gerenciamento de SVI do Switch Multilayer 3650
  !OBSERVAÇÃO-02: as SVIs dos Switches Layer 2 e 3 serão configuradas utilizando a VLAN 99
  interface vlan 99
    description Interface de SVI de Gerenciamento Switch Multilayer 3650
    ip address 172.16.0.97 255.255.255.224
    no shutdown
    exit

  !Configurando as Interfaces de Acesso a VLAN 50 dos Servidores
  !DICA-03: a opção range do comando interface possibilita fazer a mesma configuração em várias interfaces
  !OBSERVAÇÃO-03: existe a possibilidade de utilizar a opção de range para portas não consecutivas, 
  !utilizando o separador , (vírgula) e adicionando o nome das portas na configuração.
  !EXEMPLO-01: interface range fastEthernet 0/1 - 5, fastEthernet 0/10, fastEthernet 0/15
  interface range GigabitEthernet 1/0/10 - 19

    !Descrição das Interfaces dos Servidores
    description Interface de Acesso da VLAN 50 dos Servidores

    !Configurando a Interface (Porta de Rede) para o Modo de Acesso (Access)
    !DICA-04: uma Interface de Acesso pertence e trafega dados de uma única VLAN
    !OBSERVAÇÃO-04: por padrão todos os Switches tem a VLAN 1 que não pode ser removida e está associada 
    !a todas as Interfaces, é recomendado sempre configurar as Interfaces dos dispositivos finais para 
    !o Modo Acesso (Access).
    !OBSERVAÇÃO-05: tipos de configurações das Interfaces: access (porta de acesso), trunk (porta de tronco)
    !e dynamic (porta dinâmica)
    switchport mode access

    !Desabilitando o recurso de auto-negociação da Interface (Porta de Rede)
    !DICA-05: por padrão todas as Interfaces dos Switches está com o recurso do DTP (Dynamic Trunk 
    !Protocol) habilitado nas Interfaces
    !OBSERVAÇÃO-06: é recomendado desabilitar o recurso de DTP nas Interfaces que são do tipo Acesso 
    !(Access) para que servidores ou clientes não configure as opções de Trunk nessas portas.
    switchport nonegotiate

    !Configurando o acesso a VLAN 50 das Interfaces dos Servidores
    !DICA-06: por padrão só podemos configurar uma VLAN na porta de rede do Switch
    !OBSERVAÇÃO-07: a partir do momento que configuramos a VLAN na porta do Switch, todos os quadros 
    !(frames) recebem a Tag (etiqueta) dot1q (IEEE 802.1Q) no seu Frame (quadro) Ethernet quando 
    !transmite pacotes pela porta de rede do Switch
    switchport access vlan 50

    !Saindo das configurações da Interface
    exit

  !Configurando a Interface de Acesso a VLAN 60 do Access Point 802.11-AC
  interface range GigabitEthernet 1/0/20 - 23
    description Interface de Acesso da VLAN 60 do Access Point AC
    switchport mode access
    switchport nonegotiate
    switchport access vlan 60
    exit

  !Acessando todas as Interfaces (Porta de Rede) que não estão sendo utilizadas
  !OBSERVAÇÃO IMPORTANTE: Esse recurso previne conectar dispositivos nas portas que estão Ligadas 
  !(No Shutdown) por padrão e te acesso a rede sem restrição.
  interface range GigabitEthernet 1/0/5 - 9, GigabitEthernet 1/0/14 - 19, GigabitEthernet 1/0/21 - 23, GigabitEthernet 1/1/1 - 4

    !Descrição das Interfaces
    description Interfaces Desligadas

    !Desligando todas as Portas de Redes do Switch Layer 3
    shutdown

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## SEXTA ETAPA: Configurando as VLANs no Switch Cisco Layer 2 2960 (LADO ESQUERDO - ACESSO)
```python
configure terminal

  !Criando as VLANs Standard (Padrão) no Switch Layer 2 2960
  vlan 10
    name FIN
  vlan 20
    name EST
  vlan 30
    name FAT 
  vlan 40
    name GER
  vlan 50
    name Server
  vlan 60
    name Wireless
  vlan 99
    name SVI-Switches
    exit

  !Configurando a Interfaces de SVI do Switch 2960
  interface vlan 99
    description Interface de SVI de Gerenciamento Switch Layer 2 2960
    ip address 172.16.0.98 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface da VLAN 10 Financeiro
  interface range fastEthernet 0/1 - 4
    description Interface de Acesso da VLAN 10 Financeiro
    switchport mode access
    switchport nonegotiate
    switchport access vlan 10
    exit

  !Configurando a Interface da VLAN 20 Estoque
  interface range fastEthernet 0/5 - 9
    description Interface de Acesso da VLAN 20 Estoque
    switchport mode access
    switchport nonegotiate
    switchport access vlan 20
    exit

  !Configurando a Interface da VLAN 30 Faturamento
  interface range fastEthernet 0/10 - 14
    description Interface de Acesso da VLAN 30 Faturamento
    switchport mode access
    switchport nonegotiate
    switchport access vlan 30
    exit

  !Configurando a Interface da VLAN 40 Gerencia
  interface range fastEthernet 0/15 - 20
    description Interface de Acesso da VLAN 30 Gerencia
    switchport mode access
    switchport nonegotiate
    switchport access vlan 40
    exit

  !Desligando as Interfaces que não estão sendo utilizadas
  interface range fastEthernet 0/2 - 4, fastEthernet 0/6 - 9, fastEthernet 0/11 - 14, fastEthernet 0/16 - 22
    description Interfaces Desligadas
    shutdown

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## SÉTIMA ETAPA: Configurando as VLANs no Switch Cisco Layer 2 2960 (LADO DIREITO - ACESSO)
```python
configure terminal

  !Criando as VLANs Standard (Padrão) no Switch Layer 2 2960
  vlan 10
    name FIN
  vlan 20
    name EST
  vlan 30
    name FAT 
  vlan 40
    name GER
  vlan 50
    name Server
  vlan 60
    name Wireless
  vlan 99
    name SVI-Switches
    exit

  !Configurando a Interfaces de SVI do Switch 2960
  interface vlan 99
    description Interface de SVI de Gerenciamento Switch Layer 2 2960
    ip address 172.16.0.99 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface da VLAN 10 Financeiro
  interface range fastEthernet 0/1 - 4
    description Interface de Acesso da VLAN 10 Financeiro
    switchport mode access
    switchport nonegotiate
    switchport access vlan 10
    exit

  !Configurando a Interface da VLAN 20 Estoque
  interface range fastEthernet 0/5 - 9
    description Interface de Acesso da VLAN 20 Estoque
    switchport mode access
    switchport nonegotiate
    switchport access vlan 20
    exit

  !Configurando a Interface da VLAN 30 Faturamento
  interface range fastEthernet 0/10 - 14
    description Interface de Acesso da VLAN 30 Faturamento
    switchport mode access
    switchport nonegotiate
    switchport access vlan 30
    exit

  !Configurando a Interface da VLAN 40 Gerencia
  interface range fastEthernet 0/15 - 20
    description Interface de Acesso da VLAN 30 Gerencia
    switchport mode access
    switchport nonegotiate
    switchport access vlan 40
    exit

  !Desligando as Interfaces que não estão sendo utilizadas
  interface range fastEthernet 0/2 - 4, fastEthernet 0/6 - 9, fastEthernet 0/11 - 14, fastEthernet 0/16 - 22
    description Interfaces Desligadas
    shutdown

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## OITAVA ETAPA: Verificando as Configurações dos Switches 3650 e 2960.
```python
!Visualizando as Configurações do Running-Config (RAM)
show running-config

!Visualizando as configurações do Running-Config (RAM) filtrando só as interfaces
show running-config | section interface

!Visualizando os status das Interfaces de Rede
show ip interface brief

!Verificando as informações das VLAN (Tabela, Id e Name)
show vlan brief
show vlan id 10
show vlan name FIN
```