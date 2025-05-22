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
#01_ 

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do SYSLOG Server do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

O **SYSLOG (System Logging Protocol)** é um padrão criado pela IETF (Internet Engineering Task Force) para a transmissão de mensagens de Log em redes IP. O termo é geralmente usado para identificar tanto o protocolo de rede quanto para a aplicação ou biblioteca de envio de mensagens no protocolo syslog.

O protocolo padrão utilizado pelo Syslog é o *UDP (User Datagram Protocol)* na porta padrão: *514*

**OBSERVAÇÃO-01:** O Servidor de Syslog também utiliza o Protocolo *TCP na porta 514*, e com suporte a **Criptografia** na Porta padrão: *6514*

O Syslog trabalha com Níveis de Severidade **(Traps)** que inicia de: *0 até 7* utilizando palavras chaves como:

| Traps | Key words |
|-------|-----------|
| 0 | emergency, |
| 1 | alert, |
| 2 | critical, |
| 3 | error, |
| 4 | warning, |
| 5 | notice, |
| 6 | info, |
| 7 | debugging. |

## PRIMEIRA ETAPA: Configuração do Servidor de Syslog

**OBSERVAÇÃO-02:** por padrão o Servidor de Syslog do Cisco Packet Tracer está ligado

```python
!Habilitando o Serviço do SYSLOG Server no Servidor 05
Server-05
  Services
    SYSLOG
```

## SEGUNDA ETAPA: Configuração dos Switches e Router para enviar os Logs para o Servidor de Syslog

```python
!Acessando o modo EXEC Privilegiado
enable

  !Acessando o modo de Configuração Global de Comandos
  configure terminal
    
    !Habilitando o serviço de marcação de Data/Hora detalhado nos Logs do Switch e Router
    !OBSERVAÇÃO-03: a configuração da Marcação de Data/Hora detalhado nos Log já foi executada no Script Base
    service timestamps log datetime msec
    
    !Habilitando o Recurso de Log no Switch e Router
    !DICA-01: por padrão todos os Logs habilitadoS no Switch ou Router são volátil (desligou, perdeu tudo)
    !OBSERVAÇÃO-04: salvar os Logs no Servidor de Syslog garante a auditoria de falhas nos equipamentos
    logging on
    
    !Configurando o Endereço IPv4 do Servidor de Syslog
    !OBSERVAÇÃO-05: não é possível utilizar nomes para servidores de Syslog no Cisco Packet Tracer, somente IPv4
    logging host 172.16.0.99
    
    !Configurando o Nível de Log que será enviado para o Servidor de Syslog
    !DICA-02: o nível de detalhamento do Log facilita a análise de erros e possíveis falhas de segurança
    !OBSERVAÇÃO-06: no Cisco Packet Tracer temos apenas a opção: Debugging (severity=7)
    logging trap debugging
    
    !Habilitando os Logs de Autenticação que será enviado para o Servidor de Syslog
    !DICA-03: esse recurso aumenta o nível de segurança e auditoria da rede em relação a autenticação física ou remota
    !OBSERVAÇÃO-07: recomendado habilitar os recursos de sucesso e falhas de autenticação física ou remota
    !OBSERVAÇÃO-08: essas informações em conjunto com as regras de segurança aumenta o nível de confiabilidade da rede
    !OBSERVAÇÃO-09: esse recurso não está disponível no Switch Layer 2 2960
    login on-success log
    login on-failure log
    
    !Habilitando os Logs de Nível de Privilégio de Autenticação do Usuário
    !DICA-04: esse recurso mostra no momento da autenticação qual é o nível de privilégio do usuário
    !OBSERVAÇÃO-10: esse recurso facilita a administração e o monitoramento dos equipamentos utilizados na rede
    !OBSERVAÇÃO-11: esse recurso não está disponível no Switch Layer 2 2960
    logging userinfo
    
    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

  !Salvando as configurações da memória RAM para a memória NVRAM
  write
```

## SEGUNDA ETAPA: Visualizando as configurações do Syslog nos Switches e Router

```python
!Visualizando as configurações da memória RAM
show running-config | include log

!Comandos para verificar do envio das Mensagens para o Syslog Server

!DICA-05: o comando Debug é muito utilizado para analisar informações detalhadas de recursos ou comandos

!OBSERVAÇÃO-12: muito cuidado quando habilitar o Debug, não esqueça de desabilitar no final da análise,
!esse recurso consome muita memória RAM e processamento CPU do hardware causando lentidão ou travamento.

!Habilitando o Debug do ICMP no Switch Layer 3 ou Router
debug ip icmp

!Pingando o servidor remoto para testar os Logs
ping 192.168.1.1

!Parando a análise do Debug do ICMP
no debug ip icmp
```