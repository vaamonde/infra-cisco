#Autor: Robson Vaamonde<br>
#Procedimentos em TI: http://procedimentosemti.com.br<br>
#Bora para Prática: http://boraparapratica.com.br<br>
#Robson Vaamonde: http://vaamonde.com.br<br>
#Facebook Procedimentos em TI: https://www.facebook.com/ProcedimentosEmTi<br>
#Facebook Bora para Prática: https://www.facebook.com/BoraParaPratica<br>
#Instagram Procedimentos em TI: https://www.instagram.com/procedimentoem<br>
#YouTUBE Bora Para Prática: https://www.youtube.com/boraparapratica<br>
#Data de criação: 16/09/2024<br>
#Data de atualização: 27/03/2025<br>
#Versão: 0.05<br>
#Testado e homologado no Linux Mint 22 Wilma e 22.1 Xia x64<br>
#Testado e homologado o Cisco Packet Tracer 8.2.x x64<br>
#Testado e homologado o Microsoft Visual Studio Code VSCode no Linux Mint 22 Wilma e 22.1 Xia<br>

Conteúdo estudado nessa instalação:<br>
#01_ Verificando as Informações do Sistema Operacional Linux Mint<br>
#02_ Atualização do Sistema Operacional Linux Mint<br>
#03_ Instalando as Dependências do VSCode no Linux Mint<br>
#04_ Baixando o Microsoft Visual Studio Code VSCode para o Linux<br>
#05_ Instalando o VSCode utilizando o Gdebi-Gtk no Linux Mint<br>
#06_ Verificando o novo repositório do VSCode no MintUpdate<br>
#07_ Iniciando o VSCode no Linux Mint<br>
#08_ Configurando o VSCode como Aplicativo de Preferência no Linux Mint<br>
#09_ Adicionando o VSCode nas Lista de Abrir Com no Linux Mint<br>
#10_ Instalando e Configurando as Principais Extensões do Cisco no VSCode<br>
#11_ Configurações básicas do VSCode para funcionar perfeitamente no Linux Mint<br>
#12_ Trabalhando com as Extensões do Cisco no VSCode no Linux Mint<br>

**OBSERVAÇÃO IMPORTANTE:** COMENTAR NO VÍDEO DO INSTALAÇÃO DO VSCODE SE VOCÊ CONSEGUIU FAZER A INSTALAÇÃO COM A SEGUINTE FRASE: *Instalação do VSCODE Cisco realizado com sucesso!!! #BoraParaPrática*

#boraparapratica #boraparaprática #vaamonde #robsonvaamonde #procedimentosemti #cisco #infracisco #desafiovaamonde #desafioboraparapratica #desafiocisco #desafioinfracisco

Site Oficial do Visual Studio Code: https://code.visualstudio.com/<br>
Site Oficial do Visual Studio Code Web: https://vscode.dev/<br>
Link do Marketplace: https://marketplace.visualstudio.com/VSCode

**O QUE É E PARA QUE SERVER O VSCODE:** O Visual Studio Code é um editor de código-fonte desenvolvido pela Microsoft para Windows, Linux e macOS. Ele inclui suporte para depuração, controle de versionamento Git incorporado, realce de sintaxe, complementação inteligente de código, snippets e refatoração de código.

[![VScode Git Github](http://img.youtube.com/vi/f9ZqzzhSzcA/0.jpg)](https://www.youtube.com/watch?v=f9ZqzzhSzcA "VScode Git Github")

Link da vídeo aula: https://www.youtube.com/watch?v=f9ZqzzhSzcA

**OBSERVAÇÃO IMPORTANTE:** OS VÍDEOS DE INSTALAÇÃO E CONFIGURAÇÃO DO MICROSOFT VISUAL STUDIO CODE VSCODE, GIT E GITHUB SÃO DO CURSO GRATUITO DE PYTHON 3 DO PROJETO BORA PARA PRÁTICA, HOJE O CISCO SUPORTA PROGRAMAÇÃO EM PYTHON, RECOMENDO SEGUIR OS PROCEDIMENTOS ABAIXO PARA A CORRETA INSTALAÇÃO DESSAS FERRAMENTAS QUE SERÃO UTILIZADAS NESSE CURSO

[![Instalação Python 3](http://img.youtube.com/vi/klIKuVGRHmM/0.jpg)](https://www.youtube.com/watch?v=klIKuVGRHmM "Instalação Python 3")

Link da vídeo aula: https://www.youtube.com/watch?v=klIKuVGRHmM

Link da documentação: https://github.com/vaamonde/python3/blob/main/01-introduction/01-install.md

[![Instalação Git](http://img.youtube.com/vi/VBxmsmPK60s/0.jpg)](https://www.youtube.com/watch?v=VBxmsmPK60s "Instalação Git")

Link da vídeo aula: https://www.youtube.com/watch?v=VBxmsmPK60s

Link da documentação: https://github.com/vaamonde/python3/blob/main/01-introduction/02-git-gthub.md

## 01_ Verificando as Informações do Sistema Operacional Linux Mint<br>
```bash
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#OBSERVAÇÃO IMPORTANTE: Linux Mint 22.x é derivado do Ubuntu Desktop 24.04.x Noble Numbat

#verificando as versões e codinome do sistema operacional
sudo cat /etc/os-release
sudo cat /etc/lsb-release

#modo gráfico para verificar as informações de sistema operacional e hardware
Menu
  Informações do Sistema
```

## 02_ Atualização do Sistema Operacional Linux Mint<br>
```bash
#atualizando o sistema operacional via MintUpdate (Recomendado)
A) Atualização do sistema utilizando o MintUpdate;
B) Atualização do sistema utilizando o Apt;

#atualizando o sistema operacional via Terminal
#atalho para acessar o Terminal
Terminal: Ctrl + Alt + T

#recomendo utilizando o comando: apt - o comando: apt-get é considerado obsoleto
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean
sudo apt clean
```

## 03_ Instalando as Dependências do VSCode no Linux Mint<br>
```bash
#instalando as dependências do VSCode no Linux Mint 22.x
sudo apt install vim git python3 python3-pip cloc
```

## 04_ Baixando o Microsoft Visual Studio Code VSCode para o Linux<br>
```bash
#link de download oficial do VSCode
Link de download: https://code.visualstudio.com/download
  Versão: .deb (Debian, Ubuntu 64 Bits)
    Salvar aquivo
```

## 05_ Instalando o VSCode utilizando o Gdebi-Gtk no Linux Mint<br>
```bash
#instalando em modo gráfico (mais fácil) o VSCode
Arquivos
  Download
    Clique duas vezes no instalar: code_1.*_amd64.deb
      <Instalar Pacote>
        Digite sua senha e clique em: <Autenticar>
        (ON) Add Microsoft apt repository for Visual Studio Code? <Next>
    <Fechar>
```

## 06_ Verificando o novo repositório do VSCode no MintUpdate<br>
```bash
#verificando o novo repositório no Linux Mint
Menu
  MintUpdate
    Editar
      Fontes de Programas
        (Digite a senha do seu usuário)
          Repositórios Adicionais
            Habilitado: Microsoft / Stable - code
          Chaves de Autenticação
            Microsoft (Release signing)
      <Fechar>
  <Fechar>
```

## 07_ Iniciando o VSCode no Linux Mint<br>
```bash
#iniciando o VSCode no Linux Mint
Menu
  Busca Indexada
    vscode
      Dark Theme
      Notifications: Pacote PT-BR
      Disable: Mostrar página inicial na inicialização
```

## 08_ Configurando o VSCode como Aplicativo de Preferência no Linux Mint<br>
```bash
#configuração básica do VSCode no Linux Mint
Menu
  Aplicativos Preferenciais
    Escritório
      Código Fonte: Outro aplicativo
        Visual Studio Code <Selecionar>
    Sistema
      Texto Puro: Outro aplicativo
        Visual Studio Code <Selecionar>
  <Fechar>
```

## 09_ Adicionando o VSCode nas Lista de Abrir Com no Linux Mint<br>
```bash
#adicionando o VSCode na lista de Abrir com
Gerenciador de Arquivos
  Pasta Pessoal
    Selecionar: Documentos
      Clicar com o botão direito do mouse no diretório: Documentos e selecionar: Abrir com
        Outro aplicativo
          Visual Studio Code
        <Adicionar à lista>
      <OK>
```

## 10_ Instalando e Configurando as Principais Extensões do Cisco no VSCode<br>
```bash
#Instalação das Extensões Básicas do VSCode
Portuguese (Brazil) Language Pack for Visual Studio Code
  (Sem necessidade de configuração)

#instalação e configuração da extensão do Corretor Ortográfico PT-BR e US
Brazilian Portuguese - Code Spell Checker (Corretor Ortográfico de Código)
Manter selecionado a extensão: Brazilian Portuguese - Code Spell Checker
  Pressionar F1
    Show Spell Checker Configuration Info (OPÇÃO FOI DESATIVADA NA NOVA VERSÃO)
      User
        Language
          English (en_us)
          Portuguese (pt_br)
          Portuguese - Brazil (pt-br)
            File Types and Programming Languages
              shellscript, python, markdown, etc...

Translator for VsCode
  (Sem necessidade de configuração)

Code Spell Checker
  (Sem necessidade de configuração)

Cisco IOS Syntax
  (Sem necessidade de configuração)

Cisco Config Highlight
  (Sem necessidade de configuração)

Cisco IOS-XR Syntax
  (Sem necessidade de configuração)
```

## 11_ Configurações básicas do VSCode para funcionar perfeitamente no Linux Mint<br>
```bash
#configurações básicas do VSCode para funcionar no Linux Mint
Gerenciar
  Configurações
    Code Spell Checker
      C Spell: Enabled Language Ids: (OPÇÃO FOI DESATIVADA NA NOVA VERSÃO)
        Adicionar Item: shellscript (OPÇÃO FOI DESATIVADA NA NOVA VERSÃO)
      C Spell: Language: en,en-US,pt,pt-BR
      C Spell: Max Duplicate Problems: 500000
      C Spell: Max Number Of Problems: 500000
    Editor
      Editor: Tab Size: 2
      Editor: Detect Indentation: False (Off)
      Editor: Insert Spaces: True (On)
      Render Whitespace: All
    Files
      Files: Eol: \n (LF)
```

## 12_ Trabalhando com as Extensões do Cisco no VSCode no Linux Mint<br>
```bash
01) Cisco IOS Syntax
    Salvar os arquivos com a extensão: ios

02) Cisco Config Highlight
    Salvar os arquivos com as extensões: .cisco ou .config

03) Cisco IOS-XR Syntax
    Salvar os arquivos com a extensão: .xr ou .iosxr
```