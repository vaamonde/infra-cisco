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
Data de atualização: 26/11/2024<br>
Versão: 0.03<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

## PRIMEIRA ETAPA: Conhecendo o Serviço do DHCP Server no Cisco Packet Tracer.

**DHCPv4 (Dynamic Host Configuration Protocol)** é um protocolo de serviço *TCP/IP (Transmission Control Protocol/Internet Protocol)* que oferece configuração dinâmica de dispositivos finais, com concessão de endereços IP de Host (Computador), máscara de sub-rede, gateway padrão, servidores DNS (Domain Name Service), sufixos de pesquisa do DNS, servidores WINS (Windows Internet Name Service), servidores NTP (Network Time Protocol) é muito mais.

O protocolo padrão utilizado pelo DHCP Server é o: *UDP (User Datagram Protocol)* na porta padrão: *67*.

**Escopo DHCP:** Trata-se do intervalo completo dos possíveis endereços IP de uma rede. Os escopos definem a sub-rede física da rede que vai oferecer os serviços do DHCP.

## SEGUNDA ETAPA: Configurando o Serviço do DHCP Server no Cisco Packet Tracer.

**OBSERVAÇÃO-01:** por padrão o Serviço de DHCP Server no Cisco Packet Tracer está: *desligado*

**OBSERVAÇÃO-02:** o nome do escopo padrão do DHCP Server no Cisco Packet Tracer tem que ser: *serverPool*

**DICA-01:** o escopo inicial está sempre relacionado a Placa de Rede e sua Configuração do Endereçamento IPv4, com base nesse endereço que é ofertado o escopo de rede.

**DICA-02:** geralmente em Servidores Microsoft ou GNU/Linux, após a instalação do Serviço do DHCP Server ele está desligado por padrão para não entrar em conflito com outros servidores na rede.

**CUIDADO-01:** é recomendado ter apenas: *1 (um) Servidor DHCP* na rede, em redes mais complexas existe a possibilidade de mais servidores para prover redundância.

**OBSERVAÇÃO-03:** o Switch Cisco Catalyst Layer 3 3560 ou Router possui os recursos para a configuração do DHCP Server, para redes pequenas e de médio porte é recomendado o seu uso, para redes grandes ou complexas o seu uso é limitado em alguns recursos, principalmente de monitoramento, relatórios e integrações de serviços.

```python
!Habilitando o Serviço do DHCP Server no Servidor 02
Server-02
  Services
    DHCP

!Configurando o Escopo padrão da Rede: 172.16.0.64/27 (Wireless)
Interface:                 GigabitEthernet0
Service:                   On
Pool Name:                 wireless
Default Gateway:           172.16.0.94     (Interface de SVI de Gateway da VLAN-60 do Switch Layer 3)
DNS Server:                172.16.0.33     (DNS Preferencial ou Alternativo - no Cisco Packet Tracer e limitado)
Start IP Address:          172.16.0.65     (Início da Faixa de Oferta de Endereços IPv4)
Subnet Mask:               255.255.255.224
Maximum Number of Users:   28              (Fim da Faixa de Oferta de Endereços IPv4 - 65 até 93)
TFTP Server:               172.16.0.33
WLC Address:               NÃO UTILIZADO NESSE CENÁRIO (Endereço IP do WLC - Wireless LAN Controller)
<Save>

!Configurando o Escopo padrão da Rede: 172.16.0.128/27 (Financeiro)
Interface:                 GigabitEthernet0
Service:                   On
Pool Name:                 financeiro
Default Gateway:           172.16.0.158    (Interface de SVI de Gateway da VLAN-10 do Switch Layer 3)
DNS Server:                172.16.0.33     (DNS Preferencial ou Alternativo - no Cisco Packet Tracer e limitado)
Start IP Address:          172.16.0.129    (Início da Faixa de Oferta de Endereços IPv4)
Subnet Mask:               255.255.255.224
Maximum Number of Users:   28              (Fim da Faixa de Oferta de Endereços IPv4 - 65 até 93)
TFTP Server:               172.16.0.33
WLC Address:               NÃO UTILIZADO NESSE CENÁRIO (Endereço IP do WLC - Wireless LAN Controller)
<Save>
```

## TERCEIRA ETAPA: Configurando o Recurso de Ajuda do DHCP no Switch Multilayer 3650 no Cisco Packet Tracer.

O **IP Helper (Ajuda de Endereço IP)** são endereços IPs configurados em uma Interface Roteada como uma Interface de VLAN ou uma Interface Ethernet (FastEthernet, GigabitEthernet, etc) de Roteadores ou Switch Layer 3, permitindo que esse dispositivo específico atue como um intermediário (middle man) para encaminhar a solicitação DHCP do BOOTP (Broadcast) que recebe em uma interface para o Servidor DHCP especificado pelo endereço *IP Helper* via **Unicast**.

As mensagens do DHCPv4 não é o único serviço no qual o roteador pode ser configurado para retransmitir as solicitações, por padrão o comando: *ip helper-address* encaminha os seguintes pacotes de serviços UDP: 
 
A) Porta 37: tempo;<br>
B) Porta 49: TACACS;<br>
C) Porta 53: Consulta DNS;<br>
D) Porta 67: cliente de DHCP/BOOTP;<br>
E) Porta 68: servidor de DHCP/BOOTP;<br>
F) Porta 69: TFTP;<br>
G) Porta 137: serviço de nomes NetBIOS;<br>
H) Porta 138: serviço de conjunto de dados NetBIOS.<br>

**OBSERVAÇÃO-04:** vale lembrar que o Roteador por padrão não encaminha Mensagens de Broadcast para outras Redes conectadas.

```python
!Acessando o modo de Configuração Global de Comandos
configure terminal

  !Configurando o suporte da Ajuda de Endereço DHCPv4 nas Interfaces de SVI
  interface range vlan 10, 20, 30, 40, 60

    !Configurando o Recurso de Ajuda de Endereço DHCPv4 na Interface SVI do Switch Multilayer
    !DICA-01: configurando o endereço IPv4 do Servidor de DHCPv4 que possui o Escopo da Rede configurado
    !OBSERVAÇÃO-01: esse recurso funciona no Router ou Switch Layer 3, principalmente quando trabalhamos
    !com VLAN e Sub-Redes que os Escopos do DHCP estão configurado em um servidor dedicado.
    ip helper-address 172.16.0.33

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## TERCEIRA ETAPA: Testando o Serviço do DHCP Server no Cisco Packet Tracer.

a) Abrindo o Prompt de Comando do Desktop;

**DICA-03** não confunda Terminal com Command Prompt, Terminal é utilizado para se conectar no Switch ou Router utilizando o Cabo Console, já o Command Prompt (Prompt de Comando) é utilizado para testar as configurações de rede e acessar remotamente o Switch ou Router.

```bash
!Verificando o endereço IPv4 configurado no Desktop
C:\> ipconfig

!Verificando o endereço detalhado IPv4 configurado no Desktop
C:\> ipconfig /all

!Liberando o Aluguel do Leasing do DHCP Client
C:\> ipconfig /release

!Renovando o Aluguel do Leasing do DHCP Cliente
C:\> ipconfig /renew

!Verificando o endereço detalhado IPv4 configurado no Desktop
C:\> ipconfig /all

!Testando a comunicação com o Server 02 utilizando o pacote ICMP (Internet Control Message Protocol)
C:\> ping 172.16.0.33
```