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
Data de atualização: 16/05/2024<br>
Versão: 0.01<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## Protocolos de Roteamento utilizados no Cisco (APROFUNDAMENTO DE ESTUDO PARA CERTIFICAÇÃO CISCO, COMPTIA, MIKROTIK, UBIQUITI, ETC)

**==== Protocolos: PDU, TCP, UDP, IPv4/IPv6, MAC, CAM e ARP ====**
```bash
A) PDU  (Protocol Data Unit - Protocolo de Unidade de Dados - Camada de Dados do Usuário) 
B) TCP  (Transmission Control Protocol - Protocolo de Controle de Transmissão - Com Confiabilidade)
C) UDP  (User Datagram Protocol - Protocolo de Datagrama do Usuário - Sem Confiabilidade)
D) IPv4 (Internet Protocol - Protocolo de Internet versão 4 - Decimal (Base 10) - 32 Bits - 4 Octetos)
E) IPv6 (Internet Protocol - Protocolo de Internet versão 6 - Hexadecimal (Base 16) - 128 Bits - 8 Hextetos)
F) MAC  (Media Access Control - Controle de Acesso a Média - Hexadecimal (Base 16) - 48 Bits - 12 dígitos Hexadecimal)
G) CAM  (Content Addressable Memory - Tabela de Memória de Acesso Rápido - Endereço MAC para Porta de Rede)
H) ARP  (Address Resolution Protocol - Protocolo de Resolução de Endereços - Endereço IPv4 para Endereço MAC)
```

**==== Protocolos: AS, IGP (RIP, RIPng, EIGRP, OSPF e IS-IS), EGP e BGP (eBGP, iBGP e MP-BGP) ====**
```bash
A) AS  (Autonomous System - Sistema Autônomo)
A) IGP (Interior Gateway Protocol - Protocolo de Gateway Interno: RIP, RIPng, EIGRP, OSPF e IS-IS)
    -> RIP (V1/V2) – Routing Information Protocol (Protocolo de Informações de Roteamento)
    -> RIPng – Routing Information Protocol Next Generation IPv6 (Protocolo de Informações de Roteamento IPv6 de Próxima Geração)
    -> EIGRP – Enhanced Interior Gateway Routing Protocol (Protocolo de Roteamento de Gateway Interno Aprimorado)
    -> OSPF (V2/V3) – Open Shortest Path First (Caminho mais Curto Primeiro)
    -> IS-IS – Intermediate System to Intermediate System (Sistema Intermediário para Sistema Intermediário)
B) EGP (Exterior Gateway Protocol - Protocolo de Gateway Externo: Antigo e Obsoleto)
C) BGP (Border Gateway Protocol - Protocolo de Gateway de Borda: eBGP, iBGP e MP-BGP)
    -> eBGP – External Border Gateway Protocol (Protocolo de Gateway de Fronteira Externa)
    -> iBGP – Internal Border Gateway Protocol (Protocolo de Gateway de Fronteira Interna)
    -> MP-BGP – Multiprotocol Border Gateway Protocol (Protocolo de Gateway de Borda Multiprotocolo)
```

**==== Distância Administrativa (Escolha do Melhor Caminho e Confiabilidade do Link) ====**
```bash
A) AD   0 --> Interface Diretamente Conectada (Ethernet, FastEthernet, GigabitEthernet, etc)
B) AD   1 --> Rota Estática, Rota Flutuante ou Gateway Padrão (Rota Padrão)
C) AD  90 --> EIGRP (Enhanced Interior Gateway Routing Protocol - Protocolo de Roteamento de Gateway Interno Aprimorado)
D) AD 110 --> OSPF (Open Shortest Path First - Caminho Mais Curto Primeiro)
E) AD 115 --> IS-IS (Intermediary System / Intermediary System - Caminho Mais Curto para as Rotas)
E) AD 120 --> RIP (Routing Information Protocol - Protocolo de Informações de Roteamento)
```

**==== Métrica (Custo do Link) dos Protocolos IGP ====**
```bash
A) Rota Estática --> Custo 0 (Mais Prioridade)
B) EIGRP         --> Largura de Banda, Atraso, Confiabilidade, Utilização, MTU (Maximum Transmission Unit) e Contagem de Saltos
C) OSPF          --> Largura de Banda Acumulativa, Menor Custo e Menor Distância
D) IS-IS         --> Caminho mais Curto com base na soma das métricas ao longo de um caminho
E) RIP           --> Contagem de Saltos no Máximo de 15 (Routes)
```

**==== Tecnologias de Links de WAN (Wide Area Network) mais utilizados no Brasil ====**
```bash
A) Links Dedicados e Circuitos Privados: Fibra Óptica Dedicada (Ponto a Ponto ou Internet Dedicada);
B) MPLS (Multiprotocol Label Switching): Rede privada gerenciada pelo provedor;
C) Metro Ethernet: Rede de alta capacidade baseada em Ethernet sobre Fibra Óptica;
D) Fibra Óptica Compartilhada (Broadband / FTTH - Fiber to the Home/Business);
E) Internet via Rádio (Wireless ISP): Alternativa para regiões sem infraestrutura de Fibra Óptica ou Par-Metálico;
F) 4G/4.5G/5G Empresarial (LTE e Redes Móveis): Opção de Backup WAN ou para locais sem outra conectividade;
G) Link E1 (RDSI - Rede Digital de Serviços Integrados): Usado para telefonia e dados em conexões ponto a ponto;
H) X.25 e Frame Relay: Antigas tecnologias de WAN, ainda usadas em bancos e automação industrial;
I) SD-WAN (Software-Defined WAN): Permite usar múltiplos links (MPLS, Fibra, 4G/5G, etc) de forma inteligente;
J) VPN IPsec ou VPN SSL: Utilizada para interligar redes privadas sobre a Internet pública.
```

## PRIMEIRA ETAPA: Configuração do Protocolo OSPF Router Cisco 2911

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Configuração da Interface de Loopback 0 (sempre será a Loopback 0, não mudar o número da Interface)
    interface loopback 0

      !Descrição da Interface de Loopback
      description Interface de Loopback para ID do OSPF do Grupo-0???

      !Endereço IPv4 para o ID do OSPF da Interface de Loopback
      !Verificar o endereçamento IPv4 de Loopback do seu grupo
      !Endereço IPv4 utilizado para o gerenciamento e métrica do Protocolo OSPF
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 270 
      !(NONA ETAPA: Determinação das Configurações do Protocolo de Roteamento Dinâmico OSPF)
      ip address ???.???.???.??? 255.255.255.255

      !Inicializando a interface
      no shutdown

      !Saindo das configurações da Interface
      exit

    !Configurando o Roteamento de OSPF (??? = número de processo local do seu Grupo)
    !Verificar a tabela de Endereçamento para ver o número de Processo Local do seu Grupo
    !Pode existir vários processos locais do OSPF, cada um com uma finalidade diferente
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 270 
    !(NONA ETAPA: Determinação das Configurações do Protocolo de Roteamento Dinâmico OSPF)
    router ospf ???

      !Identificação do Roteador do Processo do OSPF
      !Verificar o endereço IPv4 de Loopback do seu grupo
      !OSPF utiliza o endereço de Loopback para gerenciar os processos locais
      router-id ???.???.???.???

      !Desativando os anúncios do Protocolo OSPF na Interface da LAN
      !Essa interface não vai anunciar suas rotas pela interface, mais pode receber anúncios
      passive-interface gigabitEthernet 0/0

      !Desativando os anúncios do Protocolo OSPF na Interface de Internet
      !Essa interface não vai anunciar suas rotas pela interface, mais pode receber anúncios
      passive-interface gigabitEthernet 0/1

      !Configuração da referência de largura de banda (Métrica) do Protocolo OSPF
      !Utilizado para o cálculo de custo dos links, padrão 10^8 = 100000000 bps (100 Mbps)
      !Link da tabela padrão de métrica do custo dos links do OSPF: 
      !http://nomundodasredes.blogspot.com.br/2012/03/metrica-do-ospf.html
      !https://ciscoredes.com.br/wp-content/uploads/2012/06/Cost_Interface.png
      auto-cost reference-bandwidth 10000

      !Registrar todas as alterações de adjacência e o estado dos links do OSPF
      !Esses registros serão armazenados nos logs do sistema operacional do Router
      !Utilizado principalmente para analise de problemas (troubleshooting) do Protocolo OSPF
      log-adjacency-changes detail

      !Declarando as redes fisicamente conectadas no Router Cisco 2911
      !Utilizando o recurso de Wildcard Mask (máscara coringa - máscara invertida)
      !Configuração da Área 0 (Single Area - Backbone, obrigatória existir na topologia do OSPF)
      !Calculando a máscara coringa: 255.255.255.255 - sua_mascara = máscara coringa/invertida
      !Exemplo do cálculo: 255.255.255.255 - 255.255.255.252 = 0.0.0.3
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 270 
      !(NONA ETAPA: Determinação das Configurações do Protocolo de Roteamento Dinâmico OSPF)
      network 172.16.???.0 0.0.0.255 area 0
      network 172.16.???.0 0.0.0.255 area 0
      network 172.16.???.0 0.0.0.255 area 0
      network 172.16.???.0 0.0.0.255 area 0
      network 172.16.???.0 0.0.0.255 area 0
      network 172.16.???.0 0.0.0.255 area 0
      network 192.168.1.??? 0.0.0.3 area 0
      network 192.168.1.??? 0.0.0.3 area 0

      !Saindo de todas as configurações
      end

  !Salvando todas as configurações
  copy running-config startup-config

  !Comandos de Verificação do Protocolo OSPF e da última etapa de configuração do Routers

  !Visualizando as configurações
  show running-config

  !Visualizando parâmetros e estatísticas do processo do protocolo de roteamento IP
  show ip protocols

  !Visualizando as configurações de endereçamento IPv4
  show ip interface brief

  !Visualizando as informações de Roteamento
  show ip route

  !Visualizando as informações de Roteamento do Open Shortest Path First (OSPF)
  show ip route ospf 

  !Visualizando as informações do Processo do OSPF
  show ip route ospf ??? (ID)

  !Visualizando as informações das listas das vizinhanças do OSPF
  show ip ospf neighbor

  !Visualizando as informações sumarizadas do banco de dados do OSPF
  show ip ospf database

  !Visualizando as informações dos statos dos links do OSPF
  show ip ospf database router

  !Visualizando as informações do processo do OSPF
  show ip ospf ??? (ID)

  !Visualizando as informações de interfaces do OSPF
  show ip ospf interface
```

## A PARTIR DESSE MOMENTO TODOS OS GRUPOS DEVERÃO SE PINGAR, PINGAR O ENDEREÇO IPv4 DE CADA SWITCH DOS GRUPOS E TAMBÉM OS DESKTOPS.