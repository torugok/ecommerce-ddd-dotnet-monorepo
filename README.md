# Cheatsheet nx + dotnet

## Instalação e Inicialização

- **Adicionar o plugin ao workspace Nx:**

```bash
npm i --save-dev @nx-dotnet/core
npx nx g @nx-dotnet/core:init
```

Ou, com outros gerenciadores:

```bash
pnpm i --save-dev @nx-dotnet/core
pnpx nx g @nx-dotnet/core:init
```

```bash
yarn add --dev @nx-dotnet/core
npx nx g @nx-dotnet/core:init
```

> Certifique-se de ter o .NET SDK instalado e disponível no PATH[^1].


## Geradores (Generators)

- **Gerar uma aplicação:**

```bash
npx nx g @nx-dotnet/core:app nome-da-app --language C# --test-template nunit
```

- **Gerar uma biblioteca:**

```bash
npx nx g @nx-dotnet/core:library nome-da-lib --language C#
```

- **Adicionar referência entre projetos:**

```bash
npx nx g @nx-dotnet/core:project-reference --source projetoA --target projetoB
```

- **Sincronizar referências NuGet:**

```bash
npx nx g @nx-dotnet/core:sync
```

- **Adicionar referência NuGet a um projeto:**

```bash
npx nx g @nx-dotnet/core:nuget-reference --project nome-do-projeto --package Nome.Pacote
```

- **Restaurar pacotes NuGet:**

```bash
npx nx g @nx-dotnet/core:restore
```

- **Gerar projeto de teste:**

```bash
npx nx g @nx-dotnet/core:test --project nome-da-app --test-template nunit
```

- **Adicionar target Swagger/OpenAPI:**

```bash
npx nx g @nx-dotnet/core:add-swagger-target --project nome-da-api
```

- **Gerar biblioteca TypeScript a partir de OpenAPI/Swagger:**

```bash
npx nx g @nx-dotnet/core:swagger-typescript --project nome-da-api --outputPath libs/swagger-types
```

- **Mover projeto:**

```bash
npx nx g @nx-dotnet/core:move --project nome-do-projeto --destination novo/caminho
```


## Executores (Executors)

- **Build do projeto:**

```bash
npx nx build nome-do-projeto
```

- **Servir aplicação (hot reload):**

```bash
npx nx serve nome-do-projeto
```

- **Rodar testes:**

```bash
npx nx test nome-do-projeto
```

- **Publicar projeto:**

```bash
npx nx publish nome-do-projeto
```

- **Formatar código:**

```bash
npx nx format nome-do-projeto
```

- **Gerar documentação Swagger:**

```bash
npx nx update-swagger nome-da-api
```

- **Atualizar código gerado via OpenAPI:**

```bash
npx nx openapi-codegen --project nome-da-api
```


## Configuração

- **Configuração dos targets inferidos (Nx 17+):**
    - No `nx.json`, adicione:

```json
"plugins": [
  {
    "plugin": "@nx-dotnet/core",
    "options": {
      "inferredTargets": {
        "build": true,
        "test": "mstest",
        "serve": false,
        "lint": true
      }
    }
  }
]
```

    - Para ignorar caminhos:

```json
"ignorePaths": ["caminho/para/ignorar"]
```

    - Para tags globais:

```json
"tags": ["nx-dotnet", "backend"]
```


> O arquivo `.nx-dotnet.rc.json` ainda pode ser usado em versões anteriores[^2].


## Dicas Rápidas

- **Ver dependências e grafo do projeto:**

```bash
npx nx graph
```

- **Atualizar nx-dotnet:**

```bash
npm update @nx-dotnet/core
```

- **Migrar para nova versão:**

```bash
npx nx migrate @nx-dotnet/core
```

- **Ver changelog oficial para novidades:**
    - Consulte o changelog para ver as últimas correções e recursos[^3][^4].


## Novidades Recentes (2025)

- **Performance aprimorada em criação de dependências**
- **Ajustes no comando openapi-codegen**
- **Melhorias de compatibilidade com Nx 20**
- **Suporte a configuração via `nx.json`**
- **Correções em targets inferidos e paths no Windows**[^3][^4]


## Links Úteis

- [Documentação oficial nx-dotnet](https://nx-dotnet.com/core)[^1]
- [Changelog oficial](https://nx-dotnet.com/changelog)[^3]
- [Releases no GitHub](https://github.com/nx-dotnet/nx-dotnet/releases)[^4]

> Este cheatsheet cobre os comandos e práticas mais usados no dia a dia com o nx-dotnet, atualizado até julho de 2025. Consulte sempre a documentação e changelog para novidades e breaking changes.

<div style="text-align: center">⁂</div>

[^1]: https://nx-dotnet.com/core

[^2]: https://nx-dotnet.com/core/configuration

[^3]: https://nx-dotnet.com/changelog

[^4]: https://github.com/nx-dotnet/nx-dotnet/releases

[^5]: https://www.nx-dotnet.com

[^6]: https://github.com/nx-dotnet/nx-dotnet

[^7]: https://codesandbox.io/examples/package/@nx-dotnet/core

[^8]: https://npmjs.com/package/@nx-dotnet/nxdoc

[^9]: https://github.com/bbaia/nx-dotnet-core

[^10]: https://github.com/nrwl/nx/blob/master/docs/shared/recipes/add-stack/add-dotnet.md

[^11]: https://www.npmjs.com/package/@bbaia/nx-dotnet-core

[^12]: https://nx.dev/ci/reference/release-notes

[^13]: https://www.libhunt.com/compare-nx-dotnet-vs-nx-examples

[^14]: https://www.npmjs.com/package/@nx-dotnet/core

[^15]: https://www.jsdelivr.com/package/npm/@nx-dotnet/nxdoc

[^16]: https://nx-dotnet.com/core/generators/application

[^17]: https://dev.to/luishcastroc/the-dotnet-nx-analogjs-angular-stack-is-here-part-1-1eli

[^18]: https://classic.yarnpkg.com/en/package/@nx-dotnet/nxdoc

[^19]: https://www.reddit.com/r/dotnet/comments/1ein3vs/do_you_use_nx_or_other_alternatives_to_manage/

[^20]: https://devblogs.microsoft.com/dotnet/

[^21]: https://www.npmjs.com/search?q=dotnet

# Cheatsheet nx + React

<a alt="Nx logo" href="https://nx.dev" target="_blank" rel="noreferrer"><img src="https://raw.githubusercontent.com/nrwl/nx/master/images/nx-logo.png" width="45"></a>

✨ Your new, shiny [Nx workspace](https://nx.dev) is almost ready ✨.

[Learn more about this workspace setup and its capabilities](https://nx.dev/getting-started/tutorials/react-monorepo-tutorial?utm_source=nx_project&amp;utm_medium=readme&amp;utm_campaign=nx_projects) or run `npx nx graph` to visually explore what was created. Now, let's get you up to speed!

## Finish your CI setup

[Click here to finish setting up your workspace!](https://cloud.nx.app/connect/9cc8zeo12Z)


## Run tasks

To run the dev server for your app, use:

```sh
npx nx serve backoffice
```

To create a production bundle:

```sh
npx nx build backoffice
```

To see all available targets to run for a project, run:

```sh
npx nx show project backoffice
```

These targets are either [inferred automatically](https://nx.dev/concepts/inferred-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) or defined in the `project.json` or `package.json` files.

[More about running tasks in the docs &raquo;](https://nx.dev/features/run-tasks?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Add new projects

While you could add new projects to your workspace manually, you might want to leverage [Nx plugins](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) and their [code generation](https://nx.dev/features/generate-code?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) feature.

Use the plugin's generator to create new projects.

To generate a new application, use:

```sh
npx nx g @nx/react:app demo
```

To generate a new library, use:

```sh
npx nx g @nx/react:lib mylib
```

You can use `npx nx list` to get a list of installed plugins. Then, run `npx nx list <plugin-name>` to learn about more specific capabilities of a particular plugin. Alternatively, [install Nx Console](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) to browse plugins and generators in your IDE.

[Learn more about Nx plugins &raquo;](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects) | [Browse the plugin registry &raquo;](https://nx.dev/plugin-registry?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)


[Learn more about Nx on CI](https://nx.dev/ci/intro/ci-with-nx#ready-get-started-with-your-provider?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Install Nx Console

Nx Console is an editor extension that enriches your developer experience. It lets you run tasks, generate code, and improves code autocompletion in your IDE. It is available for VSCode and IntelliJ.

[Install Nx Console &raquo;](https://nx.dev/getting-started/editor-setup?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

## Useful links

Learn more:

- [Learn more about this workspace setup](https://nx.dev/getting-started/tutorials/react-monorepo-tutorial?utm_source=nx_project&amp;utm_medium=readme&amp;utm_campaign=nx_projects)
- [Learn about Nx on CI](https://nx.dev/ci/intro/ci-with-nx?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [Releasing Packages with Nx release](https://nx.dev/features/manage-releases?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
- [What are Nx plugins?](https://nx.dev/concepts/nx-plugins?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)

And join the Nx community:
- [Discord](https://go.nx.dev/community)
- [Follow us on X](https://twitter.com/nxdevtools) or [LinkedIn](https://www.linkedin.com/company/nrwl)
- [Our Youtube channel](https://www.youtube.com/@nxdevtools)
- [Our blog](https://nx.dev/blog?utm_source=nx_project&utm_medium=readme&utm_campaign=nx_projects)
