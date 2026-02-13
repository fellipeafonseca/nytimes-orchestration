# 🐳 NYTimes Microservices - Orquestração

Este repositório é responsável por orquestrar os serviços do projeto NYTimes utilizando Docker Compose.

⚠️ Ele **não contém lógica de negócio**.  
Sua única responsabilidade é gerenciar a infraestrutura e a integração entre os serviços.

---

## 🏗️ Arquitetura

O sistema é composto por três serviços principais:

- 📰 **Scraper** → Coleta notícias do NYTimes utilizando Selenium
- 🚀 **API** → Recebe, valida e persiste as notícias
- 🗄️ **PostgreSQL** → Banco de dados relacional

### Fluxo de comunicação

[ Scraper ] ---> [ API ] ---> [ PostgreSQL ]

---

## 📦 Repositórios Necessários

Antes de executar este projeto, é necessário clonar os seguintes repositórios no mesmo diretório raiz:

- 👉 https://github.com/fellipeafonseca/prj_python-api-nytimes
- 👉 https://github.com/fellipeafonseca/prj_python-rpa-nytimes-scraper

---

## 📁 Estrutura Esperada de Pastas

Todos os repositórios devem estar no mesmo nível:

workspace/
├── nytimes-api/
├── nytimes-scraper/
└── nytimes-orchestration/


⚠️ Os nomes das pastas devem corresponder exatamente aos caminhos definidos no `docker-compose.yml`.

---

## 🚀 Como Executar o Sistema Completo

### 1️⃣ Clonar os repositórios

```bash
git clone https://github.com/SEU_USUARIO/nytimes-api
git clone https://github.com/SEU_USUARIO/nytimes-scraper
git clone https://github.com/SEU_USUARIO/nytimes-orchestration
```

2️⃣ Acessar a pasta de orquestração
```
cd nytimes-orchestration
```

3️⃣ Subir os containers
```
docker compose up --build
```

## 🌐 Serviços Disponíveis

### Após a inicialização:

Serviço	URL
API (Swagger)	http://localhost:8000/docs
Banco de Dados	localhost:5432

## 🔧 Variáveis de Ambiente

As variáveis estão definidas diretamente no docker-compose.yml.
Para ambientes mais avançados (produção), recomenda-se utilizar um arquivo .env.

## 🧠 Decisões de Arquitetura

Cada serviço possui seu próprio repositório
Comunicação entre serviços ocorre via rede interna do Docker
O Scraper envia dados para a API via HTTP
A API valida e persiste os dados no PostgreSQL
A infraestrutura é gerenciada exclusivamente pelo Docker Compose
Essa abordagem segue princípios de separação de responsabilidades e permite que cada serviço seja versionado e implantado de forma independente.

## 📌 Observações Importantes

O Scraper é executado como serviço independente
A API não depende do Scraper para funcionar
Este repositório existe apenas para orquestração da infraestrutura











