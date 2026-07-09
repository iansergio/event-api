# Event-Platform

O projeto é uma aplicação de eventos dividida em microserviços Spring Boot.

Hoje existem dois serviços principais:

- `auth-service`: cuida de cadastro e login de usuários.
- `events-service`: cuida da criação e consulta de eventos.

O objetivo da divisão é crescer com novos serviços no futuro sem misturar responsabilidades no mesmo código.

## Visão geral

1. O usuário se registra ou faz login no `auth-service`.
2. O `auth-service` retorna um token de autenticação.
3. O token é usado nas chamadas ao `events-service`.
4. O `events-service` valida permissões por perfil, como `USER` e `ADMIN`.

## Como rodar

O projeto usa Maven multi-módulo. Na raiz, você pode compilar os módulos com:

```bash
mvn clean install
```

Os serviços usam as portas padrão:

- `auth-service`: `8081`
- `events-service`: `8080`

### Dependências externas

Os dois serviços esperam os seguintes componentes disponíveis localmente:

- PostgreSQL em `localhost:5432`
- RabbitMQ em `localhost:5672`

## Documentação por serviço

- [auth-service](auth-service/README.md)
- [events-service](events-service/README.md)

## Estrutura

- `auth-service`: cadastro, login, segurança e emissão de token.
- `events-service`: criação e listagem de eventos.

Conforme novos serviços forem sendo criados, a ideia é adicionar um README próprio para cada um deles e manter este arquivo como ponto de entrada do projeto.