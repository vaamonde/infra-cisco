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
Versão: 0.07<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Conhecendo o Serviço do DNS Server no Cisco Packet Tracer.<br>
#02_ SEGUNDA ETAPA: Testando o Serviço do DNS Server no Cisco Packet Tracer.<br>
#03_ TERCEIRA ETAPA: Configurando o Serviço do DNS no Switch e Router no Cisco Packet Tracer.<br>
#04_ QUARTA ETAPA: Testando o Serviço de DNS Server nos Switches e Routers.<br>
#05_ QUINTA ETAPA: Automatizando a Configuração do Segundo Switch 2960 e Router 1941<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração DNS Server do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Config Basic DNS](http://img.youtube.com/vi/KultMQMMCiQ/0.jpg)](https://www.youtube.com/watch?v=KultMQMMCiQ "Config Basic DNS")

Link da vídeo aula: https://www.youtube.com/watch?v=KultMQMMCiQ

## PRIMEIRA ETAPA: Conhecendo o Serviço do DNS Server no Cisco Packet Tracer.

**DNSv4 (Domain Name System)** é um sistema hierárquico e distribuído de gestão de nomes para computadores, serviços ou qualquer máquina conectada à Internet ou a uma rede privada. Utilizado principalmente para fazer as resoluções de nomes para endereços IPv4 ou IPv6.

O protocolo padrão utilizado pelo DNS Server é o: *UDP (User Datagram Protocol)* na porta padrão: *53*, utilizada principalmente pelo cliente para fazer as consultas de Nomes para IP ou IP para Nomes.

**OBSERVAÇÃO-01:** O DNS Server também utiliza o: *TCP (Transmission Control Protocol)* na porta padrão: *53*,utilizado para receber a transferência de Zonas entre o Servidores: *Master (Mestre - Preferencial)* e: *Slaver (Escravo - Alternativo)*.

**OBSERVAÇÃO-02:** O DNS Server também utiliza o: *TCP (Transmission Control Protocol)* na porta padrão: *953*, utilizado pelo serviço do RNDC (Remote Name Daemon Control).

**DICA-01:** Zona de Pesquisa Direta: resolução de Nome para endereço IPv4 ou IPv6.

**DICA-02:** Zona de Pesquisa Inversa/Reversa: resolução de endereço IPv4 ou IPv6 para Nome.

**Registros DNS:** Os registros DNS são mapeamentos de arquivos ou sistemas que dizem a um servidor DNS para qual endereço IP um determinado domínio está associado. Também informa aos servidores DNS como lidar com as solicitações que estão sendo enviadas para cada nome de domínio.

**Sintaxe DNS:** Diferentes sequências de letras são usadas para ditar as ações do servidor DNS. Essas letras são chamadas de sintaxe DNS (Exemplo: A (IPv4), AAAA (IPv6), CNAME, MX, PTR, NS, SOA, SRV, TXT, etc).

**Registro Tipo A....:** Significa Endereço e é o tipo mais básico de sintaxe DNS. Indica o endereço IP real para um domínio ou computador;<br>
**Registro Tipo AAAA.:** Igual ao Tipo A mais utilizado nas configurações do IPv6;<br>
**Registro Tipo CNAME:** Significa o Nome Canônico (Canonical Name Record) e seu papel é fazer que um domínio use um alias (Pseudônimo - Apelido) de outro domínio;<br>
**Registro Tipo SOA..:** Significa Início de Autoridade. Obviamente é um dos registros de DNS mais importantes;<br>
**Registro Tipo NS...:** Significa Name Server ele indica qual nome de servidor é autoritativo para o domínio.

01. Configurações do Serviço de DNS Server no Cisco Packet Tracer.

**OBSERVAÇÃO-03:** por padrão o Serviço de DNS Server no Cisco Packet Tracer está: *desligado*.

**OBSERVAÇÃO-04:** no Cisco Packet Tracer as configuração de Sintaxe DNS são limitadas somente ao tipos: *A (IPv4), AAAA (IPv6), CNAME, SOA e NS* estão disponíveis para configuração.

**OBSERVAÇÃO-05:** no Cisco Packet Tracer temos apenas a configuração da Zona de Pesquisa Direta, não está disponível a opção para configurar a Zona de Pesquisa Reversa.
```bash
!Habilitando o Serviço do DNS Server no Servidor 01
Server-01
  Services
    DNS
      DNS Service:       On

!Criando os Ponteiros do Tipo A no DNS Server
Resource Records:  Name = server-01       Type = A Record     Address = 192.168.1.1
Resource Records:  Name = sw-01           Type = A Record     Address = 192.168.1.250
Resource Records:  Name = sw-02           Type = A Record     Address = 192.168.1.251
Resource Records:  Name = rt-01           Type = A Record     Address = 192.168.1.254
Resource Records:  Name = desktop-01      Type = A Record     Address = 192.168.1.10
Resource Records:  Name = desktop-02      Type = A Record     Address = 192.168.1.11
Resource Records:  Name = desktop-03      Type = A Record     Address = 192.168.1.12
Resource Records:  Name = desktop-04      Type = A Record     Address = 192.168.1.13
Resource Records:  Name = notebook-01     Type = A Record     Address = 192.168.1.21
Resource Records:  Name = notebook-02     Type = A Record     Address = 192.168.1.23
Resource Records:  Name = celular-01      Type = A Record     Address = 192.168.1.20
Resource Records:  Name = celular-02      Type = A Record     Address = 192.168.1.22
```

## SEGUNDA ETAPA: Testando o Serviço do DNS Server no Cisco Packet Tracer.

a) Abrindo o Prompt de Comando do Desktop.

**DICA-03** não confunda Terminal com Command Prompt, Terminal é utilizado para se conectar no Switch ou Router utilizando o Cabo Console, já o Command Prompt (Prompt de Comando) é utilizado para testar as configurações de rede e acessar remotamente o Switch ou Router.
```bash
!Verificando o endereço IPv4 configurado no Desktop
C:\> ipconfig

!Verificando o endereço detalhado IPv4 configurado no Desktop
C:\> ipconfig /all

!Testando a Resolução de Nomes DNS no Desktop
C:\> nslookup server-01
C:\> nslookup sw-01

!Testando a comunicação com o Server 01 utilizando o pacote ICMP (Internet Control Message Protocol)
C:\> ping server-01

!Testando a comunicação com o Switch 01 utilizando o pacote ICMP (Internet Control Message Protocol)
C:\> ping sw-01

!Acessando remotamente o Switch utilizando o protocolo SSH (Secure Shell)
!OBSERVAÇÃO: -l (éli não é o número "1" (um) e sim "l" (éli) em minúsculo)
C:\> ssh -l admin sw-01   (Switch SW-01)
```

## TERCEIRA ETAPA: Configurando o Serviço do DNS no Switch e Router no Cisco Packet Tracer.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: robson
Password: pti@2018

sw-01> enable
Password: pti@2018

sw-01# configure terminal
sw-01(config)#
```

A) Habilitando o recurso de Resolução de Nomes de Domínio no Switch ou no Router

**OBSERVAÇÃO-06:** esse recurso vem habilitado por padrão no Switch ou no Router, no começo no curso esse recurso foi desabilitado para corrigir a falha de digitar comandos errados no Cisco IOS e travar o terminal, só habilitar novamente esse recurso se você for utilizar o serviço de DNS no Switch ou no Router.

**OBSERVAÇÃO-07:** por padrão o endereço IPv4 de resolução de nomes de DNS no Switch ou no Router é: 255.255.255.255 (Broadcast IPv4).

**DICA-04** habilitar esse recurso somente quando o Servidor DNS estiver configurado, caso contrário, desabilitar para não causar falhas na digitação de comandos no Cisco IOS.

```bash
sw-01(config)# ip domain-lookup
```

B) Configurando o Nome de Domínio no Switch ou no Router

**OBSERVAÇÃO-08:** esse recurso já foi configurado no Switch e no Router, ele é necessário para o serviço do SSH Server e para o correto funcionando do serviço do DNS Server.

**DICA-05** a configuração do Nome de Domínio é recomendada mesmo que não seja utilizada no Switch ou no Router ou recursos de resolução de nomes do DNS.

```bash
sw-01(config)# ip domain-name pti.intra
```

C) Configurando o Endereço IPv4 do Servidor de DNS no Switch ou no Router

**DICA-06** após a configuração do endereço IPv4 do Servidor de DNS no Switch ou no Router ele não usará mais o endereço de Broadcast IPv4 255.255.255.255 para a resolução de nomes de DNS, agora ele irá consultar o servidor de DNS para resolver os nomes de host.

**OBSERVAÇÃO-09:** você só pode configurar apenas um Servidor de Resolução de Nomes de DNS no Switch ou no Router no Cisco IOS

```bash
sw-01(config)# ip name-server 192.168.1.1
```

D) Adicionando manualmente a Resolução de Nomes e Endereços Estáticos no Switch ou no Router

**DICA-07** por padrão o Switch ou Router consulta primeiro a Base Dados Local de Nomes e depois o serviço do DNS Server configurado na opção: *ip name-server*

**OBSERVAÇÃO-10:** a criação de nomes locais facilita o acesso a equipamentos sem a necessidade de um servidor de DNS configurado no rede

**OBSERVAÇÃO-11:** a desvantagem desse método está relacionada a configuração de forma manual em cada equipamento na rede, sua atualização não é dinâmica, qualquer mudança na topologia de nomes ou endereços IP deverá ser feito a atualização manualmente em cada dispositivos na rede.
```bash
sw-01(config)# ip host google 8.8.8.8
```

E) Saindo de todos os níveis e voltando para o modo EXEC Privilegiado.

**DICA-08:** somente no modo EXEC Privilegiado você tem o comando: *copy* para salvar as configurações.
```bash
sw-01(config-if)# end
```

F) Salvando as configurações da memória RAM (Running-Config) para a memória NVRAM (Startup-Config)

**DICA-09:** nunca esqueça de salvar as configurações.
```bash
rt-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
rt-01#
```

02. Visualizando as configurações da memória RAM (Running-Config).
```bash
!Visualizando as Configurações do Running-Config (RAM)
sw-01# show running-config

!Fazendo um Filtro na Visualização do Running-Config somente da Sessão IP
sw-01# show running-config | section include ip
```

## QUARTA ETAPA: Testando o Serviço de DNS Server nos Switches e Routers.

01. Testando a resolução de nomes no Switch e Router

```bash
!OBSERVAÇÃO IMPORTANTE: CARACTERES UTILIZADOS NA SAÍDA DO COMANDO PING NO CISCO
!a) "!"  = Receipt of a reply (Echo reply recebido (ping Ok))
!b) "."  = The Network service timed out while waiting for a reply (Echo reply não chegou no tempo limite)
!c) "?"  = Unknown packet type (Tipo de pacote desconhecido)
!d) "|"  = Ping Interrupted (Interrompido, cancelado)
!e) "&"  = Package lifetime exceeded (Tempo de vida do pacote excedido)
!f) "!H" = Host unreachable (Negado administrativamente (access-list))
!g) "C"  = Congested network (Rede congestionada)
!h) "M"  = Could not fragment (Problema na fragmentação)
!i) "N"  = Network (Rede inalcançável)
!j) "P"  = Protocol (Protocolo inalcançável (problema no protocolo))
!k) "Q"  = Source quench (Destino ocupado)
!l) "U"  = Destination Unreachable (Destino inalcançável (falta de rota, access-list…))

!Digitando um comando errado no Modo EXEC Privilegiado
sw-01# time
  Translating "time"...domain server (192.168.1.1)
  % Unknown command or computer name, or unable to find computer address
sw-01#

!Pingando o Nome de host do Google
sw-01# ping google
  Type escape sequence to abort.
  Sending 5, 100-byte ICMP Echos to 8.8.8.8, timeout is 2 seconds:
  U.U.U
  Success rate is 0 percent (0/5)
sw-01#

!Pingando o Router pelo nome
sw-01# ping rt-01
  Type escape sequence to abort.
  Sending 5, 100-byte ICMP Echos to 192.168.1.254, timeout is 2 seconds:
  !!!!!
  Success rate is 100 percent (5/5), round-trip min/avg/max = 0/0/0 ms
sw-01#

!Acessando o Router via SSH pelo nome
sw-01# ssh -l admin rt-01
  Trying 192.168.1.254 ...
  Password: 
  AVISO: acesso autorizado somente a funcionarios
rt-01#
```

## QUINTA ETAPA: Automatizando a Configuração do Segundo Switch 2960 e Router 1941.

01. Utilizando o Visual Studio Code (VSCode) para automatizar as configurações do Cisco IOS.

**OBSERVAÇÃO-12:** recomendo sempre utilizar um *Editor de Texto Profissional* para criar os scripts e automatizar as tarefas de configuração do Cisco IOS, hoje em dia é indicado utilizar o Visual Studio Code (VSCode) junto com as Extensões: *Cisco IOS Syntax e Cisco Config Highlight* para facilitar essa configuração.

**DICA-10:** o caractere: *! (exclamação)* é utilizado como um recurso de *Comentário*, sua utilização server para comentar o código de automação do Cisco IOS ou para desativar um comando para não ser executado, *RECOMENDO FORTEMENTE DOCUMENTAR TODOS OS COMANDOS E PROCEDIMENTOS DE CONFIGURAÇÃO PARA FACILITAR O ENTENDIMENTO.*

**DICA-11:** para facilitar a leitura do código, recomendo utilizar o recurso de **Indentação de Código** usando a Tecla TAB (Tabulador/Tabulação) para cada nível que você está configurando o Cisco IOS, isso facilitada a análise de erros (Debug) do código.

```python
!Acessando o modo de Configuração Global de comandos
configure terminal

  !Habilitando o serviço de resolução de nomes de DNS
  ip domain-lookup

  !Configurando o serviço de resolução de nomes de DNS
  ip name-server 192.168.1.1

  !Adicionando manualmente um host e endereço IP
  ip host google 8.8.8.8
  
  !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
  end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```