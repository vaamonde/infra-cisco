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
Data de atualização: 27/03/2025<br>
Versão: 0.06<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

## PRIMEIRA ETAPA: Determinação da Rede Classful do Cenário B
```bash
A) Bloco de Rede Classful B fornecido: 172.16.0.0/16
B) Cenário B irá utilizar: 8 (oito) Sub-redes.
```

## SEGUNDA ETAPA: Cálculo de Sub-Redes do Cenário B:
```bash
OBSERVAÇÃO IMPORTANTE: NESSE CENÁRIO NÃO ESTÁ SENDO CONSIDERADO A QUANTIDADE DE HOSTS POR REDE,
SOMENTE A QUANTIDADE DE REDES PARA A CONFIGURAÇÃO DAS VLANS E ROTAS INTERNAS E EXTERNAS.

A) Trabalhar no 4 (quarto octeto) mudando o CIDR padrão de: /16 para: /24;

B) Necessidade de 8 (oito) Sub-Redes, utilizar 3 (três) Bits emprestado de hosts para esse cenário;
   Cálculo: 2 ^ 3 = 8 (Sub-Redes)

C) Quantidade Bits restantes de hosts: 5 total de Hosts por Sub-Rede: 2 ^ 5 = 32 - 2 = 30 (Hosts Válidos)

D) Variação das Sub-Redes: 32 - Novo CIDR: /27 - Nova Máscara de Rede: 255.255.255.224

E) Validação da Variação de Rede: 2 ^ 8 = 256, 256 - 224 = 32

F) Separação das Sub-Redes para os serviços do Cenário B:
   Rede-01) ID: 172.16.0.0    PIV: 172.16.0.1    UIP: 172.16.0.30   BROADCAST: 172.16.0.31   USO: RT-02 para SW-03
   Rede-02) ID: 172.16.0.32   PIV: 172.16.0.33   UIP: 172.16.0.62   BROADCAST: 172.16.0.63   USO: VLAN-50 Servidores
   Rede-03) ID: 172.16.0.64   PIV: 172.16.0.65   UIP: 172.16.0.94   BROADCAST: 172.16.0.95   USO: VLAN-60 Wireless
   Rede-04) ID: 172.16.0.96   PIV: 172.16.0.97   UIP: 172.16.0.126  BROADCAST: 172.16.0.127  USO: VLAN-99 SVI Switches
   Rede-05) ID: 172.16.0.128  PIV: 172.16.0.129  UIP: 172.16.0.158  BROADCAST: 172.16.0.159  USO: VLAN-10 Financeiro
   Rede-06) ID: 172.16.0.160  PIV: 172.16.0.161  UIP: 172.16.0.190  BROADCAST: 172.16.0.191  USO: VLAN-20 Estoque
   Rede-07) ID: 172.16.0.192  PIV: 172.16.0.193  UIP: 172.16.0.222  BROADCAST: 172.16.0.223  USO: VLAN-30 Faturamento
   Rede-08) ID: 172.16.0.224  PIV: 172.16.0.225  UIP: 172.16.0.254  BROADCAST: 172.16.0.255  USO: VLAN-40 Gerencia
```


## TERCEIRA ETAPA: Determinação das VLAN's para cada Serviço do Cenário B:
```bash
A) VLANs Switches Layer 3 e Layer 2
   VLAN-10: Financeiro     Name: FIN
   VLAN-20: Estoque        Name: EST
   VLAN-30: Faturamento    Name: FAT
   VLAN-40: Gerencia       Name: GER
   VLAN-50: Servidores     Name: Servers
   VLAN-60: Wireless       Name: Wireless
   VLAN-99: SVI Switches   Name: SVI-Switches
```

## QUARTA ETAPA: Determinação das Sub-Redes para cada Serviço do Cenário B:
```bash
  Rede-01) RT-02 para SW-03: 172.16.0.0/27
    Router rt-01: 172.16.0.30/27
    Switch sw-03: 172.16.0.29/27

  Rede-02) Servidores: 172.16.0.32/27
    Server server-02....: 172.16.0.33/27
    Server server-03....: 172.16.0.34/27
    Server server-04....: 172.16.0.35/27
    Server server-05....: 172.16.0.36/27
    Gateway SVI sw-03...: 172.16.0.62
    DNS Server server-02: 172.16.0.33

  Rede-03) Wireless (Wi-Fi - Sem-Fio): 172.16.0.64/27
    Gateway SVI sw-03...: 172.16.0.94
    DNS Server server-02: 172.16.0.33

  Rede-04) SVI Switches: 172.16.0.96/27
    SVI VLAN-99 sw-03.: 172.16.0.97/27
    SVI VLAN-99 sw-04.: 172.16.0.98/27
    SVI VLAN-99 sw-05.: 172.16.0.99/27
    Gateway SVI Switches Layer2: 172.16.0.97
    DNS Server server-02.......: 172.16.0.33

  Rede-05) VLAN-10 Financeiro (FIN): 172.16.0.128/27
    Gateway SVI VLAN-10 sw-03: 172.16.0.158
    DNS Server server-02.....: 172.16.0.33

  Rede-06) VLAN-20 Estoque (EST): 172.16.0.160/27
    Gateway SVI VLAN-10 sw-03: 172.16.0.190
    DNS Server server-02.....: 172.16.0.33

  Rede-07) VLAN-30 Faturamento (FAT): 172.16.0.192/27
    Gateway SVI VLAN-10 sw-03: 172.16.0.222
    DNS Server server-02.....: 172.16.0.33

  Rede-08) VLAN-40 Gerencia (GER): 172.16.0.224/27
    Gateway SVI VLAN-10 sw-03: 172.16.0.254
    DNS Server server-02.....: 172.16.0.33
```