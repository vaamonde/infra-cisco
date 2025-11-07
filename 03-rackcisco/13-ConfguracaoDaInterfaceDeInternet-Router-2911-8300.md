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
Data de atualização: 05/10/2025<br>
Versão: 0.02<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560, SW-9200L, RT-2911 e RT-8200L

## PRIMEIRA ETAPA: Configuração da Interface de Internet no Router Cisco 2911 ou 8300

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Configuração da interface GigabitEthernet 0/1 para acesso a Internet
    interface gigabitEthernet 0/0/1

      !Descrição da Interface GigabitEthernet 0/0/1
      description Interface de acesso a Internet do Grupo-0???

      !Configuração do endereçamento IPv4 Dinâmico via DHCP Client
      ip address dhcp

      !Inicializando a Interface
      no shutdown

      !Saindo das configurações da interface
      end

  !Salvando as configurações
  copy running-config startup-config

  !Visualizando as configurações
  show running-config

  !Visualizando as configurações de endereçamento IPv4
  show ip interface brief

  !Visualizando as informações de Roteamento (Rota Padrão: 0.0.0.0 0.0.0.0 e Gateway Padrão)
  show ip route

  !Pingar os servidores do SENAC Tatuapé no Router
  ping 10.26.40.190
  ping 10.26.40.191

  !Pingar o Endereço IPv4 do Google no Router
  ping 8.8.8.8

  !Traçar as Rotas para os Servidores do SENAC Tatuapé no Router
  traceroute 10.26.40.190
  traceroute 10.26.40.191

  !Traçar as Rotas para os Servidores do Google no Router
  traceroute 8.8.8.8
```

## PRIMEIRA ETAPA: Testando as conexões com a Internet nos Desktops Windows e Linux Mint

```python
!Nos Desktops Linux Mint ou Windows 10 deverá pingar e traçar as rotas via DNS
ping 8.8.8.8
ping google.com
traceroute -n google.com (Linux Mint)
tracepath -n google.com  (Linux Mint)
tracert -n google.com    (Windows 10)
```