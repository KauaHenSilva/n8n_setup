# My n8n setup

Este repositório contém os arquivos de configuração para executar o n8n com PostgreSQL, ngrok e Ollama usando o Docker Compose.

## Descrição do Projeto

Este projeto utiliza o Docker Compose para orquestrar containers para o n8n, PostgreSQL, ngrok e Ollama. A configuração inclui variáveis de ambiente, rede e armazenamento persistente.

## Descrição dos Arquivos

### docker-compose.yml

Este arquivo define os serviços necessários para o projeto:
- **postgres**: Banco de dados PostgreSQL
- **n8n**: Ferramenta de automação n8n
- **ngrok**: Túnel seguro para localhost
- **ollama**: Serviço Ollama

### .env

Este arquivo contém as variáveis de ambiente utilizadas no docker-compose.yml:
- `TIMEZONE`: O fuso horário para o n8n.
- `NGROK_TOKEN`: Token de autenticação para o ngrok.
- `URL`: A URL para o webhook do n8n.
- `POSTGRES_USER`: Nome de usuário do PostgreSQL.
- `POSTGRES_PASSWORD`: Senha do PostgreSQL.
- `POSTGRES_DB`: Nome do banco de dados PostgreSQL.
- `N8N_ENCRYPTION_KEY`: Chave de criptografia para o n8n.
- `N8N_USER_MANAGEMENT_JWT_SECRET`: Segredo JWT para a gestão de usuários do n8n.

### ngrok.yml

Este arquivo contém a configuração para o ngrok:
- **tunnels**: Define o túnel para o n8n.

## Passos para a Instalação

### Pré-requisitos

- Docker
- Docker Compose

### Configuração

1. Clone o repositório:
   ```sh
   git clone https://github.com/KauaHenSilva/n8n_setup.git
   cd n8n_setup
   ```

2. Crie um arquivo `.env` no diretório raiz e adicione o seguinte conteúdo:
   ```dotenv
   TIMEZONE=Europe/London
   NGROK_TOKEN=seu_token_ngrok
   URL=sua_url_ngrok
   POSTGRES_USER=root
   POSTGRES_PASSWORD=root
   POSTGRES_DB=n8n
   N8N_ENCRYPTION_KEY=chave-super-secreta
   N8N_USER_MANAGEMENT_JWT_SECRET=segredo-ainda-mais-secreto
   ```

3. Atualize o arquivo `ngrok.yml` com seu domínio ngrok:
   ```yaml
   version: 2
   log_level: debug
   tunnels:
       n8n:
           proto: http
           addr: n8n:5678
           domain: seu_dominio_ngrok
   ```

4. Inicie os serviços usando o Docker Compose:
   ```sh
   docker-compose up -d
   ```

5. Acesse o n8n em `http://localhost:5678`.

### Notas

- Certifique-se de que o arquivo `.env` está corretamente configurado com as suas variáveis de ambiente.
- O arquivo `ngrok.yml` deve ser atualizado com seu domínio e token ngrok.

---

Este arquivo README.md fornece uma visão geral do projeto e instruções detalhadas para configurar o ambiente. Se precisar de mais assistência, consulte a documentação do Docker e Docker Compose.
