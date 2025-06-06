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
Data de atualização: 06/06/2024<br>
Versão: 0.02<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## PRIMEIRA ETAPA: Instalação e Configuração do GNU/Linux Mint e Windows 10

**OBSERVAÇÃO: TODOS OS INTEGRANTES DOS GRUPOS DEVERÃO INSTALAR O LINUX MINT E O WINDOWS 10 UTILIZANDO O VIRTUALBOX NA UNIDADE DE DISCO CORRESPONDENTE PARA O ARMAZENAMENTO CORRETO DOS VHDs VIRTUAIS, PROCEDIMENTO SERÁ PASSADO EM SALA DE AULA**

**OBSERVAÇÃO IMPORTANTE:** Utilizar as máquinas virtuais do Linux Mint e Windows 10 no VirtualBOX, nesse cenário as máquinas virtuais estarão conectadas na Rede do Switch Cisco Catalyst 3560 e vai obter os endereços IPv4 fornecidos pelo Router Cisco 2911 via DHCP.

**OBSERVAÇÃO** Caso a Placa de Rede Off-Board não esteja funcionando, informar o docente para documentar e utilizar a Placa de Rede On-Board.

01. Alterar a Porta de Rede das Máquinas no VirtualBOX

```bash
A) LinuxMint
  Propriedades
    Rede
      Adaptador 1
        Conectado a: Placa em mode Bridge (Alterar)
        Nome: Realtek PCI GbE Family Controller (Alterar conforme necessidade)
  <OK>

B) Windows10
  Propriedades
    Rede
      Adaptador 1
        Conectado a: Placa em mode Bridge (Alterar)
        Nome: Realtek PCI GbE Family Controller (Alterar conforme necessidade)
  <OK>
```

02. Conectar o Cabo de Rede na Placa de Rede Off-Board do Desktop

```bash
A) Conectar o cabo de rede na placa de rede off-board;
B) Conectar o cabo de rede no ponto de rede do Rack Cisco da VLAN do seu usuário;
C) Verificar se os LEDs da Placa de Rede e do Switch estão ligados;
D) Desativar e Ativar novamente a Placa de Rede no Linux Mint.
```

03. Ligar as Máquinas Virtuais e verificar se obteve os endereços IPv4 via DHCP

```bash
A) Linux Mint
  Terminal: Ctrl + Alt + T 
    ifconfig   (verificar a linha: inet 172.16.???.??? VLAN da sua Sub-Rede)
    route -n   (verificar a linha: 0.0.0.0 172.16.???.254 VLAN da sua Sub-Rede)
    resolvectl (verificar a linha: Current DNS Server 8.8.8.8)

B) Windows 10
  Powershell
    ipconfig /all (verificar a linha: Endereço IPV4 172.16.???.??? VLAN da sua Sub-Rede)
    ipconfig /all (verificar a linha: Gateway Padrão 172.16.???.254 VLAN da sua Sub-Rede)
    ipconfig /all (verificar a linha: Servidores DNS 8.8.8.8)
```

04. Testar o ping no Router 2911 e do Switch 3560 no Linux e no Windows

```bash
Linux Mint ou Windows 10 
  ping 172.16.???.253 (VLAN da SVI do Switch)
  ping 172.16.???.254 (Gateway da VLAN do seu Usuário)
```

05. Testar os pings dos Desktops das VLAN's no Linux e no Windows

**OBSERVAÇÃO:** NO WINDOWS 10, POR PADRÃO O FIREWALL ESTÁ HABILITADO, RECOMENDO DESABILITAR O FIREWALL PARA TESTAR OS PINGS EM TODOS OS EQUIPAMENTOS PARA NÃO TER FALHAS DE CONEXÃO.

```bash
Linux Mint ou Windows 10 
  ping 172.16.???.???  (Pingar os Desktops Windows e Linux da sua VLANs)
  ping 172.16.???.???  (Pingar os Desktops Windows e Linux de outras VLANs)
```

06. Acessar remotamente o Switch Cisco Catalyst 3560 e Router Cisco 2911 utilizando o SSH

**OBSERVAÇÃO IMPORTANTE:** NOS SISTEMAS OPERACIONAIS GNU/LINUX MINT E NO WINDOWS 10, UTILIZANDO O TERMINAL OU POWERSHELL A CONEXÃO COM O SWITCH E ROUTER VIA COMANDO SSH PRECISA SER MODIFICADA DEVIDO AO ALGORÍTIMO DE CRIPTOGRAFIA DE SENHA DOS EQUIPAMENTOS DA CISCO UTILIZAR UM PADRÃO DIFERENTE, ESSE ERRO NÃO ACONTECE QUANDO VOCÊ UTILIZAR O SOFTWARE PUTTY (RECOMENDADO).

```bash
A) Linux Mint
  Terminal: Ctrl + Alt + T
    #Linha do SSH para acessar o Switch 3560
    #OBSERVAÇÃO IMPORTANTE: existe somente a Primeira Sub-Rede para acessar o Switch
    #opções do comando ssh: -oKexAlgorithms (Define os algoritmos de troca de chaves  Key Exchange Algorithms - Kex),
    #+diffie-hellman-group1-sha1 (é um algoritmo antigo e inseguro, + indica que esse algoritmo está sendo adicionado
    #aos padrões suportados), -oHostKeyAlgorithms (Define quais algoritmos podem ser usados para validar a chave do 
    #servidor), +ssh-rsa ( é um algoritmo baseado em SHA-1, + adiciona esse algoritmo à lista de suportados), -c (Define
    #o algoritmo de criptografia do canal de comunicação), aes256-cbc (AES (Advanced Encryption Standard) com uma 
    #chave de 256 bits - Modo de operação CBC (Cipher Block Chaining))
    ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostKeyAlgorithms=+ssh-rsa -c aes256-cbc seu_usuario@172.16.???.253

    #Linha do SSH para acessar o Router 2911
    #OBSERVAÇÃO IMPORTANTE: alterar a Sub-Rede para cada usuário a Rede
    ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostKeyAlgorithms=+ssh-rsa -c aes256-cbc seu_usuario@172.16.???.254

B) Windows 10
  Powershell
    #Linha do SSH para acessar o Switch 3560
    #OBSERVAÇÃO IMPORTANTE: existe somente a Primeira Sub-Rede para acessar o Switch
    ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostKeyAlgorithms=+ssh-rsa -c aes256-cbc seu_usuario@172.16.???.253

    #Linha do SSH para acessar o Router 2911
    #OBSERVAÇÃO IMPORTANTE: alterar a Sub-Rede para cada usuário a Rede
    ssh -oKexAlgorithms=+diffie-hellman-group1-sha1 -oHostKeyAlgorithms=+ssh-rsa -c aes256-cbc seu_usuario@172.16.???.254
```