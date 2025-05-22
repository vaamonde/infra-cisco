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
Data de atualização: 20/05/2025<br>
Versão: 0.04<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ Configuração do Servidor de NTP Local<br>
#02_ Configuração dos Clientes de NTP nos Switches e Router<br>
#03_ Visualizando as configurações de Data Hora nos Switches e Router<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do NTP Server do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

O **NTP (Network Time Protocol)** é um protocolo para sincronização dos relógios dos computadores. É utilizado para sincronização do relógio de um conjunto de computadores e dispositivos em redes de dados com latência variável.

O protocolo padrão utilizado pelo NTP é o *UDP (User Datagram Protocol)* na porta padrão: *123*

No Brasil, o Servidor de Referência de Data e Hora é o Ntp.br: a.st1.ntp.br **(IPv4: 200.160.7.186 e IPv6: 2001:12ff:0:7::186)**

## PRIMEIRA ETAPA: Configuração do Servidor de NTP Local

**OBSERVAÇÃO-01:** por padrão o Servidor de NTP do Cisco Packet Tracer está ligado

```python
!Habilitando o Serviço do NTP Server no Servidor 05
Server-05
  Services
    NTP

!Configurando o serviço do NTP Server no Servidor 05
NTP Service:    On
Authentication: Enable
Key:            123456    Password: SUA_SENHA
Date:           22/05/2025
Hour:           15:00:00 PM
```

## SEGUNDA ETAPA: Configuração dos Clientes de NTP nos Switches e Router

```python
!Acessando o modo EXEC Privilegiado
enable

  !Verificando a Data e Hora atual do Switch e Router
  show clock

    !Acessando o modo de Configuração Global de Comandos
    configure terminal
      
      !Configuração do Fuso Horário (Timezone) do Switch e Router
      !DICA-01: configurar o Fuso Horário nos equipamentos é obrigatório para a Data/Hora ficar correta
      !OBSERVAÇÃO-02: a configuração do Fuso Horário é dividida em: Nome da Zona (BR) e o UTC (Coordinated Universal Time)
      !OBSERVAÇÃO-03: no Brasil utilizamos quatro UTCs diferentes, em São Paulo utilizamos o UTC de Brasília -3
      !ERRATA-01: no Cisco Packet Tracer tem um Bug em relação ao UTC, mesmo configurado com o comando: show clock temos o
      !erro na configuração da Hora
      clock timezone BR -3
      
      !Habilitando o recurso de Autenticação do Servidor NTP
      !DICA-02: esse recurso aumenta o nível de segurança da configuração de NTP Server
      ntp authenticate
      
      !Configurando a Chave e Senha de autenticação do Servidor NTP
      !DICA-03: a chave por padrão é uma sequência numérica já a senha é criptografada utilizando o MD5
      !OBSERVAÇÃO-04: essas informações são configuradas no Servidor de NTP Local
      ntp authentication-key 123456 md5 SUA_SENHA
      
      !Configurando o Endereço IPv4 do Servidor de NTP
      !DICA-04: por padrão apenas um servidor de NTP é configurado no Cisco Packet Tracer, em equipamentos reais permite mais
      !DICA-05: Switch Layer 3 ou Router pode ser Servidores de NTP na Rede usando a opção: ntp master 1 (stratum)
      !OBSERVAÇÃO-05: não é possível utilizar nomes para servidores de NTP no Cisco Packet Tracer, somente endereços IPv4
      ntp server 172.16.0.99
      
      !Habilitando o sincronismo da Data e Hora do NTP Server com o Hardware
      !DICA-06: essa opção habilitar o recurso de sincronização de Data/Hora de Software e Hardware
      !OBSERVAÇÃO-06: no Switch Layer 2 2960 esse recurso não está disponível para configuração
      ntp update-calendar
      
      !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
      end

    !Salvando as configurações da memória RAM para a memória NVRAM
    write
```

## TERCEIRA ETAPA: Visualizando as configurações de Data Hora nos Switches e Router

```python
!Visualizando as configurações da memória RAM
show running-config | include ntp

!Comandos para teste e verificação do Sincronismo do NTP Server
!OBSERVAÇÃO-07: a sincronização no Cisco Packet Tracer demora alguns segundos

!Visualizando as configurações do NTP Local
show ntp status
show ntp associations

!Visualizando a Data e Hora Sincronizada
show clock
```