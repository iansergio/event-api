# events-service

Serviço responsável por criar e listar eventos.

Ele exige autenticação e usa perfis de acesso para liberar operações diferentes.

## Base URL

```text
http://localhost:8080/api/events
```

## Endpoints

### `POST /`

Cria um novo evento.

Permissão necessária:

- `ADMIN`

Request:

```json
{
  "title": "Conferência de Tecnologia",
  "dateTime": "2026-08-15T19:00:00",
  "address": {
    "street": "Av. Paulista, 1000",
    "city": "São Paulo",
    "state": "SP",
    "zipCode": "01310-100"
  },
  "status": "DRAFT"
}
```

Response exemplo:

```json
{
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "title": "Conferência de Tecnologia",
  "dateTime": "2026-08-15T19:00:00",
  "address": {
    "street": "Av. Paulista, 1000",
    "city": "São Paulo",
    "state": "SP",
    "zipCode": "01310-100"
  },
  "status": "DRAFT",
  "organizerId": "550e8400-e29b-41d4-a716-446655440001"
}
```

### `GET /`

Lista todos os eventos.

Permissão necessária:

- `USER`
- `ADMIN`

Response:

```json
[
  {
    "id": "550e8400-e29b-41d4-a716-446655440000",
    "title": "Conferência de Tecnologia",
    "dateTime": "2026-08-15T19:00:00",
    "address": {
      "street": "Av. Paulista, 1000",
      "city": "São Paulo",
      "state": "SP",
      "zipCode": "01310-100"
    },
    "status": "DRAFT",
    "organizerId": "550e8400-e29b-41d4-a716-446655440001"
  }
]
```

### `GET /{eventTitle}`

Busca eventos pelo título.

Permissão necessária:

- `USER`
- `ADMIN`

Exemplo:

```text
GET /api/events/Conferência%20de%20Tecnologia
```

Se não encontrar nenhum evento com o título informado, o serviço retorna `404`.

## Observações

- O serviço roda na porta `8080`.
- A criação de evento valida se a data não está no passado.
- O status disponível hoje é `DRAFT`, `PUBLISHED` e `CANCELED`.

## Exemplo com `curl`

```bash
curl http://localhost:8080/api/events \
  -H "Authorization: Bearer <seu-token-aqui>"
```