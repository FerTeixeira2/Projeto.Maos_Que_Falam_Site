# Guia de Integração com Backend Node.js

Este documento descreve a estrutura esperada do backend Node.js para integração com o frontend React.

## 📋 Estrutura de Endpoints Esperada

### Autenticação

#### POST `/api/auth/login`
**Request:**
```json
{
  "email": "usuario@example.com",
  "password": "senha123"
}
```

**Response (200):**
```json
{
  "data": {
    "user": {
      "id": "uuid",
      "name": "João Silva",
      "email": "usuario@example.com",
      "avatar": "https://...",
      "role": "student",
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    },
    "token": "jwt-token-here",
    "refreshToken": "refresh-token-here"
  }
}
```

#### POST `/api/auth/register`
**Request:**
```json
{
  "name": "João Silva",
  "email": "usuario@example.com",
  "password": "senha123"
}
```

**Response (201):**
```json
{
  "data": {
    "id": "uuid",
    "name": "João Silva",
    "email": "usuario@example.com",
    "role": "student",
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

#### GET `/api/auth/me`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": {
    "id": "uuid",
    "name": "João Silva",
    "email": "usuario@example.com",
    "avatar": "https://...",
    "role": "student",
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

### Usuários

#### GET `/api/users`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "name": "João Silva",
      "email": "usuario@example.com",
      "avatar": "https://...",
      "role": "student",
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### GET `/api/users/:id`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": {
    "id": "uuid",
    "name": "João Silva",
    "email": "usuario@example.com",
    "avatar": "https://...",
    "role": "student",
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

#### GET `/api/users/:id/stats`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": {
    "totalLessonsCompleted": 15,
    "totalCoursesCompleted": 2,
    "currentStreak": 5,
    "longestStreak": 10,
    "totalPoints": 1500,
    "achievementsCount": 8,
    "timeSpent": 1200
  }
}
```

### Cursos

#### GET `/api/courses`
**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "title": "LIBRAS Básico",
      "description": "Curso introdutório de LIBRAS",
      "level": "beginner",
      "thumbnail": "https://...",
      "lessonCount": 10,
      "duration": 300,
      "lessons": [],
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### GET `/api/courses/:id`
**Response (200):**
```json
{
  "data": {
    "id": "uuid",
    "title": "LIBRAS Básico",
    "description": "Curso introdutório de LIBRAS",
    "level": "beginner",
    "thumbnail": "https://...",
    "lessonCount": 10,
    "duration": 300,
    "lessons": [],
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

#### GET `/api/courses/:id/lessons`
**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "courseId": "uuid",
      "title": "Alfabeto em LIBRAS",
      "description": "Aprenda o alfabeto",
      "videoUrl": "https://...",
      "content": "Conteúdo da lição",
      "order": 1,
      "duration": 30,
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### POST `/api/courses`
**Headers:** `Authorization: Bearer <token>`

**Request:**
```json
{
  "title": "LIBRAS Básico",
  "description": "Curso introdutório de LIBRAS",
  "level": "beginner",
  "thumbnail": "https://..."
}
```

**Response (201):**
```json
{
  "data": {
    "id": "uuid",
    "title": "LIBRAS Básico",
    "description": "Curso introdutório de LIBRAS",
    "level": "beginner",
    "thumbnail": "https://...",
    "lessons": [],
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

### Lições

#### GET `/api/lessons`
**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "courseId": "uuid",
      "title": "Alfabeto em LIBRAS",
      "description": "Aprenda o alfabeto",
      "videoUrl": "https://...",
      "content": "Conteúdo da lição",
      "order": 1,
      "duration": 30,
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### GET `/api/lessons/:id`
**Response (200):**
```json
{
  "data": {
    "id": "uuid",
    "courseId": "uuid",
    "title": "Alfabeto em LIBRAS",
    "description": "Aprenda o alfabeto",
    "videoUrl": "https://...",
    "content": "Conteúdo da lição",
    "order": 1,
    "duration": 30,
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

### Progresso

#### GET `/api/progress`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "userId": "uuid",
      "lessonId": "uuid",
      "courseId": "uuid",
      "completed": false,
      "progress": 75,
      "timeSpent": 1200,
      "completedAt": null,
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### GET `/api/progress/user/:userId`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "userId": "uuid",
      "lessonId": "uuid",
      "courseId": "uuid",
      "completed": true,
      "progress": 100,
      "timeSpent": 1800,
      "completedAt": "2024-01-01T00:00:00.000Z",
      "createdAt": "2024-01-01T00:00:00.000Z",
      "updatedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### POST `/api/progress`
**Headers:** `Authorization: Bearer <token>`

**Request:**
```json
{
  "userId": "uuid",
  "lessonId": "uuid",
  "courseId": "uuid",
  "progress": 50,
  "timeSpent": 600,
  "completed": false
}
```

**Response (201):**
```json
{
  "data": {
    "id": "uuid",
    "userId": "uuid",
    "lessonId": "uuid",
    "courseId": "uuid",
    "completed": false,
    "progress": 50,
    "timeSpent": 600,
    "createdAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

#### PUT `/api/progress/:id`
**Headers:** `Authorization: Bearer <token>`

**Request:**
```json
{
  "progress": 100,
  "timeSpent": 1800,
  "completed": true
}
```

**Response (200):**
```json
{
  "data": {
    "id": "uuid",
    "userId": "uuid",
    "lessonId": "uuid",
    "courseId": "uuid",
    "completed": true,
    "progress": 100,
    "timeSpent": 1800,
    "completedAt": "2024-01-01T00:00:00.000Z",
    "updatedAt": "2024-01-01T00:00:00.000Z"
  }
}
```

### Conquistas

#### GET `/api/achievements`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "userId": "uuid",
      "type": "lesson_completed",
      "title": "Primeira Lição",
      "description": "Complete sua primeira lição",
      "icon": "🎉",
      "points": 100,
      "earnedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

#### GET `/api/achievements/user/:userId`
**Headers:** `Authorization: Bearer <token>`

**Response (200):**
```json
{
  "data": [
    {
      "id": "uuid",
      "userId": "uuid",
      "type": "lesson_completed",
      "title": "Primeira Lição",
      "description": "Complete sua primeira lição",
      "icon": "🎉",
      "points": 100,
      "earnedAt": "2024-01-01T00:00:00.000Z"
    }
  ]
}
```

## 🔐 Autenticação

O frontend espera que o backend use **JWT (JSON Web Tokens)** para autenticação.

### Fluxo de Autenticação

1. Usuário faz login via `POST /api/auth/login`
2. Backend retorna um token JWT no campo `token`
3. Frontend salva o token no `localStorage` com a chave `authToken`
4. Todas as requisições subsequentes incluem o header: `Authorization: Bearer <token>`
5. Se o token expirar (401), o frontend remove automaticamente o token do localStorage

### Estrutura do Token

O token deve ser um JWT válido que pode ser decodificado e verificado pelo backend.

## ❌ Tratamento de Erros

O backend deve retornar erros no seguinte formato:

### Erro de Validação (400)
```json
{
  "message": "Erro de validação",
  "errors": {
    "email": ["Email é obrigatório", "Email inválido"],
    "password": ["Senha deve ter no mínimo 6 caracteres"]
  },
  "statusCode": 400
}
```

### Erro de Autenticação (401)
```json
{
  "message": "Token inválido ou expirado",
  "statusCode": 401
}
```

### Erro Não Encontrado (404)
```json
{
  "message": "Recurso não encontrado",
  "statusCode": 404
}
```

### Erro do Servidor (500)
```json
{
  "message": "Erro interno do servidor",
  "statusCode": 500
}
```

## 📦 CORS

O backend deve estar configurado para aceitar requisições do frontend. Durante desenvolvimento, o frontend roda em `http://localhost:5173`.

**Exemplo de configuração CORS (Express.js):**
```javascript
const cors = require('cors')

app.use(cors({
  origin: process.env.FRONTEND_URL || 'http://localhost:5173',
  credentials: true
}))
```

## 🚀 Próximos Passos

1. Implementar os endpoints no backend Node.js conforme esta documentação
2. Configurar autenticação JWT
3. Configurar CORS adequadamente
4. Implementar validação de dados de entrada
5. Configurar variáveis de ambiente no backend
6. Testar a integração entre frontend e backend

