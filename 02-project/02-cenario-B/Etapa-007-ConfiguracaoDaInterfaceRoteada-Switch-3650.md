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

## PRIMEIRA ETAPA: Configurando a Interface Roteada no Switch Multilayer 3650 no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Interface (Porta de Rede) Roteada do Switch Multilayer 3650
    interface GigabitEthernet 1/0/24

      !Desabilitando o recurso de Switch da Porta conectada com o Router 4321
      !DICA-01: desabilitar o recurso de Switch da porta permite transforma a mesma em um Interface de Rede, permitindo
      !adicionar um endereço IPv4 ou IPv6 e utilizar como uma Interface Roteada ou como uma Porta de Gateway.
      no switchport

      !Configurando a Descrição da Interface de Rede do Switch Multilayer
      description Interface de conexão com o Router 4321
      
      !Configurando o endereço de IPv4 de conexão com a Rede do Router 4321
      ip address 172.16.0.30 255.255.255.224
      exit

    !Configurando o Gateway Padrão do Switch Multilayer 3650
    !DICA-02: a configuração do Gateway no Switch Layer 3 com suporte a roteamento será utilizada somente para o acesso
    !remoto ou gerenciamento do Switch, utilizando protocolos como SNMP, Syslog, etc
    !OBSERVAÇÃO-03: para a porta roteada acessar outras redes é necessário a configuração do roteamento estático, dinâmico
    !ou rota padrão.
    ip default-gateway 172.16.0.1
    end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## SEGUNDA ETAPA: Verificando as Configurações do Switch Multilayer 3650 no Cisco Packet Tracer.

```python
!Visualizando as configurações da memória RAM
show running-config | section interface

!Verificando as informações das Interfaces e Roteamento
show ip interface brief
show ip route
```