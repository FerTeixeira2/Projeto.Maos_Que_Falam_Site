# 🛠️ Extensões Recomendadas para React + TypeScript

Este documento lista as extensões recomendadas para desenvolvimento React com TypeScript no VS Code/Cursor.

## 📦 Extensões Essenciais

### 1. **ESLint** (dbaeumer.vscode-eslint)
- **O que faz**: Analisa seu código JavaScript/TypeScript em tempo real
- **Por que usar**: Encontra e corrige erros automaticamente
- **Instalação**: Já está configurado no projeto!

### 2. **Prettier** (esbenp.prettier-vscode)
- **O que faz**: Formata código automaticamente
- **Por que usar**: Mantém o código consistente e limpo
- **Instalação**: 
  ```bash
  # No VS Code/Cursor, procure por "Prettier - Code formatter"
  ```

### 3. **ES7+ React/Redux/React-Native snippets** (dsznajder.es7-react-js-snippets)
- **O que faz**: Atalhos de código para React
- **Por que usar**: Acelera o desenvolvimento com snippets
- **Exemplos de atalhos**:
  - `rafce` → Cria componente React funcional com export
  - `rfc` → Cria componente funcional
  - `useState` → Cria hook useState
  - `useEffect` → Cria hook useEffect

### 4. **TypeScript and JavaScript Language Features** (ms-vscode.vscode-typescript-next)
- **O que faz**: Suporte completo para TypeScript
- **Por que usar**: Autocomplete, verificação de tipos, refatoração
- **Instalação**: Geralmente já vem instalado

## 🎨 Extensões de Produtividade

### 5. **Auto Rename Tag** (formulahendry.auto-rename-tag)
- **O que faz**: Renomeia automaticamente tags HTML/JSX correspondentes
- **Por que usar**: Economiza tempo ao editar componentes

### 6. **Error Lens** (usernamehw.errorlens)
- **O que faz**: Mostra erros inline no código
- **Por que usar**: Visualiza erros sem abrir o painel de problemas

### 7. **Path Intellisense** (christian-kohler.path-intellisense)
- **O que faz**: Autocomplete para caminhos de arquivos
- **Por que usar**: Facilita imports e referências a arquivos

## 🚀 Como Instalar

### Método 1: Via Interface do VS Code/Cursor

1. Abra o VS Code/Cursor
2. Clique no ícone de **Extensões** na barra lateral (ou pressione `Ctrl+Shift+X`)
3. Procure pelo nome da extensão
4. Clique em **Instalar**

### Método 2: Via Command Palette

1. Pressione `Ctrl+Shift+P` (ou `Cmd+Shift+P` no Mac)
2. Digite: `Extensions: Show Recommended Extensions`
3. Clique em **Instalar** nas extensões recomendadas

### Método 3: Via Terminal (VS Code)

```bash
# Instalar ESLint
code --install-extension dbaeumer.vscode-eslint

# Instalar Prettier
code --install-extension esbenp.prettier-vscode

# Instalar React Snippets
code --install-extension dsznajder.es7-react-js-snippets

# Instalar Auto Rename Tag
code --install-extension formulahendry.auto-rename-tag

# Instalar Error Lens
code --install-extension usernamehw.errorlens

# Instalar Path Intellisense
code --install-extension christian-kohler.path-intellisense
```

## ⚙️ Configuração Recomendada

Crie um arquivo `.vscode/settings.json` no seu projeto com estas configurações:

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "typescript.tsdk": "node_modules/typescript/lib",
  "typescript.enablePromptUseWorkspaceTsdk": true,
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[javascriptreact]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

## 📝 Snippets Úteis do ES7+ React

### Criar Componente Funcional
```
rafce → React Arrow Function Component Export
```

Gera:
```typescript
import React from 'react'

const ComponentName = () => {
  return (
    <div>ComponentName</div>
  )
}

export default ComponentName
```

### Criar useState
```
useState → const [state, setState] = useState(initialState)
```

### Criar useEffect
```
useEffect → useEffect(() => { }, [])
```

### Criar useCallback
```
useCallback → useCallback(() => { }, [])
```

### Criar useMemo
```
useMemo → useMemo(() => { }, [])
```

## 🎯 Extensões Opcionais (Mas Úteis)

### **GitLens** (eamodio.gitlens)
- Visualiza histórico do Git inline
- Útil para entender mudanças no código

### **Thunder Client** (rangav.vscode-thunder-client)
- Cliente REST API dentro do VS Code
- Útil para testar endpoints do backend

### **Import Cost** (wix.vscode-import-cost)
- Mostra o tamanho dos imports
- Útil para otimização

## ✅ Verificar Instalação

Após instalar as extensões, você pode verificar se estão funcionando:

1. **ESLint**: Deve mostrar erros inline no código
2. **Prettier**: Ao salvar, o código deve ser formatado automaticamente
3. **React Snippets**: Digite `rafce` e pressione Tab para criar um componente

## 🆘 Problemas Comuns

### Prettier não está formatando
- Verifique se está configurado como formatador padrão
- Verifique se `formatOnSave` está habilitado

### ESLint não está funcionando
- Execute `npm install` para instalar dependências
- Verifique se o arquivo `.eslintrc` existe

### TypeScript não reconhece tipos
- Execute `npm install` para instalar `@types/react` e `@types/react-dom`
- Reinicie o VS Code/Cursor


