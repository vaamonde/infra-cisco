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
Data de atualização: 12/06/2024<br>
Versão: 0.02<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## PRIMEIRA ETAPA: Configuração dos Routers e Access Point D-Link, TP-Link ou Linksys

01. Procedimento de Reset dos Routers e Access Point D-Link, TP-Link ou Linksys

Manual: https://www.dlink.com.br/wp-content/uploads/2018/10/DIR-809_A2_Manual_v1.00DI.pdf
```bash
Modelo: D-Link DIR-809
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Botão WPS/Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.0.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: Sem senha
```

Manual: https://www.dlink.com.br/wp-content/uploads/2018/10/DIR-819_A1_PPPoE.pdf
```bash
Modelo: D-Link DIR-819
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Botão WPS/Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.0.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: Sem senha
```

Manual: https://www.dlink.com.br/wp-content/uploads/2020/02/DIR-846_MANUAL_10072020_v1.03_EN.pdf
```bash
Modelo: D-Link DIR-846
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Botão WPS/Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.0.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: Sem senha
```

Manual: https://www.dlink.com.br/wp-content/uploads/2019/03/DIR-853_A2_WiFi.pdf
```bash
Modelo: D-Link DIR-853
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.0.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: Sem senha
```

Manual: https://static.tp-link.com/res/down/doc/TL-WR1043ND_V2_UG.pdf
```bash
Modelo: TP-Link TL-WR1043ND
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.1.1/24
    B) Usuário padrão.......: admin
    C) Senha padrão.........: admin
```

Manual: https://static.tp-link.com/upload/manual/2022/202206/20220621/1910013193_Archer%20AX3000%20Pro(US)1.0_UG_V1.pdf
```bash
Modelo: TP-Link AX3000
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.0.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: NECESSÁRIO CRIAR SENHA NO PRIMEIRO ACESSO
```

Manual: https://downloads.linksys.com/downloads/userguide/1224699372213/MAN_EA6900_8220_01617A00_Userguide_EN.pdf
```bash
Modelo: Linksys EA-6900 AC-1900
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.0.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: Sem senha
```

Manual: https://downloads.linksys.com/downloads/userguide/EA-Series_UG_Full_3425-00125D_EN_FR-CA_Web.pdf
```bash
Modelo: Linksys EA-4500 N900
01) Ligar o roteador e aguardar ele iniciar normalmente
02) Segurar o Reset por aproximadamente 15 segundos
03) Após soltar o botão, todos os LED´s devem piscar e os LED´s de Rede fica ligado e depois apaga.
    A) Endereço IPv4 padrão.: 192.168.1.1/24
    B) Usuário padrão.......: Sem usuário
    C) Senha padrão.........: Sem senha
```

**OBSERVAÇÃO:** ANTES DE CONECTAR NA REDE, FAÇA TODAS AS CONFIGURAÇÕES DO ROUTER ACCESS POINT D-LINK, TP-LINK OU LINKSYS FORA DA REDE, TESTAR E VERIFICA SE TUDO ESTÁ FUNCIONANDO, DEPOIS CONECTA NA SUA VLAN DA REDE SEM-FIO (WI-FI/WIRELESS).

**OBSERVAÇÃO IMPORTANTE:** DESATIVAR O SERVIÇO DE DHCP SERVER DO ROUTER ACCESS POINT D-LINK, TP-LINK OU LINKSYS, CONECTAR O CABO DE REDE NA PORTA 6 DO SEU SWITCH DIRETAMENTE NA PORTA DE SWITCH DO ROUTER ACCESS POINT D-LINK, TP-LINK OU LINKSYS, O ENDEREÇO IPv4 SERÁ FORNECIDO PELO ROUTER CISCO 2911.

02. Endereço IPv4 de cada Access Point para o Gerenciamento dos Grupos
```bash
A) Grupo-01   IPv4: 172.16.15.250 - Máscara: 255.255.255.0
B) Grupo-02   IPv4: 172.16.25.250 - Máscara: 255.255.255.0
C) Grupo-03   IPv4: 172.16.35.250 - Máscara: 255.255.255.0
D) Grupo-04   IPv4: 172.16.45.250 - Máscara: 255.255.255.0
E) Grupo-05   IPv4: 172.16.55.250 - Máscara: 255.255.255.0
F) Grupo-06   IPv4: 172.16.65.250 - Máscara: 255.255.255.0
```

03. Configuração das Redes Sem-Fio (cuidado com roteadores Dual Band 2.4Ghz e 5.0Ghz)
```bash
A) Grupo-01   SSID: G-01-2.4 e G-01-5.0 - Senha: ????
B) Grupo-02   SSID: G-02-2.4 e G-02-5.0 - Senha: ????
C) Grupo-03   SSID: G-03-2.4 e G-03-5.0 - Senha: ????
D) Grupo-04   SSID: G-04-2.4 e G-04-5.0 - Senha: ????
E) Grupo-05   SSID: G-05-2.4 e G-05-5.0 - Senha: ????
F) Grupo-06   SSID: G-06-2.4 e G-06-5.0 - Senha: ????
```

04. Configurações especificas da Rede Sem-Fio de 2.4Ghz (WiFi 4) e 5.0Ghz (WiFi 6)
```bash
A) Grupo-01: WiFi 4 (802.11n) 2.4Ghz Channel Width (MHz): 20MHz - Channel: 01 - Transmit Power: Medium - Security Protocol: WPA2 Personal
B) Grupo-02: WiFi 4 (802.11n) 2.4Ghz Channel Width (MHz): 20MHz - Channel: 06 - Transmit Power: Medium - Security Protocol: WPA2 Personal
C) Grupo-03: WiFi 4 (802.11n) 2.4Ghz Channel Width (MHz): 20MHz - Channel: 11 - Transmit Power: Medium - Security Protocol: WPA2 Personal
D) Grupo-04: WiFi 4 (802.11n) 2.4Ghz Channel Width (MHz): 20MHz - Channel: 01 - Transmit Power: Medium - Security Protocol: WPA2 Personal
E) Grupo-05: WiFi 4 (802.11n) 2.4Ghz Channel Width (MHz): 20MHz - Channel: 06 - Transmit Power: Medium - Security Protocol: WPA2 Personal
F) Grupo-06: WiFi 4 (802.11n) 2.4Ghz Channel Width (MHz): 20MHz - Channel: 11 - Transmit Power: Medium - Security Protocol: WPA2 Personal

A) Grupo-01: WiFi 6 (802.11ax) 5.0Ghz Channel Width (MHz): 40MHz - Channel: 038 - Transmit Power: High - Security Protocol: WPA2 Personal
B) Grupo-02: WiFi 6 (802.11ax) 5.0Ghz Channel Width (MHz): 40MHz - Channel: 046 - Transmit Power: High - Security Protocol: WPA2 Personal
C) Grupo-03: WiFi 6 (802.11ax) 5.0Ghz Channel Width (MHz): 40MHz - Channel: 151 - Transmit Power: High - Security Protocol: WPA2 Personal
D) Grupo-04: WiFi 6 (802.11ax) 5.0Ghz Channel Width (MHz): 40MHz - Channel: 159 - Transmit Power: High - Security Protocol: WPA2 Personal
E) Grupo-05: WiFi 6 (802.11ax) 5.0Ghz Channel Width (MHz): 40MHz - Channel: 038 - Transmit Power: High - Security Protocol: WPA2 Personal
F) Grupo-06: WiFi 6 (802.11ax) 5.0Ghz Channel Width (MHz): 40MHz - Channel: 046 - Transmit Power: High - Security Protocol: WPA2 Personal
```

05. Baixar os Softwares de Análise de Rede Sem-Fio no seu Smartphone

A) Unifi WiFiMan: https://play.google.com/store/apps/details?id=com.ubnt.usurvey&hl=pt_BR&gl=US<br>
B) SIMET Mobile: https://play.google.com/store/apps/details?id=br.ceptro.simet.client.android&hl=pt_BR&gl=US<br>

06. Sites On-Line para Testar a Velocidade da Internet no seu Computador

A) SIMET (Nic.br): https://beta.simet.nic.br/<br>
B) SpeedTest: https://www.speedtest.net/<br>
C) Fast (Netflix): https://fast.com/pt/<br>
D) MLab: https://speed.measurementlab.net/#/<br>
E) NPerf: https://www.nperf.com/pt/<br>
