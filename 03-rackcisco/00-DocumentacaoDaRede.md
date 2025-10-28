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
Data de atualização: 24/10/2024<br>
Versão: 0.02<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560, SW-9200L, RT-2911 e RT-8200L

## PRIMEIRA ETAPA: Documentação dos Pontos de Rede do Rack Cisco.

01. Todos os pontos de Rede do Rack Cisco estão identificados pela sigla: **R.Cisco - Ponto 0x.**

02. Todos os pontos de Rede do Rack Cisco estão conectados nos: **2 (dois) primeiros Patch Panel.**
```bash
A) Primeiro Patch Panel: Pontos de Rede de: 01 até 24;
B) Segundo Patch Panel.: Pontos de Rede de: 25 até 30.
```
03. Todos os Patch Cords do Rack Cisco estão identificados pela sigla: **R.Cisco - Ponto 0x.** e Etiqueta na Cor **VERDE**

04. No Rack Cisco existe: **2 (dois) Patch Panel** que serão utilizados para o *Espelhamento das Portas dos Switches Cisco Catalyst Layer-3 3560.*

**OBSERVAÇÃO IMPORTANTE: UTILIZAR O FLUKE DTX-1800 PARA CERTIFICAR TODOS OS PONTOS DE REDE DO MV8 (KEYSTONE) LOCALIZADOS DEBAIXO DAS MESAS OU NAS CANALETAS APARENTES NAS JANELAS ATÉ O PATCH PANEL NO RACK CISCO.**

O Fluke DTX-1800 é um certificador de cabos de rede utilizado para testar a infraestrutura de cabeamento estruturado. Ele fornece diversos parâmetros que ajudam a avaliar a qualidade e conformidade dos cabos com os padrões de transmissão de dados. 

A) **Malha Elétrica (Wiremap)**: Refere-se à continuidade do fio de aterramento no cabo. Esse teste verifica se há uma conexão adequada entre os condutores de aterramento e detecta possíveis problemas, como fios quebrados ou conexões soltas.

B) **Resistência (Resistance/Impedance)**: Mede a resistência elétrica dos condutores do cabo, geralmente expressa em ohms (Ω). Uma resistência elevada pode indicar fios muito finos, conexões ruins ou cabos de baixa qualidade.

C) **Comprimento (Length)**: Indica o comprimento total do cabo testado, geralmente medido em metros (m). Esse valor é obtido por meio da medição do tempo de propagação do sinal elétrico pelo cabo.

D) **Retardo de Propagação (Propagation Delay)**: Representa o tempo que um sinal leva para percorrer um determinado comprimento do cabo, medido em nanossegundos (ns). Esse parâmetro é importante para sincronizar os sinais transmitidos.

E) **Desvio de Retardo (Delay Skew)**: Mede a diferença entre o tempo de propagação do par mais rápido e o do par mais lento dentro de um cabo de par trançado, expresso em nanossegundos (ns). Um alto desvio de retardo pode causar distorções na transmissão de dados, afetando o desempenho da rede.

F) **Perda de Inserção (Insertion Loss ou Attenuation)**: Refere-se à quantidade de sinal que se perde ao longo do comprimento do cabo, expressa em decibéis (dB). Uma atenuação excessiva pode prejudicar a comunicação, especialmente em cabos longos.

G) **NEXT (Near-End Crosstalk - Diafonia Próxima)**: Indica o nível de interferência de um par de fios sobre outro dentro do cabo, medido na extremidade mais próxima. O crosstalk (diafonia) ocorre devido ao acoplamento eletromagnético entre os pares trançados.

H) **PS NEXT (Power Sum Near-End Crosstalk)**: É uma variação do NEXT, mas considerando o impacto combinado de todos os outros pares de fios sobre um par específico. Isso é crucial em redes de alta velocidade, como Gigabit Ethernet.

I) **ACR-F (Attenuation to Crosstalk Ratio - Far-End)**: Compara a atenuação com o crosstalk no extremo mais distante do cabo (far-end). Um valor alto indica uma boa separação entre os sinais, reduzindo interferências.

J) **PS ACR-F (Power Sum ACR-F)**: Assim como o PS NEXT, essa medida considera o efeito cumulativo da interferência de todos os pares de fios sobre um único par, mas no extremo mais distante do cabo.

L) **ACR-N (Attenuation to Crosstalk Ratio - Near-End)**: É a relação entre a atenuação e o NEXT. Um valor positivo indica que o sinal útil é mais forte do que a interferência, garantindo melhor qualidade de transmissão.

K) **PS ACR-N (Power Sum ACR-N)**: Similar ao ACR-N, mas considera a soma da interferência de todos os pares sobre um par específico na extremidade mais próxima do cabo.

M) **Perda de Retorno (Return Loss)**: Mede a quantidade de sinal que é refletida de volta devido a irregularidades no cabo, conexões ruins ou problemas na terminação. Valores altos de perda de retorno podem indicar má qualidade no cabeamento.

N) **Analisador HDTDX (High-Definition Time Domain Crosstalk)**: Este teste mede a interferência entre pares de cabos, conhecida como diafonia (crosstalk). O HDTDX identifica exatamente onde ao longo do cabo ocorre a interferência de sinal.

O) **Analisador HDTDR (High-Definition Time Domain Reflectometry)**: Este teste mede a reflexão do sinal, identificando descontinuidades ou variações de impedância ao longo do cabo. O HDTDR ajuda a detectar problemas como cabo rompido, excesso de curvatura, conectores mal inseridos ou diferenças de impedância devido a emendas.

P) **NVP (Nominal Velocity of Propagation)**: O NVP (Velocidade Nominal de Propagação) é um percentual que indica a velocidade com que o sinal viaja através do cabo em relação à velocidade da luz no vácuo. No seu caso, NVP 69,0 significa que o sinal viaja a 69% da velocidade da luz. Cabos Furukawa SOHO Plus Cat5e: 68% e Cabos Furukawa SOHO (Small Office/Home Office)) Plus Cat6.: 68%.

05. Os Kits do Rack Cisco serão divididos em: **6 (seis) Grupos:**
```bash
A) Grupo-01: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911
B) Grupo-02: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911
C) Grupo-03: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911
D) Grupo-04: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911
E) Grupo-05: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911
F) Grupo-06: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911
```
**NOVOS KITS DO RACK CISCO:** EM 2025 FOI ATUALIZADO O RACK CISCO COM OS SEGUINTES KITS:
```bash
A) Grupo-01: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911 (FILIAL 01)
B) Grupo-02: 1 (um) Switch Cisco Catalyst Multilayer 9200L e 1 (um) Router Cisco Edge 8300L
C) Grupo-03: 1 (um) Switch Cisco Catalyst Multilayer 9200L  e 1 (um) Router Cisco Edge 8300L
D) Grupo-04: 1 (um) Switch Cisco Catalyst Multilayer 9200L  e 1 (um) Router Cisco Edge 8300L
E) Grupo-05: 1 (um) Switch Cisco Catalyst Multilayer 9200L  e 1 (um) Router Cisco Edge 8300L
F) Grupo-06: 1 (um) Switch Cisco Catalyst Layer-3 3560 e 1 (um) Router Cisco 2911 (FILIAL 02)
```

06. Cada Grupo deverá ser composto no máximo de: **4 (quatro) integrantes**, cada integrante do grupo vai utilizar seu Ponto de Rede e deverá sobrar: **1 (um) ponto de rede** para o *Roteador Sem-Fio.*

7. Cada Integrante do Grupo terá as seguintes funções:
```bash
A) 1 (um) Integrante Responsável pelo Cabeamento Estruturado (CABLING);
B) 1 (um) Integrante Responsável pelo Switch Cisco Catalyst 3560 (SWITCHING);
C) 1 (um) Integrante Responsável pelo Router Cisco 2911 (ROUTING);
D) 1 (um) Integrante Responsável pelo Link WAN, Internet e Documentação (DOCS);
E) TODOS OS INTEGRANTES SERÃO RESPONSÁVEIS PELOS DESKTOPS LINUX MINT 22.2 E WINDOWS 10 ou 11.
```
**OBSERVAÇÃO IMPORTANTE: Os equipamentos abaixo serão utilizados pelo Docente em aula.**
```bash
PROFESSOR: 1 (um) Router Cisco 4321 e 1 (um) Switch Catalyst Multilayer 2960-XR
ESSES EQUIPAMENTOS VÃO FAZER A FUNÇÃO DE SIMULAÇÃO DO ISP (INTERNET SERVICE PROVIDER).
```

## SEGUNDA ETAPA: Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo.

01. Nos scripts de configuração Base do Switch e Router existe as linhas de configuração dos usuários e senhas conforme abaixo:
```bash
A) Senha padrão: 123@Tatuape
B) Usuário: seguir o padrão da documentação dos scripts alterando o seu valor dentro de ???__ __???.
   Exemplo: username ???nome_do_primeiro_integrante??? privilege 15 secret ????
            username vaamonde privilege 15 secret 123@Tatuape
C) Domínio padrão: senac.br
```
**OBSERVAÇÃO IMPORTANTE: sempre que aparecer o carácter: ? (interrogação), você deverá retirar o carácter e alterar o seu valor, o uso de ? (interrogação) não é permitido nas configurações do Cisco IOS.**

02. Nos scripts do Switch e Router você precisa prestar muita atenção nas linhas de configuração abaixo, essas linhas precisam ser alteradas seu valor antes de executar o comando no Switch ou Router.
```bash
Exemplo:
  clock set      (configuração da data e hora)
  hostname       (configuração do nome do equipamento)
  enable secret  (habilitando a senha do modo Exec Privilegiado)
  username       (criação dos usuários)
  password       (configuração da senha de acesso)
  ip address     (endereçamento IPv4)
  ip domain-name (nome do domínio do roteador)
```
03. Nome dos Switches, Routers e Access Point de Cada Grupo:
```bash
A) Grupo-01:   Hostname Switch 3560: sw-g01   Hostname Router 2911: rt-g01   Access Point: ap-g01
B) Grupo-02:   Hostname Switch 3560: sw-g02   Hostname Router 2911: rt-g02   Access Point: ap-g02
C) Grupo-03:   Hostname Switch 3560: sw-g03   Hostname Router 2911: rt-g03   Access Point: ap-g03
E) Grupo-04:   Hostname Switch 3560: sw-g04   Hostname Router 2911: rt-g04   Access Point: ap-g04
F) Grupo-05:   Hostname Switch 3560: sw-g05   Hostname Router 2911: rt-g05   Access Point: ap-g05
G) Grupo-06:   Hostname Switch 3560: sw-g06   Hostname Router 2911: rt-g06   Access Point: ap-g06
```

## TERCEIRA ETAPA: Determinação das Redes (Sub-Redes) e VLAN (Virtual-LAN) de Cada Grupo

01. Todo o cenário será configurado utilizando VLAN (Virtual-LAN), será determinado 6 (seis) VLAN's por Grupo, sendo elas
```bash
A) 01 (uma)    VLAN de SVI (Switch Virtual Interface - Gerenciamento da Switch 3560)
B) 04 (quatro) VLANs para cada usuário na rede (4 integrantes do grupo - Desktops)
C) 01 (uma)    VLAN de Rede Sem-Fio (Wi-Fi/Wireless)
```
02. Determinação das Sub-Redes e VLAN de cada Grupo.
```bash
A) Grupo-01: Subredes:   172.16.10.0/24   VLAN:  10  -  utilizada no SVI do Switch Layer 3
             Subredes:   172.16.11.0/24   VLAN:  11  -  utilizada pelo primeiro usuário da rede
             Subredes:   172.16.12.0/24   VLAN:  12  -  utilizada pelo segundo usuário da rede
             Subredes:   172.16.13.0/24   VLAN:  13  -  utilizada pelo terceiro usuário da rede
             Subredes:   172.16.14.0/24   VLAN:  14  -  utilizada pelo quarto usuário da rede
             Subredes:   172.16.15.0/24   VLAN:  15  -  utilizada pela rede sem-fio

B) Grupo-02: Subredes:   172.16.20.0/24   VLAN:  20  -  utilizada no SVI do Switch Layer 3
             Subredes:   172.16.21.0/24   VLAN:  21  -  utilizada pelo primeiro usuário da rede
             Subredes:   172.16.22.0/24   VLAN:  22  -  utilizada pelo segundo usuário da rede
             Subredes:   172.16.23.0/24   VLAN:  23  -  utilizada pelo terceiro usuário da rede
             Subredes:   172.16.24.0/24   VLAN:  24  -  utilizada pelo quarto usuário da rede
             Subredes:   172.16.25.0/24   VLAN:  25  -  utilizada pela rede sem-fio

C) Grupo-03: Subredes:   172.16.30.0/24   VLAN:  30  -  utilizada no SVI do Switch Layer 3
             Subredes:   172.16.31.0/24   VLAN:  31  -  utilizada pelo primeiro usuário da rede
             Subredes:   172.16.32.0/24   VLAN:  32  -  utilizada pelo segundo usuário da rede
             Subredes:   172.16.33.0/24   VLAN:  33  -  utilizada pelo terceiro usuário da rede
             Subredes:   172.16.34.0/24   VLAN:  34  -  utilizada pelo quarto usuário da rede
             Subredes:   172.16.35.0/24   VLAN:  35  -  utilizada pela rede sem-fio

D) Grupo-04: Subredes:   172.16.40.0/24   VLAN:  40  -  utilizada no SVI do Switch Layer 3
             Subredes:   172.16.41.0/24   VLAN:  41  -  utilizada pelo primeiro usuário da rede
             Subredes:   172.16.42.0/24   VLAN:  42  -  utilizada pelo segundo usuário da rede
             Subredes:   172.16.43.0/24   VLAN:  43  -  utilizada pelo terceiro usuário da rede
             Subredes:   172.16.44.0/24   VLAN:  44  -  utilizada pelo quarto usuário da rede
             Subredes:   172.16.45.0/24   VLAN:  45  -  utilizada pela rede sem-fio

E) Grupo-05: Subredes:   172.16.50.0/24   VLAN:  50  -  utilizada no SVI do Switch Layer 3
             Subredes:   172.16.51.0/24   VLAN:  51  -  utilizada pelo primeiro usuário da rede
             Subredes:   172.16.52.0/24   VLAN:  52  -  utilizada pelo segundo usuário da rede
             Subredes:   172.16.53.0/24   VLAN:  53  -  utilizada pelo terceiro usuário da rede
             Subredes:   172.16.54.0/24   VLAN:  54  -  utilizada pelo quarto usuário da rede
             Subredes:   172.16.55.0/24   VLAN:  55  -  utilizada pela rede sem-fio

F) Grupo-06: Subredes:   172.16.60.0/24   VLAN:  60  -  utilizada no SVI do Switch Layer 3
             Subredes:   172.16.61.0/24   VLAN:  61  -  utilizada pelo primeiro usuário da rede
             Subredes:   172.16.62.0/24   VLAN:  62  -  utilizada pelo segundo usuário da rede
             Subredes:   172.16.63.0/24   VLAN:  63  -  utilizada pelo terceiro usuário da rede
             Subredes:   172.16.64.0/24   VLAN:  64  -  utilizada pelo quarto usuário da rede
             Subredes:   172.16.65.0/24   VLAN:  65  -  utilizada pela rede sem-fio
```

## QUARTA ETAPA: Determinação dos Endereços de SVI (Switch Virtual Interface) e Gateway de cada Grupo

01. Determinação do endereço IPv4 da VLAN de SVI e Gateway do Switch Layer 3
```bash
A) Grupo-01:  SVI Switch 3560:  172.16.10.253/24  -  Gateway: 172.16.10.254 (Interface Virtual Router 2911)
B) Grupo-02:  SVI Switch 3560:  172.16.20.253/24  -  Gateway: 172.16.20.254 (Interface Virtual Router 2911)
C) Grupo-03:  SVI Switch 3560:  172.16.30.253/24  -  Gateway: 172.16.30.254 (Interface Virtual Router 2911)
D) Grupo-04:  SVI Switch 3560:  172.16.40.253/24  -  Gateway: 172.16.40.254 (Interface Virtual Router 2911)
E) Grupo-05:  SVI Switch 3560:  172.16.50.253/24  -  Gateway: 172.16.50.254 (Interface Virtual Router 2911)
F) Grupo-06:  SVI Switch 3560:  172.16.60.253/24  -  Gateway: 172.16.60.254 (Interface Virtual Router 2911)
```

## QUINTA ETAPA: Determinação das Portas de Rede de cada VLAN dos Usuários dos Grupos

**OBSERVAÇÃO IMPORTANTE:** a Porta de Rede: FastEthernet 0/1 não será utilizada nas configurações.

**OBSERVAÇÃO IMPORTANTE:** a Porta de Rede: FastEthernet 0/24 será o Trunk entre o Switch 3560 e o Router 2911.

**OBSERVAÇÃO IMPORTANTE:** O nome da VLAN deverá ser o **Primeiro Nome dos Alunos do Grupo**, exemplo: *Robson Vaamonde - nome da VLAN 11: robson (sempre em minúsculo), Leandro Ramos - nome da VLAN 12: leandro, etc...*

**OBSERVAÇÃO:** CASO O GRUPO NÃO TENHA: *04 (QUATRO) ALUNOS*, DESCONSIDERAR A CRIAÇÃO DAS VLAN'S CORRESPONDENTE, EXEMPLO: *GRUPO COM 3 (TRÊS) ALUNOS DESCONSIDERAR A QUARTA VLAN DO GRUPO MAIS MANTER A VLAN DA REDE SEM-FIO COM O SEU NÚMERO E NOME*.

01. Determinação das Portas de Rede das VLANs do Switch 3560
```bash
A) Grupo-01: Porta: 2    VLAN: 11    Nome: ??Primeiro_Nome_do_Primeiro_Aluno??
             Porta: 3    VLAN: 12    Nome: ??Primeiro_Nome_do_Segundo_Aluno??
             Porta: 4    VLAN: 13    Nome: ??Primeiro_Nome_do_Terceiro_Aluno??
             Porta: 5    VLAN: 14    Nome: ??Primeiro_Nome_do_Quarto_Aluno??
             Porta: 6    VLAN: 15    Nome: wifi01

B) Grupo-02: Porta: 2    VLAN: 21    Nome: ??Primeiro_Nome_do_Primeiro_Aluno??
             Porta: 3    VLAN: 22    Nome: ??Primeiro_Nome_do_Segundo_Aluno??
             Porta: 4    VLAN: 23    Nome: ??Primeiro_Nome_do_Terceiro_Aluno??
             Porta: 5    VLAN: 24    Nome: ??Primeiro_Nome_do_Quarto_Aluno??
             Porta: 6    VLAN: 25    Nome: wifi02

C) Grupo-03: Porta: 2    VLAN: 31    Nome: ??Primeiro_Nome_do_Primeiro_Aluno??
             Porta: 3    VLAN: 32    Nome: ??Primeiro_Nome_do_Segundo_Aluno??
             Porta: 4    VLAN: 33    Nome: ??Primeiro_Nome_do_Terceiro_Aluno??
             Porta: 5    VLAN: 34    Nome: ??Primeiro_Nome_do_Quarto_Aluno??
             Porta: 6    VLAN: 35    Nome: wifi03

D) Grupo-04: Porta: 2    VLAN: 41    Nome: ??Primeiro_Nome_do_Primeiro_Aluno??
             Porta: 3    VLAN: 42    Nome: ??Primeiro_Nome_do_Segundo_Aluno??
             Porta: 4    VLAN: 43    Nome: ??Primeiro_Nome_do_Terceiro_Aluno??
             Porta: 5    VLAN: 44    Nome: ??Primeiro_Nome_do_Quarto_Aluno??
             Porta: 6    VLAN: 45    Nome: wifi04

E) Grupo-05: Porta: 2    VLAN: 51    Nome: ??Primeiro_Nome_do_Primeiro_Aluno??
             Porta: 3    VLAN: 52    Nome: ??Primeiro_Nome_do_Segundo_Aluno??
             Porta: 4    VLAN: 53    Nome: ??Primeiro_Nome_do_Terceiro_Aluno??
             Porta: 5    VLAN: 54    Nome: ??Primeiro_Nome_do_Quarto_Aluno??
             Porta: 6    VLAN: 55    Nome: wifi05

F) Grupo-06: Porta: 2    VLAN: 61    Nome: ??Primeiro_Nome_do_Primeiro_Aluno??
             Porta: 3    VLAN: 62    Nome: ??Primeiro_Nome_do_Segundo_Aluno??
             Porta: 4    VLAN: 63    Nome: ??Primeiro_Nome_do_Terceiro_Aluno??
             Porta: 5    VLAN: 64    Nome: ??Primeiro_Nome_do_Quarto_Aluno??
             Porta: 6    VLAN: 65    Nome: wifi06
```

## SEXTA ETAPA: Determinação das Sub-Interfaces de Gateway de cada VLAN dos Grupos

01. Determinação do endereço IPv4 de Gateway do Router 2911 utilizadas para Rotear as VLAN's
```bash
A) Grupo-01: Subinterface: 10    IPv4: 172.16.10.254/24
             Subinterface: 11    IPv4: 172.16.11.254/24
             Subinterface: 12    IPv4: 172.16.12.254/24
             Subinterface: 13    IPv4: 172.16.13.254/24
             Subinterface: 14    IPv4: 172.16.14.254/24
             Subinterface: 15    IPv4: 172.16.15.254/24

B) Grupo-02: Subinterface: 20    IPv4: 172.16.20.254/24
             Subinterface: 21    IPv4: 172.16.21.254/24
             Subinterface: 22    IPv4: 172.16.22.254/24
             Subinterface: 23    IPv4: 172.16.23.254/24
             Subinterface: 24    IPv4: 172.16.24.254/24
             Subinterface: 25    IPv4: 172.16.25.254/24

C) Grupo-03: Subinterface: 30    IPv4: 172.16.30.254/24
             Subinterface: 31    IPv4: 172.16.31.254/24
             Subinterface: 32    IPv4: 172.16.32.254/24
             Subinterface: 33    IPv4: 172.16.33.254/24
             Subinterface: 34    IPv4: 172.16.34.254/24
             Subinterface: 35    IPv4: 172.16.35.254/24

D) Grupo-04: Subinterface: 40    IPv4: 172.16.40.254/24
             Subinterface: 41    IPv4: 172.16.41.254/24
             Subinterface: 42    IPv4: 172.16.42.254/24
             Subinterface: 43    IPv4: 172.16.43.254/24
             Subinterface: 44    IPv4: 172.16.44.254/24
             Subinterface: 45    IPv4: 172.16.45.254/24

E) Grupo-05: Subinterface: 50    IPv4: 172.16.50.254/24
             Subinterface: 51    IPv4: 172.16.51.254/24
             Subinterface: 52    IPv4: 172.16.52.254/24
             Subinterface: 53    IPv4: 172.16.53.254/24
             Subinterface: 54    IPv4: 172.16.54.254/24
             Subinterface: 55    IPv4: 172.16.55.254/24

F) Grupo-06: Subinterface: 60    IPv4: 172.16.60.254/24
             Subinterface: 61    IPv4: 172.16.61.254/24
             Subinterface: 62    IPv4: 172.16.62.254/24
             Subinterface: 63    IPv4: 172.16.63.254/24
             Subinterface: 64    IPv4: 172.16.64.254/24
             Subinterface: 65    IPv4: 172.16.65.254/24
```

## SÉTIMA ETAPA: Determinação da Interface Serial de WAN dos Grupos e seu Endereçamento IPv4

**OBSERVAÇÃO IMPORTANTE:** a rede Classfull *Classe C: 192.168.1.0/24* será segmentada em: *64 Sub-Redes*.

**Bits de Rede: 2^6=64 - Bits de Host: 2^2=4-2(ID e Broadcast)=2 - Máscara: 255.255.255.252**

**PRESTE MUITA ATENÇÃO DA TABELA DE ALOCAÇÃO DE ENDEREÇAMENTO IPV4 PARA CADA GRUPO, EXEMPLO: O GRUPO 01 VAI SE CONECTAR COM OS GRUPOS 02 E 06, VOCÊ DEVERÁ MAPEAR OS ENDEREÇOS UTILIZADOS NAS INTERFACES SERIAIS 0/0/0 E 0/0/1 ANALISANDO SEMPRE A CONEXÃO COM O SEUS VIZINHOS E QUAL REDE ELA PERTENCE.**

**EXEMPLO:** ROUTER VIZINHO-DCE <-------> DTE-0/0/1_SEU ROUTER_DCE-0/0/0 <-------> DTE-ROUTER VIZINHO

**DICA: NESSA ETAPA VOCÊS PRECISAM CONVERSAR COM OS OUTROS GRUPOS, NÃO ADIANTA VOCÊ FAZER A SUA PARTE SE O OUTRO GRUPO NÃO FAZER A DELE E SE OS DOIS ERRAREM TUDO ESTARÁ ERRADO, TODOS OS GRUPOS DEPENDEM DESSA CONFIGURAÇÃO PARA FUNCIONAR.**

Endereçamento IP para Rede de Interligação (WAN) - (GP=Grupo | PI=Primeiro IP | UP=Último IP)<br>
Interface Serial 0/0/0 e Serial 0/0/1 - Rede Classfull C: 192.168.1.0/24 - 255.255.255.0 - Segmentada em: 64 Sub-Redes.
```bash
A) Grupo-01:  Rede: 192.168.1.0    PI: 192.168.1.1 - UP: 192.168.1.2    Broadcast: 192.168.1.3
   Grupo-01:  Serial0/0/0 IP: 192.168.1.1/30 --> Grupo-02 Serial0/0/1 IP: 192.168.1.2/30

B) Grupo-02:  Rede: 192.168.1.4    PI: 192.168.1.5 - UP: 192.168.1.6    Broadcast: 192.168.1.7
   Grupo-02:  Serial0/0/0 IP: 192.168.1.5/30 --> Grupo-03 Serial0/0/1 IP: 192.168.1.6/30

C) Grupo-03:  Rede: 192.168.1.8    PI: 192.168.1.9 - UP: 192.168.1.10   Broadcast: 192.168.1.11
   Grupo-03:  Serial0/0/0 IP: 192.168.1.9/30 --> Grupo-04 Serial0/0/1 IP: 192.168.1.10/30

D) Grupo-04:  Rede: 192.168.1.12   PI: 192.168.1.13 - UP: 192.168.1.14  Broadcast: 192.168.1.15
   Grupo-04:  Serial0/0/0 IP: 192.168.1.13/30 --> Grupo-05 Serial0/0/1 IP: 192.168.1.14/30

E) Grupo-05:  Rede: 192.168.1.16   PI: 192.168.1.17 - UP: 192.168.1.18  Broadcast: 192.168.1.19
   Grupo-05:  Serial0/0/0 IP: 192.168.1.17/30 --> Grupo-06 Serial0/0/1 IP: 192.168.1.18/30

F) Grupo-06:  Rede: 192.168.1.20   PI: 192.168.1.21 - UP: 192.168.1.22  Broadcast: 192.168.1.23
   Grupo-06:  Serial0/0/0 IP: 192.168.1.21/30 --> Grupo-01 Serial0/0/1 IP: 192.168.1.22/30
```

## OITAVA ETAPA: Determinação da Interface do Switch do Professor para a Conexão com a Internet
```bash
A) Grupo-01 - Porta do Switch: 01   (VLAN: 501 - Rede: 200.200.200.0/27)
B) Grupo-02 - Porta do Switch: 02   (VLAN: 502 - Rede: 200.200.200.32/27)
C) Grupo-03 - Porta do Switch: 03   (VLAN: 503 - Rede: 200.200.200.64/27)
D) Grupo-04 - Porta do Switch: 04   (VLAN: 504 - Rede: 200.200.200.96/27)
E) Grupo-05 - Porta do Switch: 05   (VLAN: 505 - Rede: 200.200.200.128/27)
F) Grupo-06 - Porta do Switch: 06   (VLAN: 506 - Rede: 200.200.200.160/27)
```

## NOVA ETAPA: Determinação das Configurações do Protocolo de Roteamento Dinâmico OSPF

01. Configuração do OSPF e Endereçamento IPv4 da Interface de Loopback 0 dos Grupos
```bash
A) Grupo-01   Endereço IPv4 Loopback: 1.1.1.1 255.255.255.255 (Máscara /32 RFC-3021 host subnet)
B) Grupo-02   Endereço IPv4 Loopback: 2.2.2.2 255.255.255.255 (Máscara /32 RFC-3021 host subnet)
C) Grupo-03   Endereço IPv4 Loopback: 3.3.3.3 255.255.255.255 (Máscara /32 RFC-3021 host subnet)
D) Grupo-04   Endereço IPv4 Loopback: 4.4.4.4 255.255.255.255 (Máscara /32 RFC-3021 host subnet)
E) Grupo-05   Endereço IPv4 Loopback: 5.5.5.5 255.255.255.255 (Máscara /32 RFC-3021 host subnet)
F) Grupo-06   Endereço IPv4 Loopback: 6.6.6.6 255.255.255.255 (Máscara /32 RFC-3021 host subnet)
```

02. Configuração do ID Local do Processo do OSPF dos Grupos
```bash
A) Grupo-01   ID do Processo: 1
B) Grupo-02   ID do Processo: 2
C) Grupo-03   ID do Processo: 3
D) Grupo-04   ID do Processo: 4
E) Grupo-05   ID do Processo: 5
F) Grupo-06   ID do Processo: 6
```

03. Configuração do Router-ID do Processo do OSPF (Loopback) dos Grupos
```bash
A) Grupo-01   Router ID: 1.1.1.1   (mesmo endereço IPv4 da Loopback)
B) Grupo-02   Router ID: 2.2.2.2   (mesmo endereço IPv4 da Loopback)
C) Grupo-03   Router ID: 3.3.3.3   (mesmo endereço IPv4 da Loopback)
D) Grupo-04   Router ID: 4.4.4.4   (mesmo endereço IPv4 da Loopback)
E) Grupo-05   Router ID: 5.5.5.5   (mesmo endereço IPv4 da Loopback)
F) Grupo-06   Router ID: 6.6.6.6   (mesmo endereço IPv4 da Loopback)
```

04. Declaração das Redes OSPF entre os Grupos
```bash
A) Grupo-01
    172.16.10.0 0.0.0.255    (SVI do Switch Layer 3)
    172.16.11.0 0.0.0.255    (Primeiro Integrante do Grupo)
    172.16.12.0 0.0.0.255    (Segundo Integrante do Grupo)
    172.16.13.0 0.0.0.255    (Terceiro Integrante do Grupo)
    172.16.14.0 0.0.0.255    (Quarto Integrante do Grupo)
    172.16.15.0 0.0.0.255    (Rede Sem-Fio do Grupo)
    192.168.1.0 0.0.0.3      (Grupo 01 para Grupo 02)
    192.168.1.20 0.0.0.3     (Grupo 06 para Grupo 01)
  
B) Grupo-02
    172.16.20.0 0.0.0.255    (SVI do Switch Layer 3)
    172.16.21.0 0.0.0.255    (Primeiro Integrante do Grupo)
    172.16.22.0 0.0.0.255    (Segundo Integrante do Grupo)
    172.16.23.0 0.0.0.255    (Terceiro Integrante do Grupo)
    172.16.24.0 0.0.0.255    (Quarto Integrante do Grupo)
    172.16.25.0 0.0.0.255    (Rede Sem-Fio do Grupo)
    192.168.1.4 0.0.0.3      (Grupo 02 para Grupo 03)
    192.168.1.0 0.0.0.3      (Grupo 01 para Grupo 02)
  
C) Grupo 03
    172.16.30.0 0.0.0.255    (SVI do Switch Layer 3)
    172.16.31.0 0.0.0.255    (Primeiro Integrante do Grupo)
    172.16.32.0 0.0.0.255    (Segundo Integrante do Grupo)
    172.16.33.0 0.0.0.255    (Terceiro Integrante do Grupo)
    172.16.34.0 0.0.0.255    (Quarto Integrante do Grupo)
    172.16.35.0 0.0.0.255    (Rede Sem-Fio do Grupo)
    192.168.1.8 0.0.0.3      (Grupo 03 para Grupo 04)
    192.168.1.4 0.0.0.3      (Grupo 02 para Grupo 03)

D) Grupo-04
    172.16.40.0 0.0.0.255    (SVI do Switch Layer 3)
    172.16.41.0 0.0.0.255    (Primeiro Integrante do Grupo)
    172.16.42.0 0.0.0.255    (Segundo Integrante do Grupo)
    172.16.43.0 0.0.0.255    (Terceiro Integrante do Grupo)
    172.16.44.0 0.0.0.255    (Quarto Integrante do Grupo)
    172.16.45.0 0.0.0.255    (Rede Sem-Fio do Grupo)
    192.168.1.12 0.0.0.3     (Grupo 04 para Grupo 05)
    192.168.1.8 0.0.0.3      (Grupo 03 para Grupo 04)
  
E) Grupo-05
    172.16.50.0 0.0.0.255    (SVI do Switch Layer 3)
    172.16.51.0 0.0.0.255    (Primeiro Integrante do Grupo)
    172.16.52.0 0.0.0.255    (Segundo Integrante do Grupo)
    172.16.53.0 0.0.0.255    (Terceiro Integrante do Grupo)
    172.16.54.0 0.0.0.255    (Quarto Integrante do Grupo)
    172.16.55.0 0.0.0.255    (Rede Sem-Fio do Grupo)
    192.168.1.16 0.0.0.3     (Grupo 05 para Grupo 06)
    192.168.1.12 0.0.0.3     (Grupo 04 para Grupo 05)

F) Grupo-06
    172.16.60.0 0.0.0.255    (SVI do Switch Layer 3)
    172.16.61.0 0.0.0.255    (Primeiro Integrante do Grupo)
    172.16.62.0 0.0.0.255    (Segundo Integrante do Grupo)
    172.16.63.0 0.0.0.255    (Terceiro Integrante do Grupo)
    172.16.64.0 0.0.0.255    (Quarto Integrante do Grupo)
    172.16.65.0 0.0.0.255    (Rede Sem-Fio do Grupo)
    192.168.1.20 0.0.0.3     (Grupo 05 para Grupo 06)
    192.168.1.16 0.0.0.3     (Grupo 06 para Grupo 01)
```

## DÉCIMA ETAPA: Configuração dos Routers e Access Point D-Link, TP-Link ou Linksys 

01. Endereço IPv4 de cada Access Point para o Gerenciamento dos Grupos
```bash
A) Grupo-01   IPv4: 172.16.15.250 - Máscara: 255.255.255.0
B) Grupo-02   IPv4: 172.16.25.250 - Máscara: 255.255.255.0
C) Grupo-03   IPv4: 172.16.35.250 - Máscara: 255.255.255.0
D) Grupo-04   IPv4: 172.16.45.250 - Máscara: 255.255.255.0
E) Grupo-05   IPv4: 172.16.55.250 - Máscara: 255.255.255.0
F) Grupo-06   IPv4: 172.16.65.250 - Máscara: 255.255.255.0
```

02. Configuração da Rede Sem-Fio (cuidado com roteador Dual Band 2.4 e 5.0Ghz)
```bash
A) Grupo-01   SSID: G-01 (G-01-2.4 e G-01-5.0) - Senha: ????
B) Grupo-02   SSID: G-02 (G-02-2.4 e G-02-5.0) - Senha: ????
C) Grupo-03   SSID: G-03 (G-03-2.4 e G-03-5.0) - Senha: ????
D) Grupo-04   SSID: G-04 (G-04-2.4 e G-04-5.0) - Senha: ????
E) Grupo-05   SSID: G-05 (G-05-2.4 e G-05-5.0) - Senha: ????
F) Grupo-06   SSID: G-06 (G-06-2.4 e G-06-5.0) - Senha: ????
```

## DÉCIMA PRIMEIRA ETAPA: Configuração dos Desktops GNU/Linux e Windows 10

01. Configuração do Hostname e Workgroup dos Desktop GNU/Linux e Windows 10
```bash
A) Grupo-01   Linux Hostname: VLAN-???-NomePrimeiroUsuário-Gnu   Windows Hostname: VLAN-???-NomePrimeiroUsuário-Win
B) Grupo-02   Linux Hostname: VLAN-???-NomePrimeiroUsuário-Gnu   Windows Hostname: VLAN-???-NomePrimeiroUsuário-Win
C) Grupo-03   Linux Hostname: VLAN-???-NomePrimeiroUsuário-Gnu   Windows Hostname: VLAN-???-NomePrimeiroUsuário-Win
D) Grupo-04   Linux Hostname: VLAN-???-NomePrimeiroUsuário-Gnu   Windows Hostname: VLAN-???-NomePrimeiroUsuário-Win
E) Grupo-05   Linux Hostname: VLAN-???-NomePrimeiroUsuário-Gnu   Windows Hostname: VLAN-???-NomePrimeiroUsuário-Win
F) Grupo-06   Linux Hostname: VLAN-???-NomePrimeiroUsuário-Gnu   Windows Hostname: VLAN-???-NomePrimeiroUsuário-Win

A) Grupo-01   Linux Workgroup: Grupo-0??-VLAN-???   Windows Hostname: Grupo-0??-VLAN-???
B) Grupo-02   Linux Workgroup: Grupo-0??-VLAN-???   Windows Hostname: Grupo-0??-VLAN-???
C) Grupo-03   Linux Workgroup: Grupo-0??-VLAN-???   Windows Hostname: Grupo-0??-VLAN-???
D) Grupo-04   Linux Workgroup: Grupo-0??-VLAN-???   Windows Hostname: Grupo-0??-VLAN-???
E) Grupo-05   Linux Workgroup: Grupo-0??-VLAN-???   Windows Hostname: Grupo-0??-VLAN-???
F) Grupo-06   Linux Workgroup: Grupo-0??-VLAN-???   Windows Hostname: Grupo-0??-VLAN-???
```