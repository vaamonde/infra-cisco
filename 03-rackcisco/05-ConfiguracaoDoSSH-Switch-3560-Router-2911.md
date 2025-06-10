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
Data de atualização: 10/06/2024<br>
Versão: 0.02<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## PRIMEIRA ETAPA: Configuração do SSH Server no Switch Cisco Catalyst 3560 

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Configuração do nome de domínio, obrigatório para a configuração do SSH
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
    !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
    ip domain-name ????

    !Criação da chave de criptografia e habilitação do serviço de SSH
    !Utilizar módulo de criptografia de 1024 bits
    crypto key generate rsa general-keys modulus 1024

    !Habilitando a versão 2 do serviço do SSH
    ip ssh version 2

    !Habilitar o tempo de inatividade para novas conexões do SSH
    ip ssh time-out 60

    !Habilitar o número máximo de tentativas de conexão do SSH
    ip ssh authentication-retries 2

    !Saindo de todos os níveis
    end

  !Salvando as configurações
  copy running-config startup-config
```

## SEGUNDA ETAPA: Configuração do SSH Server no Router Cisco 2911 

```python
!Acessando o modo Exec Privilegiado
enable

  !Acessar modo de configuração global
  configure terminal

    !Configuração do nome de domínio, obrigatório para a configuração do SSH
    !OBSERVAÇÃO IMPORTANTE: veja o arquivo 00-DocumentacaoDaRede.txt a partir da linha: 90 
    !(#02_ Usuário e Senha padrão dos Switches e Routers Cisco de cada Grupo:)
    ip domain-name ????

    !Criação da chave de criptografia e habilitação do serviço de SSH
    !Utilizar módulo de criptografia de 1024 bits
    crypto key generate rsa general-keys modulus 1024

    !Habilitando a versão 2 do serviço do SSH
    ip ssh version 2

    !Habilitar o tempo de inatividade para novas conexões do SSH
    ip ssh time-out 60

    !Habilitar o número máximo de tentativas de conexão do SSH
    ip ssh authentication-retries 2

    !Saindo de todos os níveis
    end

  !Salvando as configurações
  copy running-config startup-config
```

## TERCEIRA ETAPA: Verificando as Configurações do Switch 3560 e Router 2911.

```python
!Visualizando as Configurações do Running-Config (RAM)
show running-config

!Fazendo um Filtro na Visualização do Running-Config somente da Sessão IP SSH
show running-config | section include ip ssh

!Visualizando as configurações do SSH Server
show ip ssh

!Visualizando das chaves públicas RSA do SSH Server
show crypto key mypubkey rsa

!Visualizando as conexões ativas do SSH Server
show ssh (só vai funcionar quando você se conectar remoto no Router)

!Visualizando as conexões remotas estabelecidas no Router ou Switch
show users (só vai funcionar quando você se conectar remoto no Router)
```