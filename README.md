<div align="center"><img alt="logo" src="https://raw.githubusercontent.com/plonegovbr/plonegovbr.portal/main/docs/logo.png" width="100" /></div>

<h1 align="center">Portal Brasil</h1>

<div align="center">

[![GitHub contributors](https://img.shields.io/github/contributors/plonegovbr/plonegovbr.portal)](https://github.com/plonegovbr/plonegovbr.portal)
[![GitHub Repo stars](https://img.shields.io/github/stars/plonegovbr/plonegovbr.portal?style=social)](https://github.com/plonegovbr/plonegovbr.portal)

</div>
<a name="ancora"></a>
# Conteúdo

- [Introdução](#introdução)
- [Funcionalidades Especializadas](#funcionalidades-especializadas)
- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Inicialização](#inicialização)
- [Estrutura](#estrutura)
- [Licença](#licença)

## Introdução

O [Portal Brasil](https://plone.org.br/projetos/portal-brasil) é a distribuição Plone que contempla casos de uso do sistema de gestão de conteúdo [Plone](https://plone.org) para organizações brasileiras.

Sucessor tecnológico do [Portal Modelo](https://plone.org.br/projetos/portal-modelo) e do [Portal Padrão](https://plone.org.br/projetos/portal-padrao), a distribuição oferece aos seus usuários:

* Tipos de conteúdo especializados
* Conteúdos de Exemplo
* Design padronizado, mas com possibilidade de pequenos ajustes

## Funcionalidades Especializadas
* Serviços
* Pessoas
* Agenda
* Notícias
* Cards


## Pré-Requisitos
### Software
- Python 3.9, 3.10, 3.11
- Node 16 (ver nota abaixo)
- Yarn 3
- Yeoman
- Docker
- GNU make

Nota: 
- [Node.js 18 está em LTS desde 2022-10-25](https://github.com/nodejs/release#release-schedule) e Node.js 16 está em modo manutenção. Entretanto, por conta de mudanças nas bibliotecas internas de SSL, algumas dependências do Volto foram descontinuadas e precisam  ser atualizadas para continuar funcionando no Node.js 18, principalmente [Webpack 4](https://github.com/webpack/webpack/issues/14532#issuecomment-947525539). Você pode usar o Node.js 18 mas precisará rodar com uma flag especial: `NODE_OPTIONS=--openssl-legacy-provider`.  Volto's pull request suporta [Node.js 18](https://github.com/plone/volto/pull/3699)
- A instalação do Python está fora do escopo desta documentação. Entretanto, recomendamos usar o gerenciaador de versõs de Python [pyenv](https://github.com/pyenv/pyenv) que permite a instalação de múltiplas versões do Python no seu ambiente de desenvolvimento sem sobrescrever a versão do Python de seu sistema.


### Hardware
Os requisitos abaixo são apenas uma estimativa mínima para um servidor Plone. Add-ons e soluções de cache podem requerer mais hardware.
- Memória - Mínimo: 256 MB RAM e 512MB de SWAP para cada Plone site. Recomendável: 2 GB ou mais de RAM por Plone site.
- Disco - Mínimo: 512 MB de espaço em disco. Recomendável: 40 GB ou mais de espaço em disco (avalie principalmente a quantidade de arquivos que o site poderá armazenar no futuro)

### Sistema Operacional
- Será necessário um Sistema operacional que rode todos os pré-requisitos de software. A maioria dos sistemas operacionais baseados em UNIX, incluindo a maioria das distribuições Linux, macOS ou Windows Subsystem for Linux (WSL) no Windows. Importante: Windows puro não é recomendado pois não suporta GNU make. Se você conseguir rodar Plone no Windows puro sem WSL, encorajamos você a documentar o processo e compartilhar com a comunidade.
  

## Instalação

### nvm
Os comandos a seguir usam o bash como shell. Adapte-os  ao seu shell favorito. Veja também a [documentação da instalação e atualização do nvm](https://github.com/nvm-sh/nvm#install--update-script). Para o fish shell, veja [nvm.fish](https://github.com/jorgebucaran/nvm.fish)

1. Crie seu arquivo  profile shell se ele não existe. Os comandos abaixo levam em conta o arquivo .bash_profile. Atente-se que em algumas distribuições como a Debian/Ubuntu este arquivo é o .bashrc. Adapte os comandos a seguir à sua distribuição.
```shell
touch ~/.bash_profile
```
2. Faça download e rode script de instalação e atualização do nvm e insira-o no bash.
```shell
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.39.3/install.sh | bash
```
3. Carregue seu arquivo profile. Alternativamente você pode fechar a seção e abrir uma nova.
```shell
source ~/.bash_profile
```
4. Veirifique se a versão do nvm é a que você instalou ou atualizou .
```shell
nvm --version
```

### Node.js
1. Instale ou atualize a versão do Node.js. Este comando também ativa a versão
```shell
nvm install 16
```
2. Verifique se a versão suportada do Node.js está ativa
```shell
node -v
```

### Yarn 3
1. Instale o Yarn e atualize para a versão 3
```shell
npm install --global yarn
yarn set version berry
```
2. Verifique se a versão 3 foi ativada
```shell
yarn -v
```

### Yeoman
1. Instale o [Yeoman](https://6.docs.plone.org/glossary.html#term-Yeoman)
```shell
npm install -g yo
```

### Make
O make vem instalado na maioria das distribuições Linux. No macOS, você precisa primeiro [instalar o Xcode](https://developer.apple.com/xcode/resources/) então instale as ferramentas de linha de comando. No Windows, é recomendado [instalar o Linuxcom WSL](https://learn.microsoft.com/en-us/windows/wsl/install) que inclui o make. Também é recomendado atualizar sua versão do make porque algumas distribuições, especialmente macOS possuem versões desatualizadas. Use seu motor de busca preferido para encontrar como atualizar o make.


### Clonando o portal no git

```shell
git clone git@github.com:plonegovbr/plonegovbr.portal.git
cd portal-brasil
make install
```

## Inicialização

Inicialização do Backend (http://localhost:8080/)

```shell
make start-backend
```

Inicialização do Frontend (http://localhost:3000/)

```shell
make start-frontend
```

## Estrutura

Há duas bases de código no diretório: backend(API) e frontend.

- **backend**: API (Backend) Instalação do Plone usando pip.
- **frontend**: React (Volto) 

## Considerações

- O repositório contém todo o código necessário para rodar o site.


## Licença

Esse projeto é licenciado sob a licença GPLv2.


## Teste o PortalBrasil

### PortalBrasil.edu

Sigas as instruções para iniciar um [ambiente com containers](./stacks/edu/README.md).

## Licença

Esse projeto é licenciado sob a licença GPLv2.
