# auth-service

Serviço responsável por autenticação e cadastro de usuários.

Ele expõe endpoints para registrar um novo usuário e gerar um token de acesso no login.

## Base URL

```text
http://localhost:8081/api/auth
```

## Endpoints

### `POST /login`

Faz login com usuário e senha e retorna um token.

Request:

```json
{
  "username": "admin",
  "password": "admin123"
}
```

Response:

```json
{
  "token": "eyJhbGciOi...",
  "userId": "550e8400-e29b-41d4-a716-446655440000",
  "username": "admin",
  "role": "ADMIN",
  "expiresAtEpochMillis": 1710000000000
}
```

### `POST /register`

Cria um novo usuário.

Request:

```json
{
  "username": "joao",
  "password": "123456",
  "confirmPassword": "123456"
}
```

Response:

```json
{
  "token": "eyJhbGciOi...",
  "userId": "550e8400-e29b-41d4-a716-446655440000",
  "username": "joao",
  "role": "USER",
  "expiresAtEpochMillis": 1710000000000
}
```

## Observações

- O serviço roda na porta `8081`.
- O banco configurado por padrão é PostgreSQL.
- O projeto já inicia um usuário administrador de bootstrap com `admin / admin123`.

## Exemplo com `curl`

```bash
curl -X POST http://localhost:8081/api/auth/login \
  -H "Content-Type: application/json" \
  -d "{\"username\":\"admin\",\"password\":\"admin123\"}"
```