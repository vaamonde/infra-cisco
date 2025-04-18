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
Versão: 0.03<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ Conhecendo o Serviço do DNS Server no Cisco Packet Tracer;<br>
#02_ Configurando o Serviço do DNS Server no Cisco Packet Tracer;<br>
#03_ Testando o Serviço do DNS Server no Cisco Packet Tracer.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do DNS Server do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

## PRIMEIRA ETAPA: Conhecendo o Serviço do DNS Server no Cisco Packet Tracer.

**DNSv4 (Domain Name System)** é um sistema hierárquico e distribuído de gestão de nomes para computadores, serviços ou qualquer máquina conectada à Internet ou a uma rede privada. Utilizado principalmente para fazer as resoluções de nomes para endereços IPv4 ou IPv6.

O protocolo padrão utilizado pelo DNS Server é o: *UDP (User Datagram Protocol)* na porta padrão: *53*, utilizada principalmente pelo cliente para fazer as consultas de Nomes para IP ou IP para Nomes.

**OBSERVAÇÃO-01:** O DNS Server também utiliza o: *TCP (Transmission Control Protocol)* na porta padrão: *53*,utilizado para receber a transferência de Zonas entre o Servidores: *Master (Mestre - Preferencial)* e: *Slaver (Escravo - Alternativo)*.

**OBSERVAÇÃO-02:** O DNS Server também utiliza o: *TCP (Transmission Control Protocol)* na porta padrão: *953*, utilizado pelo serviço do RNDC (Remote Name Daemon Control).

**DICA-01:** Zona de Pesquisa Direta: resolução de Nome para endereço IPv4 ou IPv6.

**DICA-02:** Zona de Pesquisa Inversa/Reversa: resolução de endereço IPv4 ou IPv6 para Nome.

**Registros DNS:** Os registros DNS são mapeamentos de arquivos ou sistemas que dizem a um servidor DNS para qual endereço IP um determinado domínio está associado. Também informa aos servidores DNS como lidar com as solicitações que estão sendo enviadas para cada nome de domínio.

**Sintaxe DNS:** Diferentes sequências de letras são usadas para ditar as ações do servidor DNS. Essas letras são chamadas de sintaxe DNS (Exemplo: A, AAAA, CNAME, MX, PTR, NS, SOA, SRV, TXT, etc).

**Registro Tipo A....:** Significa Endereço e é o tipo mais básico de sintaxe DNS. Indica o endereço IP real para um domínio ou computador;<br>
**Registro Tipo AAAA.:** Igual ao Tipo A mais utilizado nas configurações do IPv6;<br>
**Registro Tipo CNAME:** Significa o Nome Canônico (Canonical Name Record) e seu papel é fazer que um domínio use um alias (Pseudônimo - Apelido) de outro domínio;<br>
**Registro Tipo SOA..:** Significa Início de Autoridade. Obviamente é um dos registros de DNS mais importantes;<br>
**Registro Tipo NS...:** Significa Name Server ele indica qual nome de servidor é autoritativo para o domínio.

## SEGUNDA ETAPA: Configurando o Serviço do DNS Server no Cisco Packet Tracer.

**OBSERVAÇÃO-03:** por padrão o Serviço de DNS Server no Cisco Packet Tracer está: *desligado*.

**OBSERVAÇÃO-04:** no Cisco Packet Tracer as configuração de Sintaxe DNS são limitadas somente ao tipos: *A, AAA, CNAME, SOA e NS* estão disponíveis para configuração.

**OBSERVAÇÃO-05:** no Cisco Packet Tracer temos apenas a configuração da Zona de Pesquisa Direta, não está disponível a opção para configurar a Zona de Pesquisa Reversa.

```bash
!Habilitando o Serviço do DNS Server no Servidor 02
Server-02
  Services
    DNS

DNS Service:       On
Resource Records:  Name = server-02        Type = A Record     Address = 172.16.0.33
Resource Records:  Name = ns1.senac.br     Type = NS           Server Name = server-02
Resource Records:  Name = senac.br         Type = SOA          Primary Server Name = ns1.senac.br
                                                               Mail Box = vaamonde@senac.br
                                                               Minimum TTL = 3600 (1h ou 60 minutos)
                                                               Refresh Time = 3600 (1h ou 60 minutos)
                                                               Retry Time = 600 (10 minutos)
                                                               Expiry Time = 86400 (24h ou 1440 minutos)
Resource Records:  Name = senac.br         Type = CNAME        Host Name = server-03
Resource Records:  Name = www.senac.br     Type = CNAME        Host Name = server-03
Resource Records:  Name = pop3.senac.br    Type = CNAME        Host Name = server-03
Resource Records:  Name = smtp.senac.br    Type = CNAME        Host Name = server-03
Resource Records:  Name = ftp.senac.br     Type = CNAME        Host Name = server-03
Resource Records:  Name = server-03        Type = A Record     Address = 172.16.0.34
Resource Records:  Name = server-04        Type = A Record     Address = 172.16.0.35
Resource Records:  Name = server-05        Type = A Record     Address = 172.16.0.36

A) Abrindo o Prompt de Comando do Desktop;

**DICA-03** não confunda Terminal com Command Prompt, Terminal é utilizado para se conectar no Switch ou Router utilizando o Cabo Console, já o Command Prompt (Prompt de Comando) é utilizado para testar as configurações de rede e acessar remotamente o Switch ou Router.
```

## TERCEIRA ETAPA: Testando o Serviço do DNS Server no Cisco Packet Tracer.

A) Abrindo o Prompt de Comando do Desktop;

**DICA-03** não confunda Terminal com Command Prompt, Terminal é utilizado para se conectar no Switch ou Router utilizando o Cabo Console, já o Command Prompt (Prompt de Comando) é utilizado para testar as configurações de rede e acessar remotamente o Switch ou Router.

```bash
!Verificando o endereço IPv4 configurado no Desktop
C:\> ipconfig

!Verificando o endereço detalhado IPv4 configurado no Desktop
C:\> ipconfig /all

!Testando a Resolução de Nomes DNS no Desktop
C:\> nslookup server-02

!Testando a comunicação com o Server 01 utilizando o pacote ICMP (Internet Control Message Protocol)
C:\> ping server-02
```
