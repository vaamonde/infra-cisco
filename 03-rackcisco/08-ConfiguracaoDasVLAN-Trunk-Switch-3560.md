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
Data de atualização: 28/10/2025<br>
Versão: 0.03<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560, SW-9200L, RT-2911 e RT-8200L

## PRIMEIRA ETAPA: Configuração das VLAN's e Trunk no Switch Cisco Catalyst 3560 e 9200

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Criando as VLANs Standard (Padrão) no Switch Layer 3 3560 ou 9200
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 77
    !(TERCEIRA ETAPA: Determinação das Redes (Sub-Redes) e VLAN (Virtual-LAN) de Cada Grupo)

    !Criação da VLAN padrão de SVI do Grupo
    vlan ???
      !Nome da VLAN padrão
      name svig0???

    !Criação das VLANs dos Usuários do Grupo
    vlan ???
      name ???Primeiro_Nome_do_Primeiro_Aluno??? 
    vlan ???
      name ???Primeiro_Nome_do_Segundo_Aluno???
    vlan ???
      name ???Primeiro_Nome_do_Terceiro_Aluno???
    vlan ???
      name ???Primeiro_Nome_do_Quarto_Aluno???

    !Criação da VLAN da Rede Sem-Fio
    vlan ???
      name wifi
      exit

    !OBSERVAÇÃO IMPORTANTE: a Interface gigabitEthernet 0/1 não será usada nesse projeto (Interface Reservada).

    !Configurando a Interface de Acesso a VLAN do Primeiro Usuário
    interface gigabitEthernet 1/0/2

      !Configurando a Interface de Acesso a VLAN
      description Interface de Acesso da VLAN ??? do ???Nome_E_Sobrenome_Primeiro_Usuário???

      !Configurando o Modo de Acesso da Interface
      switchport mode access

      !Configurando o Acesso a VLAN
      switchport access vlan ???

      !Saindo da configuração da Interface
      exit

    !Configurando a Interface de Acesso a VLAN do Segundo Usuário
    interface gigabitEthernet 1/0/3
      description Interface de Acesso da VLAN ??? do ???Nome_E_Sobrenome_Segundo_Usuário???
      switchport mode access
      switchport access vlan ???
      exit

    !Configurando a Interface de Acesso a VLAN do Terceiro Usuário
    interface gigabitEthernet 1/0/4
      description Interface de Acesso da VLAN ??? do ???Nome_E_Sobrenome_Terceiro_Usuário???
      switchport mode access
      switchport access vlan ???
      exit

    !Configurando a Interface de Acesso a VLAN do Quarto Usuário
    interface gigabitEthernet 1/0/5
      description Interface de Acesso da VLAN ??? do ???Nome_E_Sobrenome_Quarto_Usuário???
      switchport mode access
      switchport access vlan ???
      exit

    !Configurando a Interface de Acesso a VLAN da Rede Sem-Fio (Wi-Fi/Wireless)
    !OBSERVAÇÃO IMPORTANTE: A interface fastEthernet 0/6 sempre será utilizada para a VLAN
    !da Rede Sem-Fio (Wi-Fi/Wireless) não alterar a porta.
    interface gigabitEthernet 1/0/6
      description Interface de Acesso da VLAN ???Wireless do Grupo-0???
      switchport mode access
      switchport access vlan ???
      exit

    !Desativando as Interfaces que não serão utilizadas no Switch Layer 3 3560 ou 9200
    interface range gigabitEthernet 1/0/7 - 23
      shutdown
      exit

    !Configurando a Interface de Trunk do Switch 3560 ou 9200 com o Router 2911 ou 8300
    interface gigabitEthernet 1/0/24
      description Interface de Trunk com o Router 2911 do Grupo-0???
      switchport trunk encapsulation dot1q
      switchport mode trunk
      exit
    
    !Habilitando o serviço de Roteamento do Switch Layer 3
    ip routing

    !Criando uma rota estática padrão para o gerenciamento remoto do Switch Layer 3
    !Utilizado para resolver o problema de acesso remoto do Switch entre VLANs
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 129 
    !(QUARTA ETAPA: Determinação dos Endereços de SVI (Switch Virtual Interface) e Gateway de cada Grupo)
    ip route 0.0.0.0 0.0.0.0 172.16.???.254
    end

  !Salvando as configurações
  copy running-config startup-config
```

## SEGUNDA ETAPA: Verificando as Configurações do Switch Cisco Catalyst 3560 e 9200

```python
!Visualizando as configurações
show running-config

!Visualizando as configurações de endereçamento IPv4
show ip interface brief

!Visualizando as informações de VLAN
show vlan brief

!Visualizando informações de uma VLAN utilizando o ID
show vlan id ???

!Visualizando informações de uma VLAN utilizando o Nome
show vlan name ???

!Visualizando as informações de Status das Interfaces
show interface status

!Visualizando informações de Interfaces Trunk
show interface trunk

!Visualizando informações detalhadas das Interfaces de Trunk
show interfaces gigabitEthernet 1/0/24 status
show interfaces gigabitEthernet 1/0/24 switchport

!Visualizando a tabela de roteamento local
show ip route

!Comandos para testar a conexão do Switch 3560 ou 9200L com o Router 2911 ou 8300L

!Pingando o endereço de SVI do Switch 3560 ou 9200L
ping 172.16.???.253

!Pingando o endereço de Gateway da Subinterface do Router 2911 ou 8300L
ping 172.16.???.254

!Acessando via SSH o Router 2911 ou 8300L a partir do Switch 3560 ou 9200L
!OBSERVAÇÃO: -l (éli não é o número "1" (um) e sim "l" (éli) em minúsculo)
ssh -l ???seu_usuário??? 172.16.???.254
```