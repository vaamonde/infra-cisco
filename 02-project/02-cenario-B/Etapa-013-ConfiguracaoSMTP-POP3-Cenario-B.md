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
#01_ Configurações do Serviço de SMTP e POP3 Server no Cisco Packet Tracer;<br>
#02_ Configurações do Clientes de SMTP e POP3 no Cisco Packet Tracer.<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: *Configuração do SMTP e POP3 Server do Cenário B do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

O **SMTP (Simple Mail Transfer Protocol)** é o protocolo padrão de envio de mensagens de correio eletrônico (e-mail) através da Internet entre dois dispositivos computacionais (computadores, smartphone, etc), definido na RFC 821.

O protocolo padrão utilizado pelo SMTP Server é o *TCP (Transmission Control Protocol)* na porta padrão: *25*

**OBSERVAÇÃO-01:** desde: *01/01/2013* o CGI.br (Comitê Gestor da Internet) solicitou o bloqueio do envio de e-mails utilizando a porta padrão: **25**

**OBSERVAÇÃO-02:** atualmente a porta utilizada pelo SMTP é a: **TCP 587**, essa mudança tem o foco na diminuição de *SPAM*

**DICA-01:** a porta *587 utiliza TLS* (segurança) já a porta *465 utiliza SSL* (segurança) mais foi considera depreciada (desuso)

**O POP3 (Post Office Protocol)** é um protocolo utilizado no acesso remoto a um servidor de correio eletrônico (e-mail), definido no *RFC-1939*, que permite que todas as mensagens contidas em uma caixa de correio eletrônico possam ser transferidas sequencialmente para um software cliente de e-mail em outro dispositivo.

O protocolo padrão utilizado pelo POP3 é o *TCP (Transmission Control Protocol)* na porta padrão: *110*

**DICA-02:** a porta: *TCP 995 utiliza TLS/SSL* (segurança) ela também é conhecida como *POP3S*.

**O IMAP (Internet Message Access Protocol)** é um protocolo de gerenciamento de correio eletrônico (e-mail). O mais interessante é que as mensagens ficam armazenadas no servidor de hospedagem de e-mail. Trabalhando com sincronismo entre a caixa postal é o cliente de e-mail.

O protocolo padrão utilizado pelo IMAP é o *TCP (Transmission Control Protocol)* na porta padrão: *143*

**DICA-03:** a porta: *TCP 993 utiliza TLS/SSL* (segurança) ela também é conhecida como *IMAPS*

**O MAPI (Messaging API)** é um protocolo proprietário desenvolvido pela Microsoft. Ele é usado como interface de comunicação entre as aplicações e o servidor Microsoft Exchange.

O protocolo MAPI utiliza um conjunto de protocolos *TCP (Transmission Control Protocol)* nas portas: *80 (HTTP), 443 (HTTPS), 143 (IMAP), 993 (IMAPS), 110 (POP3), 995 (POP3S) é 587 (SMTP)*

## PRIMEIRA ETAPA: Configurações do Serviço de SMTP e POP3 Server no Cisco Packet Tracer

**OBSERVAÇÃO-03:** por padrão o Serviço de SMTP e POP3 no Cisco Packet Tracer está ligado

**DICA-04:** em servidores de e-mail geralmente no Servidor de DNS é feito a criação do Registro MX (Mail Exchanger Record)

**DICA-05:** nesse servidor também é criado os arquivos do Tipo TXT com informações de Black List (Sender Policy Framework)

**OBSERVAÇÃO-04:** esses recursos de e-mail avançado são limitados no Cisco Packet Tracer. 

```python
!Habilitando o Serviço do SMTP Server no Servidor 04
Server-04
  Services
    SMTP

SMTP Service        On
POP3 Service        On
Domain Name         SEU_DOMÍNIO.BR          SET
User Setup          User: robsonvaamonde    Password: 123456    (+)     Email: robsonvaamonde@SEU_DOMÍNIO.INTRA
                    User: theodorhinz       Password: 123456    (+)     Email: theodorhinz@SEU_DOMÍNIO.INTRA
                    User: leandroramos      Password: 123456    (+)     Email: leandroramos@SEU_DOMÍNIO.INTRA
                    User: josedeassis       Password: 123456    (+)     Email: josedeassis@SEU_DOMÍNIO.INTRA
                    User: jeffersoncosta    Password: 123456    (+)     Email: jeffersoncosta@SEU_DOMÍNIO.INTRA
                    User: rogeriosampaio    Password: 123456    (+)     Email: rogeriosampaio@SEU_DOMÍNIO.INTRA
                    User: sirlenesanches    Password: 123456    (+)     Email: sirlenesanches@SEU_DOMÍNIO.INTRA
                    User: denisnovais       Password: 123456    (+)     Email: denisnovais@SEU_DOMÍNIO.INTRA
                    User: talliswallef      Password: 123456    (+)     Email: talliswallef@SEU_DOMÍNIO.INTRA
                    User: viniciuscesar     Password: 123456    (+)     Email: viniciuscesar@SEU_DOMÍNIO.INTRA
                    User: edilsonjesus      Password: 123456    (+)     Email: edilsonjesus@SEU_DOMÍNIO.INTRA
                    User: kellycristina     Password: 123456    (+)     Email: kellycristina@SEU_DOMÍNIO.INTRA
```

## SEGUNDA ETAPA: Configurações do Clientes de SMTP e POP3 no Cisco Packet Tracer

**DICA-06:** o principal cliente de e-mail utilizado hoje em dia no mercado corporativo é o: *Microsoft Outlook*

**OBSERVAÇÃO-05:** existe outros clientes de e-mail como: *Thunderbid, Evolution, SeaMonkey, eM Client, etc.*

**OBSERVAÇÃO-06:** não confunda Cliente de Email com Webmail, nesse caso o acesso e feito via Navegador.

```bash
#Testando as resoluções de nome do SMTP e POP3
C:\> nslookup smtp.SEU_DOMÍNIO.BR
C:\> nsllokup pop3.SEU_DOMÍNIO.BR

#Configurando o cliente de email
Email
  Configure Mail
  Your Name               NOME DO SEU USUÁRIO
  Email Address           seu_usuário@SEU_DOMÍNIO.BR

  Server Information
  Incoming Mail Server    pop3.SEU_DOMÍNIO.BR
  Outgoing Mail Server    smtp.SEU_DOMÍNIO.BR

  Logon Information
  User Name               seu_usuário
  Password                sua_senha
<Save>

#Enviando um email de teste para a sua própria conta
Mail Browser
  Mails
    Compose
      To: seu_usuário@SEU_DOMÍNIO.BR
      Subject: Teste de Envio de Email
      Body: Teste de Envio de Email
    <Send>

#Recebendo o Email de teste no seu Mail Box
Mail Browser
  Receive
```
