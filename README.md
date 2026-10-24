# ☕ docker-alura

Projeto de estudos do curso de **Java Back-end** da Alura, explorando **Docker**, **Docker Compose**, **Spring Boot** e serviços locais como **PostgreSQL** e **LocalStack**. (◕‿◕)★

## 📌 Sobre

Aplicação de gerenciamento de produtos, organizada em módulos:

- `domain` — entidades e regras de negócio
- `infra` — persistência, adaptadores e configurações de infraestrutura
- `application` — API REST com Spring Boot

Subimos tudo com **Docker Compose**: aplicação + banco PostgreSQL + LocalStack (simulação da AWS localmente).

## 🛠️ Tecnologias

- Java 21
- Spring Boot 3.4.6
- Maven
- PostgreSQL 14
- LocalStack (AWS local)
- Docker & Docker Compose
- GitHub Actions (CI)

## 📂 Estrutura de pastas

```
docker-alura/
├── .github/workflows/      # CI com Maven (build a cada push)
├── application/            # Módulo da API REST
├── domain/                 # Módulo de domínio
├── infra/                  # Módulo de infraestrutura
├── Dockerfile              # Imagem da aplicação
├── docker-compose.yml      # Orquestração de containers
├── pom.xml                 # Dependências Maven
└── produto.json            # Exemplo de payload para testes
```

## 🚀 Como rodar

### Pré-requisitos
- [IntelliJ Community](https://www.jetbrains.com/idea/download/) (ou outra IDE Java)
- [Docker](https://www.docker.com/get-started/) e Docker Compose

### Variáveis de ambiente

| Nome                   | Valor             |
|------------------------|-------------------|
| `spring.profiles.active` | `local,infra_local` |

### Com Docker Compose (recomendado)

Na raiz do projeto:

```bash
docker compose up --build
```

A API fica disponível em: `http://localhost:8080/api`

### Executando fora do Docker

```sh
mvn clean install -DskipTests
```

```sh
java -jar -Dspring.profiles.active=local,infra_local application/target/api-produto.application-0.0.1-SNAPSHOT.jar
```

## 🧪 Testando a API

### Com curl

```bash
curl --location 'http://localhost:8080/api/v1/produtos' \
--header 'Content-Type: application/json' \
--data @produto.json
```

### Com Postman / Insomnia

1. Método: **POST**
2. URL: `http://localhost:8080/api/v1/produtos`
3. Body → raw → JSON, cole o conteúdo de `produto.json`
4. Envie e confira a resposta. (◕‿◕)

## 🏃 Executando Testes

```sh
mvn test
```

## 🔁 CI / GitHub Actions

O workflow em `.github/workflows/` roda o build com Maven a cada push, garantindo que o projeto compile e os testes passem.

## 📌 Versão

- [SemVer](https://semver.org/lang/pt-BR/)

## ✒ Autores

- [Maria Eduarda Angeli](https://github.com/MariaEduardaAngeli)
- Baseado no curso de Rodrigo de Sordi ([rodsordi](https://github.com/rodsordi))

---

Feito com ☕ e muito estudo kawaii! (◕‿◕)★♪~
