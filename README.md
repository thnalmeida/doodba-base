[![Doodba deployment](https://img.shields.io/badge/deployment-doodba-informational)](https://github.com/Tecnativa/doodba)
[![Last template update](https://img.shields.io/badge/last%20template%20update-v8.4.2-informational)](https://github.com/Tecnativa/doodba-copier-template/tree/v8.4.2)
[![Odoo](https://img.shields.io/badge/odoo-v14.0-a3478a)](https://github.com/odoo/odoo/tree/14.0)
[![OEEL-1.0 license](https://img.shields.io/badge/license-OEEL--1.0-critical})](LICENSE)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://pre-commit.com/)

## **Configurando um Ambiente de Desenvolvimento Odoo com Doodba**

**Objetivo**

Este documento detalha o processo completo para configurar um ambiente de desenvolvimento Odoo utilizando o template `copier` da Tecnativa.

**Doodba**
É um projeto de código aberto desenvolvido pela empresa espanhola Tecnativa. É uma camada de orquestração que se assenta sobre a infraestrutura do Docker para gerenciar intâncias de Odoo e suas dependências. 
- Vantagens: oferece uma abordagem estruturada e opinativa para a criação de ambientes Odoo customizados utilizando containers Docker. Fornece uma imagem Docker base e um conjunto de ferramentas e convenções projetadas para simplificar e padronizar o desenvolvimento, teste e implantação de projetos Odoo. 

- Objetivo: agilizar o ciclo de vida do desenvolvimento de Odoo, promovendo as melhores práticas e automatizando tarefas repetitivas.

**Pré-requisitos**

Antes de começar, garanta que os seguintes programas estão instalados em sua máquina (Linux Ubuntu/Debian ou similar):

- **Git**
    
- **Python 3** e **pip**
    
- **Docker** e **Docker Compose**

### **Fase 1: Configuração do Ambiente Local**

Estes passos preparam sua máquina para poder usar as ferramentas necessárias.

**1.1. Instalar o `pipx`**
É necessário para evitar conflitos com os pacotes Python do sistema, usaremos o `pipx` para instalar ferramentas de linha de comando.

`sudo apt update && sudo apt install pipx`

 **1.2. Instalar o `copier`**
Com o `pipx` instalado, use-o para instalar o `copier`.

`pipx install copier`

 **1.3. Configurar o PATH do Terminal**
Para que seu terminal encontre o `copier` e outros programas instalados via `pipx`, execute o comando abaixo.

`pipx ensurepath`

Reinicie o seu terminal, o comando abaixo deve funcionar sem erros:

`copier --version` 

**1.4 Instalar os módulos**

 `pipx install invoke`
 `pipx install pre-commit`

### **Fase 2: Acesso ao Repositório da Tecnativa**


 **2.1. Acesso ao GitHub da Tecnativa**

1. Acesse o repositório do copier template no github: 
``	https://github.com/Tecnativa/doodba-copier-template/tree/main
    
### **Fase 3: Criação do Projeto Odoo com `copier`**

**3.1. Obter a URL do Template**

No repositório no GitHub, navegue até a página do repositório do template `copier`. Clique no botão azul **"Clone"** e copie a URL **HTTPS**, que deve terminar em `.git`.

**3.2. Executar o `copier`**

No terminal, navegue até o diretório onde deseja criar seu projeto e execute o comando abaixo, substituindo os valores necessários:

`copier copy https://github.com/Tecnativa/doodba-copier-template.git <nome-do-projeto> --trust`

Responda às perguntas que o `copier` fará para configurar as variáveis do projeto (como `ODOO_VERSION`, `STACK_NAME`, etc.).
---> Fique atento à compatibilidade da versão do Odoo com o BD.


### **Fase 4: Build e Execução do Ambiente**

Com a estrutura do projeto criada, o último passo é construir e iniciar os contêineres Docker.

**4.1. Entrar na Pasta do Projeto**

`cd [NOME_DA_PASTA_DO_PROJETO]`

**4.2. Iniciar o Ambiente de Desenvolvimento**

Use o seguinte comando para construir a imagem:

`invoke develop img-build git-aggregate resetdb start`

- `invoke develop`: Link simbólico entre o `devel.yaml` (docker compose de dev)

- `img-build`: Build da imagem Docker
    
- `git-aggregate`: Baixar os módulos da OCA e outros.

 **4.3. Verificar a Execução**

Para confirmar que tudo está no ar, execute `docker ps`. Você deve ver os contêineres com o status "Up". Acesse seu ambiente Odoo no navegador de acordo com a porta especificada no `docker ps`.

**http://localhost:8069


### **Comandos**

- `invoke restart´: reinicia os containers
- `invoke stop: para os containers
-  `invoke start: inicia os containers
- `invoke logs -c <NOME_DO_CONTAINER>: mostra os logs do container
- `invoke git-aggregate`: baixa os repositórios definidos em addons.yaml
- `invoke install -m <NOME_DO_MODULO>:` instala o módulo que deseja. Ex: server-tools, web. 


# doodba1 - a Doodba deployment

This project is a Doodba scaffolding. Check upstream docs on the matter:

- [General Doodba docs](https://github.com/Tecnativa/doodba).
- [Doodba copier template docs](https://github.com/Tecnativa/doodba-copier-template)
- [Doodba QA docs](https://github.com/Tecnativa/doodba-qa)

# Credits

This project is maintained by: thayna
