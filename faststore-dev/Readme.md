# faststore-dev

Skill para trabalhar em **lojas VTEX FastStore existentes**, inclusive projetos legados. Antes de sugerir código, identifica a versão instalada, distingue CMS atual de Headless CMS legado e observa como aquela loja organiza componentes, seções e estilos.

## Como ajuda

- **Componentes:** procura primeiro no projeto, em `@faststore/ui` e nas seções nativas. Se houver opção parecida, explica o que ela já faz e pergunta se você prefere reutilizar, estender ou criar um componente próprio.
- **Implementação:** cria ou evolui componentes React, overrides, schemas de seção, integrações GraphQL e funcionalidades de loja seguindo a organização local. Usa SCSS para novas estilizações e aplica SOLID/Clean Code sem adicionar abstrações desnecessárias.
- **Debug:** rastreia props, dados, hooks, CMS e renderização para mostrar onde está o erro e por que ocorre. Também pode explicar o fluxo de um componente existente sem alterar o código.
- **Engenharia reversa:** rastreia o fluxo pedido, da entrada aos dados, decisões e resultado, e explica cada etapa com evidências no próprio repositório.

Por exemplo, em uma **newsletter custom**, a skill verifica a Newsletter nativa e o UI Component, compara os campos e o comportamento pedidos e só então propõe override, composição ou seção própria.

## Instalação e uso

Copie a pasta `faststore-dev` inteira para o local de skills do seu agente. O [guia de instalação](Installation.md) traz os caminhos para Codex, Claude Code, Gemini CLI e Cursor em Windows, macOS e Linux. Depois, abra o projeto FastStore no agente e descreva a tarefa.

Exemplos de pedidos:

```text
Mapeie como a PDP desta loja recebe dados e renderiza a seção de produto.
Investigue por que o filtro da PLP perde o estado ao navegar.
Crie uma newsletter customizada seguindo os padrões deste projeto.
```

Depois de uma alteração na loja, você roda `yarn build` e, se ele passar e o projeto tiver esse fluxo, `yarn cms-sync`. A skill deixa esses comandos para você executar. Ela não contém código ou dados de uma loja específica; lê as convenções do projeto aberto em cada tarefa.
