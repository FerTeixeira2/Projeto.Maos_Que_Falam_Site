# Mãos Que Falam - Aprendendo LIBRAS

Aplicativo web para ensino de LIBRAS (Língua Brasileira de Sinais) desenvolvido com React, TypeScript e preparado para integração com backend Node.js.

## 🚀 Tecnologias

- **React 18** - Biblioteca JavaScript para construção de interfaces
- **TypeScript** - Superset JavaScript com tipagem estática
- **Vite** - Build tool moderna e rápida
- **CSS Modules** - Estilos organizados por componente

## 📁 Estrutura do Projeto

```
├── src/
│   ├── components/          # Componentes React
│   │   ├── Hero.tsx
│   │   ├── Situation.tsx
│   │   ├── Relevance.tsx
│   │   ├── Conclusion.tsx
│   │   └── Button.tsx
│   ├── config/              # Configurações
│   │   └── api.ts           # Configuração da API
│   ├── hooks/               # Custom Hooks
│   │   └── useApi.ts        # Hooks para comunicação com API
│   ├── styles/              # Estilos CSS
│   │   ├── index.css        # Estilos globais
│   │   ├── Hero.css
│   │   ├── Situation.css
│   │   ├── Relevance.css
│   │   └── Conclusion.css
│   ├── types/               # Definições de tipos TypeScript
│   │   └── index.ts
│   ├── utils/               # Utilitários
│   │   └── api.ts          # Funções para requisições HTTP
│   ├── App.tsx              # Componente principal
│   └── main.tsx             # Ponto de entrada da aplicação
├── index.html
├── package.json
├── tsconfig.json
└── vite.config.ts
```

## 🛠️ Instalação e Desenvolvimento

### Pré-requisitos

- Node.js 18+ e npm/yarn/pnpm

### Instalação

```bash
# Instalar dependências
npm install

# Iniciar servidor de desenvolvimento
npm run dev

# Build para produção
npm run build

# Preview do build de produção
npm run preview
```

## 🔌 Integração com Backend Node.js

O projeto está completamente preparado para integração com um backend Node.js. A configuração da API está em `src/config/api.ts`.

### Configuração da API

1. Copie o arquivo `.env.example` para `.env`:
```bash
cp .env.example .env
```

2. Configure a URL do backend no arquivo `.env`:
```env
VITE_API_BASE_URL=http://localhost:3000/api
```

Para produção, altere para a URL do seu servidor:
```env
VITE_API_BASE_URL=https://api.maosquefalam.com.br/api
```

### Autenticação

O projeto inclui suporte completo para autenticação JWT:

```typescript
import { postData } from '../utils/api'
import { endpoints, setAuthToken } from '../config/api'
import type { LoginDto, AuthResponse } from '../types'

// Login
const login = async (email: string, password: string) => {
  const response = await postData<AuthResponse>(endpoints.auth.login, {
    email,
    password,
  } as LoginDto)
  
  // Token é automaticamente salvo no localStorage
  setAuthToken(response.data.token)
  
  return response.data
}
```

### Usando os Hooks de API (Recomendado)

Os hooks são a forma recomendada de fazer requisições em componentes React:

```typescript
import { useFetch, usePost, usePut, usePatch, useDelete } from '../hooks/useApi'
import { endpoints } from '../config/api'
import type { Course, CreateCourseDto } from '../types'

// Buscar dados (GET)
function CoursesList() {
  const { data: courses, loading, error, refetch } = useFetch<Course[]>(endpoints.courses)
  
  if (loading) return <div>Carregando...</div>
  if (error) return <div>Erro: {error.message}</div>
  
  return (
    <div>
      {courses?.map(course => (
        <div key={course.id}>{course.title}</div>
      ))}
    </div>
  )
}

// Criar dados (POST)
function CreateCourse() {
  const { post, loading, error } = usePost<Course, CreateCourseDto>()
  
  const handleSubmit = async () => {
    try {
      const newCourse = await post(endpoints.courses, {
        title: 'Novo Curso',
        description: 'Descrição do curso',
        level: 'beginner',
      })
      console.log('Curso criado:', newCourse)
    } catch (err) {
      console.error('Erro:', err)
    }
  }
  
  return (
    <button onClick={handleSubmit} disabled={loading}>
      {loading ? 'Criando...' : 'Criar Curso'}
    </button>
  )
}
```

### Utilitários de API (Para uso fora de componentes)

Para uso em funções utilitárias, serviços ou fora de componentes React:

```typescript
import { fetchData, postData, putData, patchData, deleteData } from '../utils/api'
import { endpoints } from '../config/api'
import type { User, Course } from '../types'

// GET - Buscar dados
const courses = await fetchData<Course[]>(endpoints.courses)

// POST - Criar dados
const newUser = await postData<User>(endpoints.users, {
  name: 'João',
  email: 'joao@example.com',
  password: '123456',
})

// PUT - Atualizar dados (substitui completamente)
const updated = await putData<User>(endpoints.userById('1'), {
  name: 'João Silva',
  email: 'joao.silva@example.com',
})

// PATCH - Atualizar dados (parcial)
const partiallyUpdated = await patchData<User>(endpoints.userById('1'), {
  name: 'João Silva',
})

// DELETE - Deletar dados
await deleteData(endpoints.userById('1'))
```

### Endpoints Disponíveis

O projeto inclui endpoints pré-configurados em `src/config/api.ts`:

- **Autenticação**: `endpoints.auth.login`, `endpoints.auth.register`, `endpoints.auth.me`
- **Usuários**: `endpoints.users`, `endpoints.userById(id)`, `endpoints.userStats(id)`
- **Cursos**: `endpoints.courses`, `endpoints.courseById(id)`, `endpoints.courseLessons(id)`
- **Lições**: `endpoints.lessons`, `endpoints.lessonById(id)`
- **Progresso**: `endpoints.progress`, `endpoints.progressByUser(userId)`
- **Conquistas**: `endpoints.achievements`, `endpoints.achievementsByUser(userId)`

### Exemplos Completos

Veja `src/examples/api-usage.example.ts` para exemplos completos de uso da API.

### Tratamento de Erros

Todos os hooks e funções utilitárias incluem tratamento de erros robusto:

```typescript
const { data, error } = useFetch<Course[]>(endpoints.courses)

if (error) {
  // error.message - Mensagem de erro
  // error.status - Código HTTP (401, 404, 500, etc.)
  // error.errors - Erros de validação (se houver)
  console.error('Erro:', error.message)
  console.error('Status:', error.status)
}
```

### Timeout e Cancelamento

As requisições têm timeout de 10 segundos por padrão e podem ser canceladas automaticamente se necessário.

## 📝 Tipos TypeScript

Os tipos estão definidos em `src/types/index.ts` e incluem:

- `Feature` - Características do aplicativo
- `Pillar` - Pilares do projeto
- `User` - Dados do usuário
- `Course` - Curso de LIBRAS
- `Lesson` - Lição/aula
- `UserProgress` - Progresso do usuário
- `Achievement` - Conquistas

## 🎨 Estilos

Os estilos estão organizados por componente em `src/styles/`. As variáveis CSS estão definidas em `src/styles/index.css`:

- `--cream`: #f5f1ed
- `--blue-dark`: #002e5c
- `--pink`: #e85898
- `--yellow`: #ffc84a
- `--teal`: #5db9a8
- `--blue-50`: #f0f4ff
- `--gray-600`: #666
- `--white`: #ffffff

## 🚀 Próximos Passos

1. **Backend Node.js**: Criar API REST para gerenciar usuários, cursos, lições e progresso
2. **Autenticação**: Implementar sistema de login/registro
3. **Dashboard**: Criar área do usuário para acompanhar progresso
4. **Vídeos**: Integrar player de vídeo para aulas
5. **Gamificação**: Implementar sistema de pontos e conquistas

## 📄 Licença

Este projeto é privado.

## 👥 Contribuição

Este é um projeto privado. Para contribuições, entre em contato com os mantenedores.

