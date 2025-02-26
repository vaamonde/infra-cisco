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
Versão: 0.05<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

## PRIMEIRA ETAPA: Configuração dos Gateways das VLAN's utilizando os SVI's no Switch Multilayer 3650
```python
!Acessando o modo de Configuração Global de Comandos
configure terminal

  !Habilitando o Recurso de Roteamento no Switch Multilayer 3650
  !DICA-01: habilitar o recurso de roteamento no Switch Layer 3 permite utilizar protocolos de 
  !roteamento Estático ou Dinâmico no Switch Layer 3 ou Multilayer
  !OBSERVAÇÃO-01: habilitar o recurso de roteamento do Switch Layer 3 somente se for necessário
  !OBSERVAÇÃO-02: por padrão o recurso de roteamento do Switch Layer 3 está desligado/desabilitado
  !OBSERVAÇÃO-03: os recursos de roteamento permite utilizar protocolos dinâmicos como o: RIP (Routing
  !Information Protocol), RIPv2 (Routing Information Protocol Version 2), EIGRP (Enhanced Interior 
  !Gateway Routing Protocol) e OSPF (Open Shortest Path First).
  !IMPORTANTE-01: o Switch Layer 3 não foi projetado para trabalhar com Roteamento de WAN (Internet), 
  !ele é indicado somente para a Rede Local LAN utilizando so protocolos IGP (Interior Gateway Protocol)
  ip routing

  !Configurando a Interface de Gateway da VLAN 10 Financeiro
  interface vlan 10
    description Interface de Gateway da VLAN 10 FIN
    ip address 172.16.0.158 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface de Gateway da VLAN 20 Estoque
  interface vlan 20
    description Interface de Gateway da VLAN 20 EST
    ip address 172.16.0.190 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface de Gateway da VLAN 30 Faturamento
  interface vlan 30
    description Interface de Gateway da VLAN 30 FAT
    ip address 172.16.0.222 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface de Gateway da VLAN 40 Gerencia
  interface vlan 40
    description Interface de Gateway da VLAN 40 GER
    ip address 172.16.0.254 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface de Gateway da VLAN 50 Servidores
  interface vlan 50
    description Interface de Gateway da VLAN 50 SERV
    ip address 172.16.0.62 255.255.255.224
    no shutdown
    exit

  !Configurando a Interface de Gateway da VLAN 60 Wireless
  interface vlan 60
    description Interface de Gateway da VLAN 60 WIFI
    ip address 172.16.0.94 255.255.255.224
    no shutdown

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## SEGUNDA ETAPA: Configuração do Gateway da SVI no Switch Layer 2 2960 (Lado Esquerdo)
```python
!Acessando o modo de Configuração Global de Comandos
configure terminal

  !Configurando o Gateway Padrão do Gerenciamento do Switch Layer 2 2960
  ip default-gateway 172.16.0.97

  !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
  end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## TERCEIRA ETAPA: Configuração do Gateway da SVI no Switch Layer 2 2960 (Lado Direito)
```python
!Acessando o modo de Configuração Global de Comandos
configure terminal

  !Configurando o Gateway Padrão do Gerenciamento do Switch Layer 2 2960
  ip default-gateway 172.16.0.97

  !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
  end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```

## QUARTA ETAPA: Verificando as Configurações dos Switches.
```python
!Visualizando as Configurações do Running-Config (RAM)
show running-config

!Visualizando as configurações da memória RAM
show running-config | section interface

!Verificando as informações das Interfaces de Trunk
show ip interface brief
show ip route
```