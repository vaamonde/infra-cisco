#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 16/09/2024<br>
#Data de atualização: 22/05/2025<br>
#Versão: 0.09<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>
#Testado e homologado o Cisco Packet Tracer 8.2.x x64 e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.<br>
#02_ SEGUNDA ETAPA: Configuração do Gateway padrão IPv4 no Cisco IOS.<br>
#03_ TERCEIRA ETAPA: Configuração da Interface SVI no Cisco IOS.<br>
#04_ QUARTA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração SVI Switch 2960 do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Config SVI 2960](http://img.youtube.com/vi/ueh8gp37RG8/0.jpg)](https://www.youtube.com/watch?v=ueh8gp37RG8 "Config SVI 2960")

Link da vídeo aula: https://www.youtube.com/watch?v=ueh8gp37RG8

## PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: SEU_USUÁRIO
Password: SUA_SENHA

sw-01> enable
Password: SUA_SENHA_SEGURA

sw-01# configure terminal
sw-01(config)#
```

## SEGUNDA ETAPA: Configuração do Gateway padrão IPv4 no Cisco IOS.

01. Configuração do Gateway Padrão IPv4 no Switch para Acesso Remoto.

**DICA-01:** configuração do Gateway IPv4 em Switch Cisco Catalyst Layer 2 serve somente para acesso remoto com finalidade de monitoramento/gerenciamento do Switch;

**DICA-02:** em Switch Cisco Catalyst Layer 3 o recurso de Gateway é utilizado tanto para acesso remoto ou para roteamento de Redes/Sub-Redes utilizando principalmente VLAN (Virtual-LAN) ou Protocolos de Roteamento IGP (Interior Gateway Protocols) como o: RIP (Routing Information Protocol), EIGRP (Enhanced Interior Gateway Routing Protocol), OSPF (Open Shortest Path First), Rota Estática, etc...

**OBSERVAÇÃO-01:** esse recurso é necessário para administração remota ou monitoramento do Switch Cisco Catalyst Layer 2 ou Layer 3.

**OBSERVAÇÃO-02:** existe a possibilidade da configuração do Gateway utilizar o endereço IPv6 em Switch Cisco Catalyst Layer 2 ou Layer 3, para essa configuração é recomendo utilizar o Cisco IOS na versão mínima 15.x (versão padrão no Cisco Packet Tracer 8.2.2 - v15.0.-2-SE4 que já tem suporte ao IPv6).
```bash
sw-01(config)# ip default-gateway 192.168.1.254
```

## TERCEIRA ETAPA: Configuração da Interface SVI no Cisco IOS.

01. Configuração da Interface Virtual do Switch SVI (Switch Virtual Interface).

**DICA-03:** interfaces virtuais são criadas utilizando o recurso de VLAN (Virtual-LAN) disponível nos Switch Cisco Catalyst Layer 2 ou Layer 3.

**DICA-04:** é recomendado utilizar outra VLAN para o SVI, não é recomendado utilizar a VLAN padrão 1 para essa finalidade, a VLAN 1 (VLAN Default) existe em todos os Switch e é por causa disso que Switches de Fabricantes Diferente se comunicam entre si, todos utilizam sempre a VLAN 1 como padrão para a comunicação.

**OBSERVAÇÃO-03:** em Switch Cisco Catalyst Layer 2 utilizamos o SVI somente para administração remota ou monitoramento do equipamento, ela não será utilizada para Gateway da Rede Local ou para integração com Protocolos de Roteamento.

**OBSERVAÇÃO-04:** o SVI é necessário para o acesso remoto nas Linhas Virtuais (VTY) utilizando os protocolos Telnet, SSH ou outro protocolo configurado, após a configuração da SVI o Switch irá possuir um Endereço Físico (MAC Address) associado a um Endereço Lógico de Rede (IPv4 ou IPv6) permitindo o seu acesso remoto.
```bash
sw-01(config)# interface vlan 1
```

A) Configuração da Descrição da Interface Virtual VLAN-1.

**DICA-05:** sempre utilizar o comando: *description* nas Interfaces para efeito de documentação.

**OBSERVAÇÃO-05:** documentação de Interface facilita o processo de identificação e função dela na topologia de rede, configuração obrigatória em Switch ou Router.
```bash
sw-01(config-if)# description Interface de Gerenciamento do Switch SW-01
```

B) Configuração do Endereçamento IPv4 da Interface Virtual VLAN-1.

**DICA-06:** o endereço IPv4 deve ser da mesma faixa de Rede ou Sub-Rede do Gateway Padrão configurado no Switch na Segunda Etapa.

**DICA-07:** é recomendado que os endereços de Rede ou Sub-Redes dos Switches sejam diferentes das Redes dos Desktops, Notebook, Wi-Fi (Wireless/Sem-Fio), CFTV (Circuito Fechado de TV), etc... para garantir a segurança de acesso aos equipamentos somente para a equipe/profissionais de TI que esteja nessa mesma Rede/Sub-Rede.

**OBSERVAÇÃO-06:** configuração do endereço IPv4 deve ser: *IPv4 + Máscara de Rede Completa (ClassFull)*, não utilizar CIDR (Classes Inter-Domain Routing) nas configurações.
```bash
sw-01(config-if)# ip address 192.168.1.250 255.255.255.0
```

C) Inicializando a Interface Virtual da VLAN-1.

**DICA-08:** por padrão todas as Interfaces estão no status: *desligada (Shutdown)* no Switch ou Router.

**DICA-09:** por padrão todas as Portas de Rede estão no status: *ligada (No-Shutdown)* no Switch.

**OBSERVAÇÃO-07:** o comando: *no* também é utilizado para ligar as Interfaces tirando do status: *shutdown (Desligada)* e mudando o seu status para: *no shutdown (Ligada)*.
```bash
sw-01(config-if)# no shutdown
```

D) Saindo de todos os níveis e voltando para o modo EXEC Privilegiado.

**DICA-10:** somente no modo EXEC Privilegiado você tem o comando: *copy* para salvar as configurações.

**DICA-11:** existe também o comando: *do*, esse comando permite executar qualquer comando fora do seu nível padrão.

**EXEMPLO:** sw-01(config-line)# do copy running-config startup-config | sw-01(config-line)# do show running-config | sw-01(config-line)# do write
```bash
sw-01(config-if)# end
sw-01#
```

E) Salvando as configurações da memória RAM (Running-Config) para a memória NVRAM (Startup-Config)

**DICA-12:** nunca esqueça de salvar as configurações.
```bash
sw-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
sw-01#
```

09. Visualizando as configurações da memória RAM (Running-Config).

**DICA-13** após a configuração da SVI verifique se tudo está configurado de forma correta utilizando os comandos: *show*.
```bash
!Visualizando as Configurações do Running-Config (RAM)
sw-01# show running-config
  Building configuration...

  Current configuration : 1763 bytes
  !
  ...
  !
  end
sw-01#
```
```bash
!Fazendo um Filtro na Visualização do Running-Config somente da Interface Vlan1
sw-01# show running-config | section include interface Vlan1
  interface Vlan1
    description Interface de SVI
    ip address 192.168.1.250 255.255.255.0
sw-01#
```
```bash
!Visualizando as configurações das interfaces e portas de rede do Switch
sw-01# show ip interface brief
  Interface              IP-Address      OK? Method Status                Protocol 
  FastEthernet0/1        unassigned      YES manual up                    up 
  FastEthernet0/2        unassigned      YES manual up                    up 
  FastEthernet0/3        unassigned      YES manual down                  down
  ...
  FastEthernet0/24       unassigned      YES manual up                    up 
  GigabitEthernet0/1     unassigned      YES manual up                    up 
  GigabitEthernet0/2     unassigned      YES manual up                    up 
  Vlan1                  192.168.1.250   YES manual up                    up
sw-01#
```
```bash
!Visualizando as configurações das VLANs padrão do Switch
sw-01# show vlan brief
  VLAN Name                             Status    Ports
  ---- -------------------------------- --------- -------------------------------
  1    default                          active    Fa0/1, Fa0/2, Fa0/3, Fa0/4
                                                  Fa0/5, Fa0/6, Fa0/7, Fa0/8
                                                  Fa0/9, Fa0/10, Fa0/11, Fa0/12
                                                  Fa0/13, Fa0/14, Fa0/15, Fa0/16
                                                  Fa0/17, Fa0/18, Fa0/19, Fa0/20
                                                  Fa0/21, Fa0/22, Fa0/23, Fa0/24
                                                  Gig0/1, Gig0/2
  1002 fddi-default                     active    
  1003 token-ring-default               active    
  1004 fddinet-default                  active    
  1005 trnet-default                    active
sw-01#
```

F) Testando a conectividade entre o Switch e os Desktops da Rede

**DICA-14** depois da configuração da SVI no Switch Cisco Catalyst Layer 2 você consegue agora pingar os Desktops da Rede utilizado o Protocolo ICMP (Internet Control Message Protocol) com o comando: *ping* para testar a interconectividade de rede.

**OBSERVAÇÃO-08** o carácter: *! (exclamação)* utilizado no comando: ping significa que os pacotes ICMP enviado para o destino foi recebido com sucesso, o padrão é enviar: *5 Pacotes (Sending 5)* já o carácter: *. (ponto)* significa que os pacotes ICMP foram perdidos ou o destino não recebeu os pacotes.

**OBSERVAÇÃO-09** na última linha do comando: *ping* do Cisco IOS mostra a opção: **Success rate is 100 percent (5/5)** que representa que 100% dos pacotes foram enviado e recebidos totalizando: *5 (cinco) Pacotes Enviados e 5 (cinco) Pacotes Recebidos*, na opção: **round-trip** que é o tempo de vida de ida e volta dos pacotes (RTT - Round Trip Time) medido em milissegundos, Mínimo (min): 8 ms — O menor tempo registrado, Médio (avg): 10 ms — Média dos tempos e Máximo (max): 15 ms — O maior tempo registrado.

**DICA-15:** RTT é o tempo que um pacote leva para sair do dispositivo de origem, chegar ao destino e retornar. Esse tempo inclui: *Latência da Rede, Processamento dos dispositivos intermediários e Variações momentâneas (jitter).*
```bash
!Pingando a SVI do Switch Layer 2 2960 sw-01
sw-01# ping 192.168.1.250
  Type escape sequence to abort.
  Sending 5, 100-byte ICMP Echos to 192.168.1.250, timeout is 2 seconds:
  !!!!!
  Success rate is 100 percent (5/5), round-trip min/avg/max = 8/10/15 ms
sw-01#
```
```bash
!Pingando o endereço IPv4 do Servidor
sw-01# ping 192.168.1.1
  Type escape sequence to abort.
  Sending 5, 100-byte ICMP Echos to 192.168.1.1, timeout is 2 seconds:
  .!!!!
  Success rate is 80 percent (4/5), round-trip min/avg/max = 0/0/0 ms
sw-01#
```

## QUARTA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960.

01. Utilizando o Visual Studio Code (VSCode) para automatizar as configurações do Cisco IOS.

**OBSERVAÇÃO-10:** recomendo sempre utilizar um *Editor de Texto Profissional* para criar os scripts e automatizar as tarefas de configuração do Cisco IOS, hoje em dia é indicado utilizar o Visual Studio Code (VSCode) junto com as Extensões: *Cisco IOS Syntax e Cisco Config Highlight* para facilitar essa configuração.

**DICA-16:** o caractere: *! (exclamação)* é utilizado como um recurso de *Comentário*, sua utilização server para comentar o código de automação do Cisco IOS ou para desativar um comando para não ser executado, *RECOMENDO FORTEMENTE DOCUMENTAR TODOS OS COMANDOS E PROCEDIMENTOS DE CONFIGURAÇÃO PARA FACILITAR O ENTENDIMENTO.*

**DICA-17:** para facilitar a leitura do código, recomendo utilizar o recurso de **Indentação de Código** usando a Tecla TAB (Tabulador/Tabulação) para cada nível que você está configurando o Cisco IOS, isso facilitada a análise de erros (Debug) do código.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: SEU_USUÁRIO
Password: SUA_SENHA

sw-02> enable
Password: SUA_SENHA_SEGURA

sw-02#
```

```python
!Acessando o modo de Configuração Global de comandos
configure terminal

  !Configuração do Gateway padrão IPv4 no Switch
  ip default-gateway 192.168.1.254

  !Configuração da Interface Virtual do Switch SVI
  interface vlan 1

    !Configuração da Descrição da Interface Virtual
    description Interface de Gerenciamento do Switch SW-02

    !Configuração do Endereçamento IPv4 da Interface Virtual
    ip address 192.168.1.251 255.255.255.0

    !Inicializando a Interface Virtual do Switch
    no shutdown

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```