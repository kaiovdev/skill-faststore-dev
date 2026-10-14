# faststore-dev

Uma Agent Skill para desenvolver e depurar **lojas VTEX FastStore existentes**. Ela começa pelo código da loja: identifica a versão e o CMS em uso, observa como o projeto organiza componentes e estilos e só então sugere ou implementa uma solução.

## O que a skill faz

- **Desenvolve componentes e seções:** procura primeiro implementações do projeto, FastStore UI Components e seções nativas. Quando encontra uma opção semelhante, explica o que ela atende e o que precisaria ser adaptado antes de seguir com uma abordagem.
- **Evolui código existente:** trabalha com React, TypeScript, GraphQL, CMS e SCSS conforme os padrões encontrados na área da loja. Usa princípios SOLID e Clean Code para manter responsabilidades e contratos claros, sem impor Atomic Design ou outra estrutura.
- **Investiga erros:** segue props, hooks, dados, renderização e estilos para mostrar onde o problema ocorre, por que ocorre e quais evidências sustentam o diagnóstico.
- **Mapeia a loja:** reconstrói o fluxo de uma página ou funcionalidade, ligando rota, dados, componentes, CMS e estilos aos arquivos do repositório.

Por exemplo, ao pedir uma *newsletter customizada*, a skill verifica a implementação existente e as opções nativas, compara campos e comportamento com o pedido e orienta a escolha entre reutilizar, adaptar ou criar uma seção própria.

## Como usar

1. Instale a pasta [`faststore-dev/`](faststore-dev/) inteira no seu agente de programação. Consulte o [guia de instalação](faststore-dev/Installation.md) para Codex, Claude Code, Gemini CLI e Cursor.
2. Abra o repositório da loja no agente e descreva a tarefa. A skill pode ser selecionada automaticamente ou invocada pelo nome, conforme a ferramenta.

Exemplos de pedidos:

```text
Use a skill faststore-dev para mapear como a PDP recebe e renderiza os dados de produto.
Use a skill faststore-dev para investigar por que o filtro da PLP perde o estado ao navegar.
Use a skill faststore-dev para criar uma seção de newsletter seguindo os padrões desta loja.
```

Depois de uma alteração no código da loja, a skill orienta você a executar `yarn build` no terminal e, se ele passar e o projeto usar esse fluxo, `yarn cms-sync`. Ela não executa esses comandos nem publica conteúdo no CMS.

## Estrutura

```text
faststore-dev/
├── SKILL.md         Instruções e seleção dos fluxos
├── Readme.md        Resumo incluído no pacote
├── Installation.md  Instruções de instalação por ferramenta
├── references/      Guias consultados conforme a tarefa
└── evals/           Cenários para avaliar o comportamento da skill
```

O pacote não contém código ou dados de uma loja específica. As convenções são descobertas no projeto aberto durante cada tarefa.
