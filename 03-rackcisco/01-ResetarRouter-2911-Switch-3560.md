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
Data de atualização: 09/03/2025<br>
Versão: 0.02<br>
Testado e homologado no Cisco Packet Tracer 8.2.x e Rack Cisco SW-3560 e RT-2911

## PRIMEIRA ETAPA: Reset do Switch 2960 ou 3560 (Configurações de Fábrica)

**OBSERVAÇÃO IMPORTANTE: Utilizar o PuTTY para acessar o Switch utilizando o Cabo Console.**

01. Deixar o Switch Cisco Catalyst Layer 3 3560 inicializar normalmente (esse processo demora cerca de 5 minutos)

02. Após a inicialização do Switch 3560, pressionar e segurar o Botão: **Mode** por aproximadamente: **15/20 segundos** até os LED's piscarem em: **Ambar (Laranja)** e o Switch entrar no modo de ROMmon e ser reinicializado, no Terminal será mostrado a mensagem que o equipamento será reiniciado.

03. Após a reinicialização do Switch 3560 será apresentado o **Wizard de Configuração**, digite: *no* <Enter>

```python
         --- System Configuration Dialog ---

Would you like to enter the initial configuration dialog? [yes/no]: no

Press RETURN to get started!

Switch>
```

04. Limpando as configurações residuais dos outros grupos do Switch 3560.

```python
Switch>

!Acessar o modo privilegiado de comandos 
Switch> enable

  !Verificando o conteúdo da Flash
  Switch# dir flash:

  !Remover o banco de dados de VLAN da Flash (SE EXISTIR): 
  Switch# delete flash:vlan.dat

  !Remover os backups anteriores das turmas (SE EXISTIR): 
  Switch# delete flash:startup-config

  !Reiniciar o Switch para testar as configurações
  Switch# reload
```

## OBSERVAÇÃO IMPORTANTE: Caso o Switch não volte para o estado de fábrica, será necessário utilizar os procedimentos abaixo: (SÓ USAR ESSA OPÇÃO SE FOR REALMENTE NECESSÁRIO, NÃO EXECUTAR ESSES PROCEDIMENTOS NOS EQUIPAMENTOS ANTES DE INFORMAR AO DOCENTE)

```bash
A) Pressionar o botão MODE até o switch reinicializar;
B) Na tela de inicialização, na mensagem de hardware, pressionar o botão MODE para abortar o carregamento do IOS;
C) Digitar o comando: flash_init;
D) Listar o conteúdo da Flash: dir flash:
E) Renomear o arquivo: rename flash:config.text flash:config.old
F) Inicializar o sistema: boot
G) Limpar o Startup-config: erase startup-config
H) Limpar as VLAN: delete flash:vlan.dat
I) Reinicializar o Switch: reload
```

## SEGUNDA ETAPA: Reset do Roteador (Router) 2911

**OBSERVAÇÃO IMPORTANTE: Utilizar o PuTTY para acessar o Router utilizando o Cabo Console.**

01. Parar a inicialização do IOS do Router Cisco 2911 utilizando as teclas de atalho: **Ctrl + Break** (No PuTTY utilizar o Botão direito do Mouse na Barra de Título e selecionar as opções: **Send Command: Break**)

**CUIDADO!!!!!! com a Chave de Registro que você vai digitar no ROMmon (veja os tópicos das Observações: 3 e 4)**

02. Nas configurações do Cisco ROMmon digite a chave em hexadecimal: confreg 0x2142 <Enter>

**OBSERVAÇÃO-1:** Quando configurado com esse valor (0x2142), o roteador ignora a NVRAM durante a inicialização, ou seja, não carrega a configuração armazenada (startup-config).  

```python
rommon 1> confreg 0x2142 
```

03. Após a mudança da chave, digite: reset <Enter> para reiniciar o Router Cisco 2911.

```python
rommon 2> reset
```

04. O Router Cisco 2911 vai inicializar sem ler o arquivo de configuração: **startup-config** da NVRAM.

05. Limpando as configurações do Router Cisco 2911 e voltando a ler o arquivo de configuração: *startup-config* da NVRAM.

**OBSERVAÇÃO-2:** Quando o Configuration Register está definido como 0x2102, o roteador segue este comportamento ao iniciar: Carrega a configuração salva na NVRAM (startup-config), Procura o sistema operacional (IOS) na memória flash e o executa e Permite entrar no modo ROMMON (Ctrl + Break) caso necessário.

```python
Router>

!Acessar o modo privilegiado de comandos 
Router> enable

  !Limpando as configuração da NVRAM
  Router# erase startup-config

  !Verificando o conteúdo da Flash
  Router# dir flash:

  !Remover os backups anteriores das turmas (SE EXISTIR): 
  Router# delete flash:startup-config

  !Entrar no modo de configuração global
  Router# configure terminal

    !Alterar o registro de inicialização do Router
    Router (config)# config-register 0x2102 

    !Saindo de dos os modos de configuração
    Router (config)# end

  !Salvando as configurações da RAM para a NVRAM
  Router# copy running-config startup-config 

  !Reiniciar o Router para testar as configurações
  Router# reload

!Após reiniciar o Router Cisco 2911 verifique a chave de registro
!Valor está na última linha referente ao confreg 0x2102
Router> enable

  !Visualizando a configuração de registro do Cisco IOS
  Router# show version
    Configuration register is 0x2102
```

**OBSERVAÇÃO-03: caso você digite chaves diferentes no ROMmon o sistema pode inicializar com caracteres estranhos, isso está associado a velocidade da porta console (Padrão 9600bps), será necessário fazer os testes mudando as velocidades de conexão da porta console no PuTTY para: 1200, 2400, 4800, 9600, 19200, 38400, 57600 e 115200.** 

**OBSERVAÇÃO-04: para corrigir essa falha será necessário alterar novamente a chave de registro para:**

```bash
A) Acessar o modo Exec Privilegiado: enable <Enter>
B) Mudar o registro de inicialização: config-register 0x2102 <Enter>
D) Acessar a Linha Console: line console 0 <Enter>, 
D) Alterar a velocidade da Porta Console: speed 9600 <Enter>
E) Salvar as configurações: copy running-config startup-config <Enter>
F) Reinicializar o router: reload <Enter>
G) Verificar a chave de registro: enable <Enter>, show version <Enter>
```