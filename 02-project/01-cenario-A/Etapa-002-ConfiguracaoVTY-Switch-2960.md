#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 16/09/2024<br>
#Data de atualização: 22/11/2024<br>
#Versão: 0.06<br>
#Testado e homologado no Linux Mint 22 Wilma x64<br>
#Testado e homologado o Cisco Packet Tracer 8.2.x x64 e Rack Cisco SW-3560 e RT-2911

Conteúdo estudado nessa configuração:<br>
#01_ PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.<br>
#02_ SEGUNDA ETAPA: Configuração das Linhas Virtuais (VTY) do Cisco IOS.<br>
#03_ TERCEIRA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960.<br>

OBSERVAÇÃO IMPORTANTE: COMENTAR NO VÍDEO DO CONFIGURAÇÃO DO CISCO PACKET TRACER SE VOCÊ CONSEGUIU FAZER A CONFIGURAÇÃO COM A SEGUINTE FRASE: Configuração do VTY no Switch 2960 do Cisco Packet Tracer realizado com sucesso!!! #BoraParaPrática

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

## INFORMAÇÕES IMPORTANTES SOBRE ESSA DOCUMENTAÇÃO:

A) **ACRÉSCIMO:** informações ou comandos que não estava no script original e nem comentado no vídeo, algo importante para o cenário ou dicas de alunos;<br>
B) **DESAFIO:** desafio proposto para o aluno, com o objetivo de estimular o raciocínio lógico para a resolução de problemas de rede ou mudanças nas configurações;<br>
C) **DICA:** informações importantes da tecnologia ou da prova de certificação, dica para configurar ou lembrar os recursos para sua configuração no exame;<br>
D) **ERRATA:** correções dos scripts, correções de falas, correções de configurações, etc...;<br>
E) **EXEMPLO:** exemplos de comandos ou configurações das opções de DICAS ou OBSERVAÇÃO;<br>
F) **IMPORTANTE:** informações importantes da tecnologia ou da configuração, com foco em adicionar informações detalhadas da tecnologia ou da certificação;<br>
G) **OBSERVAÇÃO:** informações relevantes da tecnologia ou da configuração, com foco em adicionar informações extras da tecnologia ou da certificação.

[![Config VTY 2960](http://img.youtube.com/vi/G/0.jpg)]( "Config VTY 2960")

Link da vídeo aula: 

## PRIMEIRA ETAPA: Acessando o Modo de Configuração Global do Switch Cisco Catalyst 2960.

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

## SEGUNDA ETAPA: Configuração das Linhas Virtuais (VTY) do Cisco IOS.

01. Acessando as Linhas (Lines) Virtuais de Acesso remoto do Switch no Cisco IOS.

**DICA-01:** por padrão o Switch Cisco possui *16 (0 até 15)* linhas virtuais de acesso remoto.

**OBSERVAÇÃO-01:** as linhas virtuais são utilizadas para acessar remotamente o terminal do Switch ou Router para facilitar a sua configuração ou administração em locais onde o acesso físico e complicado ou unidades remotas, **exemplo:** *Switch em outro Andar do Prédio, Switch em outra Unidade da Empresa, Switch Remotos em Cidades/Estados diferentes*.

**OBSERVAÇÃO-02:** linhas virtuais não são utilizadas para monitoramento, para isso usamos o Protocolo SNMP (Simple Network Management Protocol), Netflow (Network Traffic Analyzer), Syslog (System Log Analyzer), etc... com as configurações do SVI (Switch Virtual Interface).

**DICA-02:** não é recomendado habilitar poucas linhas ou todas as linhas virtuais no Cisco IOS.

**OBSERVAÇÃO-03:** as linhas virtuais é bem parecida com a linha console, a diferença é que o acesso e feito remotamente utilizando Protocolo TCP (Transmission Control Protocol) e Endereçamento IPv4 ou IPv6.

**DICA-03:** por padrão as linhas virtuais estão desabilitadas no Cisco IOS, elas dependem da configuração do SVI (Switch Virtual Interface) para funcionar.
```bash
sw-01(config)# line vty 0 4
```

a) Forçando fazer login local utilizando os usuários e senhas locais criados no Switch (usuários criados na etapa de configuração básica do Switch).

**DICA-04:** por padrão a configuração da Linha Virtual é não permitir nenhuma conexão, se você utilizar a opção do comando: *login* o acesso será feito sem autenticação, sendo necessário no mínimo configurar a opção do comando: *password*.
```bash
sw-01(config-line)# login local
```

b) Habilitando a senha de acesso do Tipo-7 Password (senha fraca).

**DICA-05:** igual na configuração da Line Console, essa regra só irá funcionar se não existir usuários no Switch e se você não configurou a opção: login local, deixando apenas a opção: local.
```bash
sw-01(config-line)# password pti@2018
```

c) Habilitando o sincronismo das mensagens de Logs na tela do terminal do Cisco IOS.

**DICA-06:** essa configuração é fundamental na Line VTY, igual a Line Console o sincronismos dos Logs e comandos precisa ser configurado para facilitar a administração do Switch ou Router.
```bash
sw-01(config-line)# logging synchronous
```

05. Habilitando o tempo de inatividade de uso do linha virtual.

**DICA-07:** na Line Virtual a desconexão por falta de interatividade é obrigatória, esse opção minimizar as falhas de segurança de acesso Remoto não Autorizado ao Switch ou Router.
```bash
sw-01(config-line)# exec-timeout 5 30
```

06. Configuração do tipo de Protocolo de Transporte de entrada ou saída da linha virtual.

**DICA-08:** na linha virtual você pode controlar o tipo de acesso remoto de entrada ou saída.

**OBSERVAÇÃO-04:** existe vários protocolos de acesso remoto no Cisco IOS, os mais utilizados são: *Telnet (não seguro)* ou *SSH (seguro)*, por motivo de segurança, acesso remoto utilizando o protocolo Telnet não é mais recomendado e será descontinuado nas próximas versões do Cisco IOS.

**DICA-09:** existe várias opções de configuração do Protocolo de Transporte, a opção: *all* permite todos os protocolos de entrada ou saída, essa é a configuração padrão do Cisco IOS (não indicado deixar essa opção).

**EXEMPLO DE ENTRADA:** transport input {lat | mop | nasi | none | pad | rlogin | ssh | telnet | v120} 

**EXEMPLO DE SAÍDA:** transport output {lat | mop | nasi | none | pad | rlogin | ssh | telnet | v120}

**EXEMPLO DE PREFERÊNCIA:** transport preferred {lat | mop | nasi | none | pad | rlogin | ssh | telnet | v120}
```bash
sw-01(config-line)# transport input ssh
```

07. Saindo de todos os níveis e voltando para o modo EXEC Privilegiado.

**DICA-10:** lembre-se sempre de sair de todos os níveis para salvar as configurações.
```bash
sw-01(config-line)# end
```

08. Salvando as configurações da memória RAM (Running-Config) para a memória NVRAM (Startup-Config).

**DICA-11:** nunca esqueça de salvar as configurações.
```bash
sw-01# copy running-config startup-config
  Destination filename [startup-config]? <Enter>
  Building configuration...
  [OK]
sw-01#
```

09. Visualizando as configurações da memória RAM (Running-Config).

**DICA-12** após a configuração da Line Virtual verifique se tudo está configurado de forma correta utilizando os comandos: *show*.
```bash
!Visualizando as Configurações do Running-Config (RAM)
sw-01# show running-config

!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Line VTY
sw-01# show running-config | section include line vty
```

## TERCEIRA ETAPA: Automatizando a Configuração do Segundo Switch Cisco Catalyst 2960.

01. Utilizando o Visual Studio Code (VSCode) para automatizar as configurações do Cisco IOS.

**OBSERVAÇÃO-05:** recomendo sempre utilizar um *Editor de Texto Profissional* para criar os scripts e automatizar as tarefas de configuração do Cisco IOS, hoje em dia é indicado utilizar o Visual Studio Code (VSCode) junto com as Extensões: *Cisco IOS Syntax e Cisco Config Highlight* para facilitar essa configuração.

**DICA-13:** o caractere: *! (exclamação)* é utilizado como um recurso de *Comentário*, sua utilização server para comentar o código de automação do Cisco IOS ou para desativar um comando para não ser executado, *RECOMENDO FORTEMENTE DOCUMENTAR TODOS OS COMANDOS E PROCEDIMENTOS DE CONFIGURAÇÃO PARA FACILITAR O ENTENDIMENTO.*

**DICA-14:** para facilitar a leitura do código, recomendo utilizar o recurso de **Indentação de Código** usando a Tecla TAB (Tabulador/Tabulação) para cada nível que você está configurando o Cisco IOS, isso facilitada a análise de erros (Debug) do código.

01. Acessando o modo EXEC Privilegiado e o modo de Configuração Global de Comandos.
```bash
AVISO: acesso autorizado somente a funcionarios
User Access Verification
Username: robson
Password: pti@2018

sw-02> enable
Password: pti@2018

sw-02#
```
```python
!Acessando o modo de Configuração Global de comandos
configure terminal

  !Acessando as linhas virtuais de acesso remoto do Switch
  line vty 0 4

    !Forçando fazer login local utilizando usuário e senha locais do switch
    login local

    !Habilitando senha de acesso do Tipo-7 Password
    password pti@2018

    !Sincronizando as mensagens de logs na tela
    logging synchronous

    !Habilitando o tempo de inatividade de uso da linha virtual
    exec-timeout 5 30

    !Configuração do tipo de protocolo de transporte de entrada
    transport input ssh

    !Saindo de todos os níveis e voltando para o modo EXEC Privilegiado
    end

!Salvando as configurações da memória RAM para a memória NVRAM
!OBSERVAÇÃO IMPORTANTE: deixar uma linha em branco no final do script para
!salvar automaticamente o script na hora da execução, fazendo a função de
!<Enter> no final do script.
write

```