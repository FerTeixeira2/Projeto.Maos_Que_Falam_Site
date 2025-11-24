# 🚀 Guia Passo a Passo - Como Rodar o Projeto

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter instalado:
- **Node.js** (versão 18 ou superior)
- **npm** (vem junto com o Node.js)

Para verificar se você tem instalado:
```bash
node --version
npm --version
```

## 🎯 Passo a Passo Completo

### **Passo 1: Abrir o Terminal**

1. Abra o **PowerShell** ou **Prompt de Comando** (CMD)
2. Navegue até a pasta do projeto:

```bash
cd "c:\Users\Ferna\OneDrive\Desktop\DEV\Novo Trabalho Gabi - Copia"
```

### **Passo 2: Verificar se as dependências estão instaladas**

Verifique se existe a pasta `node_modules`:

```bash
dir node_modules
```

Se a pasta não existir ou estiver vazia, instale as dependências:

```bash
npm install
```

**Aguarde a instalação terminar** (pode levar alguns minutos na primeira vez)

### **Passo 3: Iniciar o Servidor de Desenvolvimento**

Execute o comando:

```bash
npm run dev
```

### **Passo 4: Abrir no Navegador**

Após executar `npm run dev`, você verá uma mensagem como:

```
  VITE v5.0.8  ready in 500 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
```

**Copie o endereço `http://localhost:5173/` e cole no seu navegador!**

## 📝 Comandos Úteis

### Para **PARAR** o servidor:
- Pressione `Ctrl + C` no terminal

### Para **REINICIAR** o servidor:
- Pare o servidor (`Ctrl + C`)
- Execute novamente: `npm run dev`

### Para **VERIFICAR ERROS** no código:
```bash
npm run lint
```

### Para **CRIAR BUILD DE PRODUÇÃO**:
```bash
npm run build
```

## ⚠️ Problemas Comuns

### Erro: "npm não é reconhecido"
**Solução**: Instale o Node.js de https://nodejs.org/

### Erro: "Cannot find module"
**Solução**: Execute `npm install` novamente

### Erro: "Porta já está em uso"
**Solução**: 
1. Pare o servidor com `Ctrl + C`
2. Ou feche outros programas usando a porta 5173

### O navegador não abre automaticamente
**Solução**: Copie manualmente o endereço `http://localhost:5173/` e cole no navegador

## 🎉 Pronto!

Se tudo deu certo, você verá a aplicação "Mãos Que Falam" no navegador!

