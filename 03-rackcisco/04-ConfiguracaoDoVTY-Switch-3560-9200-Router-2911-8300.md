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
Data de atualização: 28/10/2024<br>
Versão: 0.04<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560, SW-9200L, RT-2911 e RT-8200L

## PRIMEIRA ETAPA: Configuração das Linhas Virtuais do Switch Cisco Catalyst 3560 ou 9200

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Acessando as linhas virtuais
    line vty 0 4

      !Habilitando senha do tipo Password Tipo-7
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
      !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
      password ????

      !Forçando fazer login com usuário e senha local
      login local 

      !Sincronizando os logs na tela
      logging synchronous

      !Habilitando o tempo de inatividade do terminal
      exec-timeout 5 30

      !Configuração do tipo de protocolo de transporte de entrada
      transport input ssh

      !Saindo de todos os níveis
      end

  !Salvando as configurações
  copy running-config startup-config
```

## SEGUNDA ETAPA: Configuração das Linhas Virtuais do Router Cisco 2911 ou 8300

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Acessando as linhas virtuais
    line vty 0 4

      !Habilitando senha do tipo Password Tipo-7
      !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
      !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
      password ????

      !Forçando fazer login com usuário e senha local
      login local 

      !Sincronizando os logs na tela
      logging synchronous

      !Habilitando o tempo de inatividade do terminal
      exec-timeout 5 30

      !Configuração do tipo de protocolo de transporte de entrada
      transport input ssh

      !Saindo de todos os níveis
      end

  !Salvando as configurações
  copy running-config startup-config
```

## TERCEIRA ETAPA: Verificando as Configurações do Switch 3560, 9200 e Router 2911 8300.

```python
!Visualizando as Configurações do Running-Config (RAM)
!OBSERVAÇÃO: ÚNICA LINHA QUE NÃO APARECE NAS CONFIGURAÇÃO É A: crypto key generate rsa
show running-config

!Fazendo um Filtro na Visualização do Running-Config somente da Sessão Line VTY
show running-config | section include line vty
```