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
#01_ Configurando a Interface do Roteador 4321 do Cenário B no Cisco Packet Tracer;<br>
#02_ Configurando a Interface do Roteador 1941 do Cenário A no Cisco Packet Tracer;<br>
#03_ Configurando a Rota Padrão no Router 1941 do Cenário A no Cisco Packet Tracer;<br>
#04_ Configurando a Rota Padrão no Switch Multilayer 3650 do Cenário B no Cisco Packet Tracer;<br>
#05_ Configurando a Rota Padrão e Rota Estática no Router 4321 do Cenário B no Cisco Packet Tracer;<br>
#06_ Verificando as Configurações de Rotas no Router e Switch no Cisco Packet Tracer.

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração da Rota Estática do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

## PRIMEIRA ETAPA: Configurando a Interface do Roteador 4321 do Cenário B no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Interface de Interligação com o Router 1941 (RT-01)
    interface GigabitEthernet 0/0/0

      !Habilitando o Tipo de Média utilizado na Porta GigabitEthernet
      !OBSERVAÇÃO-01: O Router 4321 utilizada a porta GigabitEthernet 0/0/0 tanto para Par-Metálico como para Fibra Óptica
      media-type sfp

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
      end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## SEGUNDA ETAPA: Configurando a Interface do Roteador 1941 do Cenário A no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Interface de Interligação Com Router 4321
    interface GigabitEthernet 0/0/0

      !Configurando a descrição da Interface
      description Interface de WAN com o Router 4321 RT-02

      !Configuração do endereço IPv4 do Router 1941
      ip address 10.0.0.1 255.255.255.252
      no shutdown
      end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## TERCEIRA ETAPA: Configurando a Rota Padrão no Router 1941 do Cenário A no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Rota Estática Padrão de Saída para o Router 4321
    !DICA-02: rota estática é indicada para links Ponto-a-Ponto e para redes simples, com poucos roteadores (saltos/caminhos)
    !DICA-03: rota estática recebe a letra: S (static) no início da rota declarada manualmente na Tabela de Roteamento
    !OBSERVAÇÃO-05: na tabela de roteamento temos as opções: L - local (Endereço Local) e C - connected (Rede Diretamente Conectada)
    !OBSERVAÇÃO-06: rota estática é configurada manualmente em cada equipamento da rede, sua atualização não é dinâmica (automática)
    !OBSERVAÇÃO-07: rota estática tem a Distância Administrativa (AD - Confiabilidade) de: 1 (um)
    !OBSERVAÇÃO-08: rota estática tem Métrica (Custo) de: 0 (zero)
    !OBSERVAÇÃO-09: rota estática pode encaminhar redes por: Endereço IPv4/IPv6 de Próximo Salto ou Interface de Saída
    !EXEMPLO-02: ip route Rede_de_Destino Máscara_de_Rede_de_Destino Interface_de_Saída ou IP_do_Próximo_Salto Distância_Administrativa
    ip route 0.0.0.0 0.0.0.0 10.0.0.2
    end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## QUARTA ETAPA: Configurando a Rota Padrão no Switch Multilayer 3650 do Cenário B no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Rota Estática Padrão de Saída para o Router 4321
    ip route 0.0.0.0 0.0.0.0 172.16.0.30
    end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## QUINTA ETAPA: Configurando a Rota Padrão e Rota Estática no Router 4321 do Cenário B no Cisco Packet Tracer.

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal

    !Configurando a Rota Estática Padrão de Saída para o Router 4321
    ip route 0.0.0.0 0.0.0.0 172.16.0.29
    ip route 192.168.1.0 255.255.255.0 10.0.0.1
    end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## SEXTA ETAPA: Verificando as Configurações de Rotas no Router e Switch no Cisco Packet Tracer.

```python
!Visualizando as configurações da memória RAM das Interfaces
show running-config | section interface

!Visualizando as configurações da memória RAM das Rotas Estática
show running-config | section ip route

!Verificando as informações das Interfaces Local
show ip interface brief

!Verificando as informações da Tabela de Roteamento Local
show ip route

!Testando a conexão nos Desktops da Rede com o Protocolo ICMP
ping 192.168.1.1
ping 172.16.0.33
tracert 192.168.1.1
tracert 172.16.0.33
```