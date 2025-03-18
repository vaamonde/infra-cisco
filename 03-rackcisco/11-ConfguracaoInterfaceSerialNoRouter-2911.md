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

**DCE (Data Circuit-Terminating Equipment):** Equipamento responsável por estabelecer, manter e encerrar a comunicação em um link de dados. Ele geralmente fornece a interface para conexão com a rede. Exemplos: modems, roteadores e CSU/DSU.

**DTE (Data Terminal Equipment):** Dispositivo terminal que se comunica através da rede. Ele gera ou recebe os dados, mas depende do DCE para transmissão. Exemplos: computadores, switches e roteadores (quando atuam como terminais).

**CSU (Channel Service Unit):** Dispositivo usado em conexões de telecomunicações para conectar redes locais (LANs) a redes de longa distância (WANs). Ele fornece funções como isolamento elétrico e regeneração do sinal.

**DSU (Data Service Unit):** Equipamento que converte os sinais digitais do DTE para um formato adequado para transmissão pela rede de telecomunicações. Muitas vezes, o CSU e o DSU estão combinados em um único dispositivo chamado CSU/DSU, usado em circuitos dedicados como T1/E1.

**T1 (Transmission System 1):** Origem: Estados Unidos, Velocidade: 1,544 Mbps, Canais: 24 canais de 64 Kbps cada (23 para voz/dados + 1 para sinalização), Uso: Amplamente utilizado na América do Norte e Japão para conexões telefônicas e de dados.

**E1 (European System 1):** Origem: Europa, Velocidade: 2,048 Mbps, Canais: 32 canais de 64 Kbps cada (30 para voz/dados + 2 para controle e sincronização), Uso: Mais comum na Europa, América Latina e outras partes do mundo.

## PRIMEIRA ETAPA: Configuração da Interface Serial no Router Cisco 2911

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Configuração da interface Serial0/0/0 DCE (Data Circuit-Terminating Equipment)
    interface serial 0/0/0

      !Descrição da Interface Serial DCE
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 232
      !(SÉTIMA ETAPA: Determinação da Interface Serial de WAN dos Grupos e seu Endereçamento IPv4)
      description Interface Serial do Grupo-??? para Grupo-???

      !Configuração do endereçamento IPv4
      !Verificar a tabela de endereçamento IP dos Grupos
      !Sempre vai ser o Endereço IPv4 IMPAR na Interface Serial 0/0/0
      ip address 192.168.1.??? 255.255.255.252

      !Configurando o Clock Rate (Velocidade do Link) para 2000000bps (2.0 Mbps)
      clock rate 2000000

      !Configurando a Largura de Banda (Dividir o Clock Rate por 1000 para achar o valor em Mbps)
      bandwidth 2000

      !Habilitando a interface Serial DCE
      no shutdown

      !Saindo das configurações da interface
      exit

    !Configuração da interface Serial0/0/1 DTE (Data Terminal Equipment)
    interface serial 0/0/1

      !Descrição da Interface Serial DTE
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 232
      !(SÉTIMA ETAPA: Determinação da Interface Serial de WAN dos Grupos e seu Endereçamento IPv4)
      description Interface Serial do Grupo-??? para Grupo-???

      !Configuração do endereçamento IP
      !Verificar a tabela de endereçamento IP dos Grupos
      !Sempre vai ser o Endereço IPv4 PAR na Interface Serial 0/0/1
      ip address 192.168.1.??? 255.255.255.252

      !Configurando a Largura de Banda (Dividir o Clock Rate por 1000 para achar o valor em Mbps)
      bandwidth 2000

      !Habilitando a interface Serial DTE
      no shutdown

      !Saindo das configurações da interface
      end

  !Salvando as configurações
  copy running-config startup-config

  !Visualizando as configurações
  show running-config

  !Visualizando as configurações de endereçamento IPv4
  show ip interface brief

  !Visualizando as informações de Roteamento
  show ip route

  !ROUTER VIZINHO-DCE <---> DTE-0/0/1_SEU_ROUTER_DCE-0/0/0 <---> DTE-ROUTER VIZINHO

  !Pingar a SUA Interface Serial 0/0/0 DCE (SEMPRE SERÁ O ENDEREÇO IPv4 PAR)
  ping 192.168.1.??? (serial 0/0/0)

  !Pingar a SUA Interface Serial 0/0/1 DTE (SEMPRE SERÁ O ENDEREÇO IPv4 IMPAR)
  ping 192.168.1.??? (serial 0/0/1)

  !Pingar a Interface Serial 0/0/1 do SEU VIZINHO DTE (SEMPRE SERÁ O ENDEREÇO IPv4 IMPAR)
  ping 192.168.1.??? (serial 0/0/1)

  !Pingar a Interface Serial 0/0/0 do SEU VIZINHO DCE (SEMPRE SERÁ O ENDEREÇO IPv4 PAR)
  ping 192.168.1.??? (serial 0/0/0)
```