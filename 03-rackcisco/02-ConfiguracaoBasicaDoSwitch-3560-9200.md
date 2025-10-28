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
Data de atualização: 28/10/2025<br>
Versão: 0.05<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560, SW-9200L, RT-2911 e RT-8200L

## PRIMEIRA ETAPA: Configuração Base do Switch Cisco Catalyst Layer-3 3560 ou Multilayer 9200L

```python
!Acessando o modo Exec Privilegiado
enable

  !Configuração de data/hora em inglês, abreviado ou completo
  !Exemplo: October ou Oct
  !Primeiro Hora no formato: 00:00:00 (hora:minutos:segundos) depois Data no formato: Dia Mês (Completo ou Abreviado) Ano Completo
  clock set ??:??:?? ?? ???????? ????

  !Acessar modo de Configuração Global
  configure terminal

    !Configuração do nome do Switch 3560 ou 9200L
    !Obrigatório para a configuração do SSH e demais serviços de redes
    !Mudar o nome do Switch 3560 ou 9200L para cada equipamento do seu grupo
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 68 
    !(#03_ Nome dos Switches, Routers e Access Point de Cada Grupo:)
    hostname sw-g???

    !Habilitar o serviço de Criptografia de Senhas do Tipo-7 Password 
    service password-encryption

    !Habilitar o serviço de marcação de Data/Hora detalhado nos Logs
    service timestamps log datetime msec

    !Habilitando o serviço de marcação de Data/Hora detalhado nos Logs do Debug
    service timestamps debug datetime msec

    !Verificar tentativas de conexão simultâneas, fazer o bloqueio de um
    !período determinado de tempo, proteção contra Brute Force
    login block-for 120 attempts 4 within 60

    !Desativar a resolução de nomes de domínio
    no ip domain-lookup

    !Configuração do Banner da mensagem do dia
    !Desafio: Buscar na Internet imagens ASCII para o Banner
    !Dica de site: https://manytools.org/hacker-tools/ascii-banner/
    banner motd #AVISO: acesso autorizado somente a funcionarios#

    !Habilitar a senha do Tipo-5 secret para o modo enable privilegiado
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
    !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
    enable secret ????

    !Criação dos usuários, senhas do Tipo-5 e privilégios diferenciados
    !Consultar Planilha de Nomes de Usuários
    !OBSERVAÇÃO: Caso o grupo tenha menos integrantes, desconsiderar a criação de 04 (quatro) usuários
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
    !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
    username ???nome_do_primeiro_integrante??? privilege 15 secret ????
    username ???nome_do_segundo_integrante??? privilege 15 secret ????
    username ???nome_do_terceiro_integrante??? privilege 15 secret ????
    username ???nome_do_quarto_integrante??? privilege 15 secret ????

    !Criação do usuário VAAMONDE para administração do equipamento
    username vaamonde privilege 15 secret 123@Tatuape

    !Desativando os Serviços de Descobertas de equipamentos na rede
    !OBSERVAÇÃO: por padrão os serviços de descobertas de equipamentos estão habilitados
    !globalmente no Switch e Router Cisco, desabilitar o CDP ou LLDP garante a segurança
    !de informações de equipamentos na rede.
    no cdp run
    no lldp run

    !Acessando a linha console
    line console 0

      !Habilitando senha do Tipo-7 Password
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
      !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
      password ????

      !Forçando fazer login com usuário e senha
      login local

      !Sincronizando os logs na tela
      logging synchronous

      !Habilitando o tempo de inatividade do console
      exec-timeout 5 30

      !Saindo de todos os níveis
      end

  !Salvando as configurações
  copy running-config startup-config
```

## SEGUNDA ETAPA: Verificando as Configurações do Switch Cisco Catalyst 3560 ou Multilayer 9200L

```python
!Visualizando a Data e Hora do Switch ou Router
show clock

!Visualizando as Configurações do Running-Config (RAM)
!OBSERVAÇÃO: ÚNICA LINHA QUE NÃO APARECE NAS CONFIGURAÇÃO É A: crypto key generate rsa
show running-config

!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Line Console 0
show running-config | section include con 0

!Visualizando os Usuários Conectados no Switch
!OBSERVAÇÃO: ESSA OPÇÃO VAI MOSTRAR O USUÁRIO LOGADO NO CONSOLE: con 0 OU NO VTY: vty 0
show users

!Visualizando os Logs de Evento do Switch e Router
show logging
```

## TERCEIRA ETAPA: Testando a autenticação dos Usuários do Switch Cisco Catalyst 3560 ou Multilayer 9200L

```python
!Saindo do modo EXEC privilegiado
disable

!Saindo da conexão do Cabo Console
exit
```