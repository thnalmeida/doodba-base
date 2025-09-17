[![Doodba deployment](https://img.shields.io/badge/deployment-doodba-informational)](https://github.com/Tecnativa/doodba)
[![Last template update](https://img.shields.io/badge/last%20template%20update-v8.4.2-informational)](https://github.com/Tecnativa/doodba-copier-template/tree/v8.4.2)
[![Odoo](https://img.shields.io/badge/odoo-v14.0-a3478a)](https://github.com/odoo/odoo/tree/14.0)
[![OEEL-1.0 license](https://img.shields.io/badge/license-OEEL--1.0-critical})](LICENSE)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://pre-commit.com/)

**Projeto Odoo com Doodba**
Este repositório contém um ambiente de desenvolvimento Odoo, configurado utilizando a metodologia Doodba e o template copier da Tecnativa.

💡 O que é Doodba?
Doodba é um projeto de código aberto desenvolvido pela Tecnativa que serve como uma camada de orquestração sobre Docker para gerenciar instâncias de Odoo e suas dependências.

Vantagens: Oferece uma abordagem estruturada para criar ambientes Odoo customizados com Docker. Ele simplifica e padroniza o desenvolvimento, teste e implantação de projetos, promovendo as melhores práticas e automatizando tarefas repetitivas.

✅ Pré-requisitos
Antes de começar, garanta que os seguintes programas estão instalados em seu sistema (Linux Ubuntu/Debian ou similar):

´Git´

´Python 3´ e ´pip´

´Docker´ e ´Docker Compose´

Siga os passos abaixo para recriar um projeto como este ou para iniciar este ambiente pela primeira vez.

1. Preparação do Ambiente Local (Apenas na Primeira Vez)
Estes comandos preparam sua máquina com as ferramentas necessárias para gerenciar o projeto.

1.1. Instalar ´pipx´: pipx isola as ferramentas de linha de comando em seus próprios ambientes, evitando conflitos.

Bash

sudo apt update && sudo apt install pipx
1.2. Instalar copier e outras ferramentas Usaremos pipx para instalar as ferramentas essenciais.

Bash

pipx install copier
pipx install invoke
pipx install pre-commit
1.3. Configurar o PATH do Terminal Este comando garante que seu terminal encontre os programas instalados via pipx.

Bash

pipx ensurepath
Atenção: Feche e reabra seu terminal para que a mudança no PATH tenha efeito.

2. Criando um Novo Projeto (Como Este Foi Criado)
Se você deseja criar um novo projeto Odoo do zero usando este template, siga os passos abaixo.

2.1. Execute o copier Navegue até o diretório onde deseja criar seu projeto e execute o comando abaixo, substituindo <nome-do-projeto> pelo nome desejado.

Bash

copier copy https://github.com/Tecnativa/doodba-copier-template.git <nome-do-projeto> --trust
2.2. Responda às Perguntas O copier fará uma série de perguntas para configurar as variáveis do projeto, como a versão do Odoo (ODOO_VERSION), nome do projeto (STACK_NAME), etc. Preencha de acordo com suas necessidades.

3. Iniciando Este Ambiente de Desenvolvimento
Com a estrutura do projeto pronta, siga os passos para construir e iniciar os contêineres Docker.

3.1. Entre na Pasta do Projeto

Bash

cd <nome-da-pasta-do-projeto>
3.2. Construa a Imagem e Inicie o Ambiente O comando invoke orquestra todas as tarefas necessárias para iniciar o ambiente de desenvolvimento pela primeira vez.

Bash

invoke develop img-build git-aggregate resetdb start
O que este comando faz:

develop: Utiliza o docker-compose.yml de desenvolvimento (devel.yaml).

img-build: Constrói a imagem Docker customizada para o projeto.

git-aggregate: Baixa todos os módulos de Odoo definidos no arquivo addons.yaml (ex: repositórios da OCA).

resetdb: Cria um banco de dados limpo para a primeira inicialização.

start: Inicia os contêineres.

3.3. Verifique a Execução Para confirmar que os contêineres estão no ar, execute docker ps. Você deverá ver os contêineres do projeto com o status Up.

Acesse seu ambiente Odoo no navegador: http://localhost:8069

日常 Uso e Comandos Úteis
Uma vez que o ambiente está configurado, você pode usar os seguintes comandos invoke para gerenciá-lo no dia a dia.

Parar o ambiente:

Bash

invoke stop
Iniciar o ambiente novamente:

Bash

invoke start
Reiniciar o ambiente:

Bash

invoke restart
Ver logs de um contêiner:

Bash

invoke logs -c <nome-do-container>
Atualizar os módulos de terceiros:

Bash

invoke git-aggregate
Instalar ou atualizar um módulo no Odoo:

Bash

invoke install -m <nome_do_modulo>
Exemplo: invoke install -m web_responsive


# doodba1 - a Doodba deployment

This project is a Doodba scaffolding. Check upstream docs on the matter:

- [General Doodba docs](https://github.com/Tecnativa/doodba).
- [Doodba copier template docs](https://github.com/Tecnativa/doodba-copier-template)
- [Doodba QA docs](https://github.com/Tecnativa/doodba-qa)

# Credits

This project is maintained by: thayna
