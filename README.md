# **Manual de instalacao**

Este documento tem como objetivo seguir os passos de instalação e configuração dos recursos necessários para automação de testes web utilizando o framework:
 - **Ruby**: Linguagem de programação para escrita dos scripts;
 - **Capybara**: Ferramenta de automação de testes escrito em ruby, que simula usuários reais interagindo com a aplicação. Ela “turbina” a automação de aplicações web usando o Selenium WebDriver. 
 - **Cucumber**: Ferramenta para executar os testes a partir do BDD;
 - **VSCode**: IDE para edição dos textos de desenvolvimento;
 - **CMDER**: Terminal para utilizar a linha de comando.

## **CMDER - Introdução e instalação**

No processo de instalação, configuração e desenvolvimento das automações, iremos utilizar a linha de comando muitas vezes, então como melhor alternativa, para não utilizarmos o prompt de comando (CMD),  é o CMDER.
O CMDER nada mais é do que um “terminal” para o Windows mais animado e de fácil entendimento, além de permitir rodar os comandos do Linux (cat, ls, rm, grep, mv, etc.)

Segue os passos de instalação:

1. Acesse o site: https://cmder.net/  e faça o download da versão FULL (recomendada porque já tem integração com o Git).
1. Descompacte o arquivo baixado em uma pasta/diretório de sua preferência. 
Exemplo: `C:\cmder`
1. Abra a pasta e execute o arquivo `cmder.exe`
![1.PNG](1.png)

> **Dica**
> Para facilitar, crie um atalho do arquivo cmder.exe na área de trabalho, isso evita ir sempre até o C: para abrir o CMDER.

## **Ruby - Introdução e instalação**

Ruby é uma linguagem programação muito boa para fins de automação de testes, de fácil compreensão e muito produtiva, por isso vamos utilizá-la. 

Segue os passos de instalação:

1. Acesse o site  rubyinstaller.org/downloads  e faça o download da **versão 2.6.5**
1. Instale o aplicativo normalmente após o fim do download;
1. Após a instalação o terminal irá abrir e pressione a tela ``Enter`` para prosseguir com a configuração do ambiente Ruby;

![2.PNG](2.PNG)
1. Depois de configurado, pressione a tela `Enter` para concluir.

### Ruby - Validar a instalação
1. Para validar a instalação correta do Ruby, abra o CMDER e execute o seguinte comando:
`$  ruby –v`

> **Observação**
> Caso o CMDER esteja aberto durante a instalação, feche-o e refaça o passo acima.

### Bundler - Gerenciador de Dependências

Bundler é o gerenciador de dependências para projetos Ruby.
1. Abra o CMDER e execute o comando:
`$ gem install bundler`

###Ruby - Desinstalação

Em casos de conflitos ou atualização da versão do Ruby, segue os passos para desinstalar:

1.  Pesquise no Menu Iniciar por "_Adicionar e remover programas_"
1.  Procure pela versão do Ruby instalada na sua maquina,  exemplo: `Ruby 2.6.4-1-x64 with MSYS2`
1. Clique em `Desinstalar`
1.  Vá até o `C:\`
1.  Remova o diretório/pasta do Ruby, exemplo: `Ruby26-x64`

> **Atenção**
> Após desinstalar a versão do Ruby, será necessário seguir todos os passos de instalação citados acima e também adicionar dos driver dos navegadores novamente.

## **VSCode - Introdução e instalação**

Visual Studio Code (VSCode) é um editor de código leve, com suporte a Plugins e vários outros recursos que auxiliam no desenvolvimento.

Segue os passos de instalação:

1. Acesse o site https://code.visualstudio.com/  e faça do download clicando em Download for Windows
1. Instale o aplicativo normalmente após o fim do download.

###Extensões do VSCode
Agora vamos instalar as extensões que irão facilitar no dia a dia. Segue os passos:
1. Utilize o atalho ``Ctrl`` + ``Shift`` + ``X`` ou clique no ícone da imagem a seguir:
![4.JPEG](4.jpeg)
1. Pesquise pelas extensões abaixo:
    - **Ruby** (Extensão utilizada para identificar de forma automática o  ambiente da linguagem Ruby, dando suporte na sintaxe e semântica do código)
    - **Material Icon Theme** (Extensão utilizada para adicionar ícones aos arquivos, ficando mais fácil na identificação)  
    - **Cucumber (Gherkin) Full Support** (Extensão utilizada identificar de forma automática a linguagem Gherkin, dando suporte na sintaxe do BDD)

> **Observação:**
> Caso não tenha a mesma versão da extensão disponível, pode considerar a **ultima** versão disponível do vscode.

E por fim, configura-las:
1. Clique no ícone da extensão

![5.JPEG](5.jpeg)
1. Clique em ``Configure Extension Settings``
1. Clique em ``Edit in settings.json``

![7.JPEG](7.jpeg)
1. Remova todo o conteúdo do arquivo e <u>adicione</u> as seguintes configurações (Arquivo: `setting.json`):
```
{
  "ruby.lint": {
    "reek": true,
    "rubocop": true,
    "ruby": true,
    "fasterer": true,
    "debride": true,
    "ruby-lint": true
  },
  "workbench.iconTheme": "material-icon-theme",
   "cucumberautocomplete.steps": [
    "features/step_definitions/*_steps.rb",
    "features/step_definitions/**/*_steps.rb",
    "features/step_definitions/**/**/*_steps.rb"
  ],
  "cucumberautocomplete.syncfeatures": "features/*.feature",
  "cucumberautocomplete.strictGherkinCompletion": true,
  "cucumberautocomplete.smartSnippets": true,
  "cucumberautocomplete.stepsInvariants": true,
  "cucumberautocomplete.customParameters": [
    {
      "parameter": "{string}",
      "value": ".s*"
    },
    {
      "parameter": "{int}",
      "value": ".i*"
    },
  ],
  "cucucumberautocomplete.formatConfOverride": {
    "And": 3,
    "But": "relative",
  },
  "cucumberautocomplete.onTypeFormat": true,
  "editor.quickSuggestions": {
    "comments": false,
    "strings": true,
    "other": true
  },
  "ruby.codeCompletion": "rcodetools",
  "ruby.format": "standard",
  "ruby.intellisense": "rubyLocate",
  "explorer.confirmDragAndDrop": false
}
```
## **Selenium WebDriver - Introdução e instalação**

Para o funcionamento do Capybara é necessário instalar os drivers (_Selenium WebDriver_) que disponibilizam a interação com os navegadores (Google Chrome, Firefox). <u>Vale lembrar que, a cada atualização da versão do seu navegador, o driver também deverá ser atualizado</u>.

### Driver Google Chrome

O driver do Google Chrome, conhecido como _ChromeDriver_, é uma ferramenta utilizada para controlar e interagir com o navegador **Chrome**.

Segue os passos de instalação:

1. Acesse https://chromedriver.storage.googleapis.com/index.html  e clique na mesma versão atual do seu navegador Chrome 
(Para descobrir a versão do navegador é só > Abrir o navegador Chrome > Clicar no Menu "_Ajuda_" > Clicar em "_Sobre o Google Chrome);
1. Clique para fazer o download do arquivo ``chromedriver_win32.zip`` (mesmo que sua máquina seja 64bits)
![8.JPEG](8.jpeg)
1. Extraia o conteúdo do arquivo baixado para ``C:\Ruby26-x64\bin`` (Local de instalação do Ruby)

### Driver Firefox

O driver do Firefox (_Geckodriver_), possui a mesma funcionalidade que o _ChromeDriver_, só que no navegador **Firefox**.

Segue os passos de instalação:

1. Acesse o site https://github.com/mozilla/geckodriver/releases
1. Procure por ``Assets`` da release mais recente e clique no pacote referente ao seu Sistema Operacional e Arquitetura (32 ou 64 bits), exemplo: ``geckodriver-v0.25.0-win64.zip``
![9.JPEG](9.jpeg)
1. Extraia o conteúdo do arquivo baixado para ``C:\Ruby26-x64\bin`` (Local de instalação do Ruby)
