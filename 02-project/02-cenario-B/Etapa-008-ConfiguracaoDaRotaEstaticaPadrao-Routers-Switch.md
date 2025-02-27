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

## PRIMEIRA ETAPA: Configurando a Interface do Roteador 4321 no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Interface de Interligação com o Router 1941 (RT-01)
    interface GigabitEthernet 0/1

      !Configurando a descrição da Interface
      description Interface de WAN com o Router 1941 RT-01

      !Configuração do endereço IPv4 do Router 4321
      !DICA-01: configuração das Interface de WAN, os endereços IPv4/IPv6 devem pertencer a mesma rede
      !OBSERVAÇÃO-02: configuração de Link Ponto-a-Ponto (Point-to-Point) é recomendado utilizar endereços IPv4 /30
      !OBSERVAÇÃO-03: o CIDR /30 permite apenas 4 endereços IPv4 válidos: ID Rede, Primeiro e Último endereço IPv4 e Broadcast
      !EXEMPLO-01: 2^2-2=2 (2 = Base | ^2 = Exponenciação de 2 bits emprestados | -2 = Subtração do ID de Rede e Broadcast)
      !OBSERVAÇÃO-04: por padrão todas as Interfaces de Roteador está com o Status Shutdown (Desligadas)
      ip address 10.0.0.2 255.255.255.252
      no shutdown
      exit

    !Configurando a Interface de Interligação com Switch Multilayer 3650
    interface GigabitEthernet 0/0

      !Configurando a descrição da Interface
      description Interface de LAN com o Switch Multilayer 3650

      !Configuração do endereço IPv4 do Router 4321
      !OBSERVAÇÃO-05: esse endereço será o Gateway para o Switch Multilayer 3650
      ip address 172.16.0.1 255.255.255.224
      no shutdown
      exit

    !Configurando a Rota Estática para atingir a Rede 192.168.1.0/24 do Cenário-A
    !DICA-02: rota estática é indicada para links Ponto-a-Ponto e para redes simples, com poucos roteadores (saltos/caminhos)
    !DICA-03: rota estática recebe a letra: S (static) no início da rota declarada manualmente na Tabela de Roteamento
    !OBSERVAÇÃO-06: na tabela de roteamento temos as opções: L - local (Endereço Local) e C - connected (Rede Diretamente Conectada)
    !OBSERVAÇÃO-07: rota estática é configurada manualmente em cada equipamento da rede, sua atualização não é dinâmica (automática)
    !OBSERVAÇÃO-08: rota estática tem a Distância Administrativa (AD - Confiabilidade) de: 1 (um)
    !OBSERVAÇÃO-09: rota estática tem Métrica (Custo) de: 0 (zero)
    !OBSERVAÇÃO-10: rota estática pode encaminhar redes por: Endereço IPv4/IPv6 de Próximo Salto ou Interface de Saída
    !EXEMPLO-02: ip route Rede_de_Destino Máscara_de_Rede_de_Destino Interface_de_Saída ou IP_do_Próximo_Salto Distância_Administrativa
    ip route 192.168.1.0 255.255.255.0 10.0.0.1
    ip route 192.168.3.0 255.255.255.0 192.168.2.1
    end

!Salvando as configurações da memória RAM para a memória NVRAM
write

```

## SEGUNDA ETAPA: Configurando a Rota Padrão no Switch Multilayer 3650 no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable
  configure terminal

    !Configurando a Rota Padrão para o Gateway do Router 1941-2
    !DICA-04: a rota padrão (Default Route), também conhecida como “Gateway de Último Recurso”, é utilizada quando não há rotas conhecidas
    !OBSERVAÇÃO-11: todos os pacotes para destinos desconhecidos da Tabela do Roteador são enviados para o endereço de rota padrão
    !OBSERVAÇÃO-12: o endereço de rota padrão no IPv4 (Na notação CIDR) é o: 0.0.0.0/0, também conhecido como “Rota dos Quatro Zeros”.
    !OBSERVAÇÃO-13: a rota padrão é utilizada para indicar uma rede além dos seus roteadores, como Links com ISP, WAN, VPN, Internet etc 
    !OBSERVAÇÃO-14: a rota padrão estática recebe a letra S com Asterisco: S* que significa que é um Gateway of last resort
    ip route 0.0.0.0 0.0.0.0 192.168.2.254
    end
  write

```

## TERCEIRA ETAPA: Configurando a Rota Padrão no Router 1941 no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable
  configure terminal
    !Configurando a Interface de Interligação com o Router 1941-2
    interface GigabitEthernet 0/1
      description Interface de WAN com o Router 1941-2
      ip address 10.0.0.1 255.255.255.252
      no shutdown
      exit
      
    !Configurando a Rota Estática para atingir as Redes 192.168.2.0/30 e 192.168.3.0/30
    !OBSERVAÇÃO-15: nesse cenário vou utilizar a Interface de Saída para as Redes
    ip route 192.168.2.0 255.255.255.0 GigabitEthernet 0/1
    ip route 192.168.3.0 255.255.255.0 GigabitEthernet 0/1
    end
  write

```

## TERCEIRA ETAPA: Verificando as Configurações de Rotas no Router e Switch no Cisco Packet Tracer.

```python
!Visualizando as configurações da memória RAM
show running-config | section interface
show running-config | section ip route

!Verificando as informações das Interfaces e Tabela de Roteamento Local
show ip interface brief
show ip route

!Testando a conexão nos Desktops da Rede com o Protocolo ICMP
ping 192.168.1.1
ping 192.168.3.1
tracert 192.168.1.1
tracert 192.168.3.1
```