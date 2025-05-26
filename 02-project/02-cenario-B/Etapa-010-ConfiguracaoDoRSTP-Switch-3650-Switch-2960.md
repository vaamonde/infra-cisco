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
Data de atualização: 21/05/2025<br>
Versão: 0.06<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ Configurando o RSTP no Switch Multilayer 3650 no Cisco Packet Tracer;<br>
#02_ Configurando o RSTP no Switch Layer 2 2960 Lado Esquerdo no Cisco Packet Tracer;<br>
#03_ Configurando o RSTP no Switch Layer 2 2960 Lado Direito no Cisco Packet Tracer;<br>
#04_ Verificando o RSTP nos Switches Multilayer e Layer 2 no Cisco Packet Tracer.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do Spanning Tree Protocol do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

O **STP (Spanning Tree Protocol)** é um Protocolo da Camada 2 que é executado nas interligações dos Switches Layer 2 e 3, a especificação para o STP é *IEEE 802.1D* (a mais recente especificação é IEEE 802.1Q), o propósito principal do STP é assegurar que você não crie ou exista caminhos redundantes (loops) de camada 2 na rede.

O STP cria uma árvore de Switches presentes na rede e elege o *Switch de Referência*, a partir do qual será criada a árvore, esse Switch é denominado de **Ponte Raiz (Root Bridge)**. A eleição do Root Bridge é feita com base na *Prioridade (Priority)* e também com base no menor endereço *MAC (MAC-Address)*, em uma rede por padrão, pode existir apenas um **Switch Root Bridge na Topologia**.

A prioridade padrão do STP nos Switches da Cisco é: **32768** acrescentado mais: *1 (um)* que faz referência a *Identificação do Sistema (ID sys-id-ext)* com base no valor da **VLAN Padrão ou VLAN configurada**, EXEMPLO: *Bridge ID Priority: 32769 (priority 32768 + sys-id-ext 1)*

A construção da árvore da topologia do STP e feita através do envio dos quadros de: **BPDU (Bridge Protocol Data Unit)**. Os BPDUs são frames enviados para a troca de informações tais como o: *Bridge ID* e o *Custo de Caminho de um Nó* para o Switch Root Bridge.

A) As portas de interligações com outros Switches da Rede do **Root Bridge** são denominadas: *Portas Designadas (Designated Port - DP)*;<br>
B) As portas de interligações dos outros Switches da Rede que não são **Non-Root Bridge** são denominadas: *Porta Raiz (Root Port - RP)*;<br>
C) A escolha do **Root Port** dos **Non-Root Bridge** e feita com base no *Menor Custo da Interface (Largura de Banda)* para o *Switch Root Bridge*, o custo das interfaces do STP padrão é: **Porta de 10Mbit/s = 100 | Porta de 100Mbit/s = 19, Porta de 1 Gbit/s = 4 e Porta de 10 Gbit/s = 2**<br>
D) A interface escolhida com o modo **Root Port** tem o *Menor Custo* para o *Designated Port* e ela e colocada no **Modo de Encaminhamento (Forwarding - FWD)**<br>
E) As interfaces que não são consideradas **Designated Port** são colocadas no **Modo de Bloqueio (Blocked Port - BLK)**;<br>
F) Na topologia do STP, apenas uma Porta e colocada no modo de *Blocked Port* por padrão, somente um processo STP e criado para toda a árvore do STP.

Os 5 estágios da Negociação das Portas do STP são: **Disabled (Desativado), Blocking (Bloqueado), Listening (Ouvindo), Learning (Aprendendo) e Forwarding (Encaminhamento)**

Os tempos utilizados pelo STP são: **2s Hello (Avisos), 15s Forward Delay (Atraso de Encaminhamento) e 20s Max Age (Idade Máxima)**

O tempo de convergência do Protocolo STP pode variar de: **30 até 50 segundos**, dependendo do tamanho da árvore da Topologia do STP.

Portas no status de **Blocking** demora cerca de *20 segundos*, portas no status de **Listening** demora cerca de *15 segundos*, portas nos status de **Learning** demora cerca de *15 segundos*, somente após esses estágios a porta entre no modo de **Forwarding**, hoje esse processo e considerado muito lento para as redes atuais.

O **RSTP (Rapid Spanning Tree - rapid-pvst Per-Vlan Rapid Spanning Tree Mode)** é o protocolo de detecção de topologias de rede que fornecer uma convergência mais rápida para criar uma rede sem *laços de loop de camada 2*, padronizado pelo *IEEE 802.1w* e desenvolvido pela Cisco.

O tempo de convergência do RSTP vária em torno de **2 segundos** em relação ao tempo de convergência padrão do STP que vária de **30 até 50s.**

Os *3 estágios* da Negociação do RSTP são: **Discarding (Descartando), Learning (Aprendendo) e Forwarding (Encaminhamento).**

Os *4 status* da Negociação das Portas do RSTP são: **Root Port (Porta Raiz), Designated Port (Porta Designadas), Alternate Port (Porta Alternativa) e Backup Port (Porta Backup).**

A vantagem do *RSTP em conjunto com o PVST (Per VLAN Spanning-Tree) ou PVST+ (Per VLAN Spanning-Tree Plus)* é a possibilidade de criar instâncias individuais para cada VLAN na Topologia do STP, facilitando a administração e configuração dos melhores caminhos para cada VLAN na Topologia da rede.

## PRIMEIRA ETAPA: Configurando o RSTP no Switch Multilayer 3650 no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando o Spanning-Tree na VLAN 1 para ser o Root Bridge Primário da Topologia
    !DICA-01: geralmente Switch Layer 3 que estão configurados na camada de Distribuição são eleitos Root Bridge
    !OBSERVAÇÃO-01: na configuração da prioridade do STP da VLAN do Switch, temos as opções: 0 até 61440 (com incremento de 4096)
    !OBSERVAÇÃO-02: na configuração do Switch Root Bridge do STP, temos as opções de: primary (Primário) ou secondary (Secundário)
    !OBSERVAÇÃO-03: podemos adicionar mais VLANs para a árvore do STP, utilizando as mesmas opções do comando: ip arp inspection ou
    !dhcp snooping - EXEMPLO: spanning-tree vlan 10 20 30 | spanning-tree vlan 10-30 | spanning-tree vlan 1,5,8,10-30
    !IMPORTANTE-01: com essa configuração, automaticamente o Bridge ID da Switch será decrementado, sendo eleito o Root Bridge com
    !a menor Prioridade (Priority) entre os demais Switches Layer 2 da Rede
    spanning-tree vlan 1 root primary

    !Configurando o Modo de Rapid-Spanning Tree no Switch Multilayer 3650
    !DICA-02: configurar o Rapid-PVST acelera o processo de convergência da rede
    !OBSERVAÇÃO-04: a configuração padrão do Modo do STP dos Switches da Cisco e: PVST
    !OBSERVAÇÃO-05: no Cisco Packet Tracer temos o suporte aos Modos do STP: pvst ou rapid-pvst 
    !IMPORTANTE-02: caso você altere o modo do STP em um Switch na rede é recomendado manter a padronização em todos os Switches 
    !para o mesmo Modo do STP, para não ter conflitos de eleições ou configurações erradas da árvore do STP
    spanning-tree mode rapid-pvst

    !Saindo de todos os níveis
    end

  !Salvando as configurações da RAM para a NVRAM
  write
```

## SEGUNDA ETAPA: Configurando o RSTP no Switch Layer 2 2960 Lado Esquerdo no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando o Modo de Rapid-Spanning no Switch Layer 2 2960
    spanning-tree mode rapid-pvst

    !Saindo de todos os níveis
    end

  !Salvando as configurações da RAM para a NVRAM
  write
```

## TERCEIRA ETAPA: Configurando o RSTP no Switch Layer 2 2960 Lado Direito no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando o Modo de Rapid-Spanning no Switch Layer 2 2960
    spanning-tree mode rapid-pvst

    !Saindo de todos os níveis
    end

  !Salvando as configurações da RAM para a NVRAM
  write
```

## QUARTA ETAPA: Verificando o RSTP nos Switches Multilayer e Layer 2 no Cisco Packet Tracer.

```python
!Visualizando as configurações da memória RAM
show running-config | section spanning-tree

!Comandos de Visualização do STP nos Switches Layer 2 e 3
show spanning-tree
show spanning-tree summary
```