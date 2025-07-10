# 🧩 Cheatsheet Nx + .NET + React

## 🚀 Instalação

```bash
# Instalar plugin .NET
npm i -D @nx-dotnet/core
npx nx g @nx-dotnet/core:init
```

> Requer o .NET SDK instalado no PATH.

---

## 🛠️ Geradores

### Criar apps

```bash
# React
npx nx g @nx/react:app nome-do-app

# .NET
npx nx g @nx-dotnet/core:app minha-api --language C# --test-template xunit
```

### Criar bibliotecas

```bash
# React
npx nx g @nx/react:lib nome-da-lib

# .NET
npx nx g @nx-dotnet/core:library minha-lib --language C#
```

### Testes

```bash
# .NET
npx nx g @nx-dotnet/core:test --project minha-api --test-template xunit
npx nx test minha-api
```

### Referências

```bash
npx nx g @nx-dotnet/core:project-reference --source minha-api --target minha-lib
npx nx g @nx-dotnet/core:nuget-reference --project minha-api --package Pacote.Nome
npx nx g @nx-dotnet/core:sync
npx nx g @nx-dotnet/core:restore
```

## 🧪 Como usar um Design System React

Se você criou uma biblioteca compartilhada (por exemplo, `design-system`) com componentes visuais reutilizáveis, pode importá-los diretamente nas aplicações React do monorepo:

### 📦 Criar biblioteca de Design System

```bash
npx nx g @nx/react:lib design-system
```

Coloque seus componentes dentro da lib `libs/design-system/src/lib`.

### 🔗 Importar na aplicação React

```tsx
// apps/backoffice/src/app/App.tsx
import { Button } from '@ecommerce-modulith/design-system';

export function App() {
  return <Button label="Clique aqui" />;
}
```

> O nome do import segue o padrão `<nome-do-workspace>/<nome-da-lib>`. Verifique no `tsconfig.base.json` os `paths` configurados.

### Swagger + OpenAPI

```bash
npx nx g @nx-dotnet/core:add-swagger-target --project minha-api
npx nx run api-swagger:codegen
```

> Gera tipos TypeScript para o front-end a partir de um `swagger.json`.

---

## ⚙️ Execução e Build

```bash
# React
npx nx serve nome-do-app
npx nx build nome-do-app

# .NET
npx nx build minha-api
npx nx serve minha-api
npx nx publish minha-api

# Formatar
npx nx format minha-api
```

---

## 🔍 Inspeção e Navegação

```bash
npx nx show project nome-do-app   # Ver targets disponíveis
npx nx graph                      # Visualizar dependências
npx nx list                       # Listar plugins instalados
```

---

## ⚙️ Configuração opcional (.NET)

Adicione no `nx.json`:

```json
"plugins": [
  {
    "plugin": "@nx-dotnet/core",
    "options": {
      "inferredTargets": {
        "build": true,
        "test": "xunit",
        "serve": false,
        "lint": true
      }
    }
  }
]
```

---

## 🔄 Manutenção

```bash
npx nx migrate @nx-dotnet/core
npm update @nx-dotnet/core
```

---

## 💡 Dica

Use a extensão **Nx Console** para VSCode ou IntelliJ: facilita execuções, geração de código e autocompletar.

[👉 Instalar Nx Console](https://nx.dev/getting-started/editor-setup)

---

## 🔗 Links úteis

* [Documentação Nx](https://nx.dev)
* [Tutorial React Monorepo](https://nx.dev/getting-started/tutorials/react-monorepo-tutorial)
* [Plugins Nx](https://nx.dev/plugin-registry)
* [.NET Plugin Docs](https://nx-dotnet.com/core)
* [.NET Changelog](https://nx-dotnet.com/changelog)
* [.NET Releases](https://github.com/nx-dotnet/nx-dotnet/releases)
