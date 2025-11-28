## 📁 Endpoints

### Base URL
```
/events
```

### 1. Criar Novo Evento
```
POST /events
Content-Type: application/json
```

**Body:**
```json
{
  "title": "Conferência",
  "description": "Evento anual de tecnologia",
  "location": {
    "street": "Rua das Flores",
    "number": "123",
    "city": "São Paulo",
    "state": "SP",
    "zipCode": "01234-567"
  },
  "eventDate": "2025-12-15T09:00:00",
  "organizerId": "123e4567-e89b-12d3-a456-426614174000"
}
```

**Exemplo cURL:**
```bash
curl -X POST http://localhost:8080/events \
  -H "Content-Type: application/json" \
  -d '{"title":"Conferência","description":"Evento anual de tecnologia","location":"São Paulo, SP","status":"SCHEDULED","eventDate":"2024-12-15T09:00:00","organizerId":"123e4567-e89b-12d3-a456-426614174000"}'
```
---

### 2. Listar Todos os Eventos
```
GET /events
```

---

### 3. Buscar Eventos por Título
```
GET /events/{eventTitle}
```

**Exemplo:**
```
GET /events/Conferência
```

---

### 4. Atualizar o Status de um Evento
```
PATCH /events/{eventId}/status
Content-Type: application/json

{
  "status": "{EventStatus}",
  "requesterId": "{UUID}"
}
```

**Exemplo:**
```
PATCH /events/d492bb32-debf-437f-acbe-00c2aa3e6ae5/status
Content-Type: application/json

{
  "status": "FINISHED",
  "requesterId": "123e4567-e89b-12d3-a456-426614174000"
}
```




