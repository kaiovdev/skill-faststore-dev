---
name: faststore-dev
description: Desenvolver, depurar e fazer engenharia reversa de lojas VTEX FastStore existentes. Use para explicar o fluxo de uma funcionalidade, entender a arquitetura, criar ou evoluir componentes e seções ou investigar erros a partir do projeto real.
---

# FastStore development

Use esta skill para entender, criar, evoluir e depurar uma loja VTEX FastStore. Entregue a análise ou implementação pedida no projeto existente, preservando seus contratos e convenções. Não trate Store Framework ou CMS Portal como FastStore sem evidência.

## Fluxo obrigatório

1. Leia os `AGENTS.md` aplicáveis, instruções locais, critérios de aceitação e o estado do Git. Não altere trabalho preexistente do usuário.
2. Inspecione árvore, `package.json`, scripts, lockfile, dependências instaladas, configuração, imports, rotas, GraphQL e CMS. Identifique também como este projeto organiza componentes, hooks, estilos e seções; Atomic Design é apenas uma possibilidade, nunca um padrão presumido. Classifique versão e confiança conforme [version-detection.md](references/version-detection.md); mapeie a arquitetura com [architecture.md](references/architecture.md). Se a evidência conflitar, investigue antes de código dependente da versão.
3. Localize implementações análogas na mesma área da loja e siga suas convenções de localização, nomenclatura, exports e composição, salvo se houver motivo concreto para mudar. Antes de criar componente, procure equivalente ou semelhante entre os componentes do projeto, as seções nativas e os FastStore UI Components disponíveis na versão instalada; use [ui-components.md](references/ui-components.md). Identifique o contrato real do componente, API ou dado. Consulte o código instalado e documentação oficial específica da versão; use [official-sources.md](references/official-sources.md). Confirme import, assinatura e disponibilidade antes de introduzi-los.
4. Se encontrar uma opção nativa igual ou próxima ao pedido e a escolha não estiver definida, explique ao usuário o que ela faz, o que já atende e quais props ou comportamentos faltam; pergunte se prefere reutilizá-la, estendê-la ou criar uma solução própria. Para mudança complexa, apresente um plano curto. Ao desenvolver um componente novo ou existente, ajude a implementar, integrar, revisar ou depurar a parte solicitada, seguindo os padrões observados na área do projeto. Aplique SOLID e Clean Code de forma proporcional: responsabilidades claras, nomes que revelem intenção, composição e contratos pequenos; extraia lógica apenas quando isso melhorar a leitura ou houver motivo concreto para reutilização. Siga [component-design.md](references/component-design.md). Preserve contratos, tipos e comportamento. Evite `any`, casts inseguros, dependências desnecessárias e edições manuais em arquivos gerados.
5. Use SCSS como padrão para novas estilizações, seguindo a organização, o tema, os módulos e os mixins do projeto atual; se a área usa outra técnica estabelecida, preserve sua consistência. Consulte [styling-and-design-system.md](references/styling-and-design-system.md). Cubra estados de carregamento, erro, vazio e sucesso quando aplicáveis. Verifique responsividade, acessibilidade, SEO e performance; proteja segredos e dados privados. Não altere versões de pacotes ou a geração do CMS como parte de uma tarefa de desenvolvimento comum. Não publique no CMS, execute deploy ou operações remotas sem autorização apropriada.
6. Confira os scripts e o gerenciador de pacotes do projeto. Revise o diff e faça apenas verificações locais proporcionais à mudança; não execute o build nem a sincronização do CMS, incluindo `yarn build` e `yarn cms-sync`, pois o usuário fará essas etapas no terminal após a entrega. Não alegue que o build passou ou que o CMS foi sincronizado. Consulte [quality-and-testing.md](references/quality-and-testing.md) para a sequência a recomendar.

Peça a preferência do usuário ao encontrar um componente nativo igual ou semelhante quando a escolha entre reutilização, extensão e solução própria não estiver definida. Para outras dúvidas, pergunte apenas quando uma decisão ausente impedir a implementação correta. Uma incerteza de versão exige mais investigação local antes de perguntar.

Descubra as convenções diretamente no repositório da tarefa. Não registre nomes de lojas, caminhos privados, versões observadas ou detalhes de clientes nas referências globais desta skill. Se uma descoberta precisar ser documentada, faça isso apenas no contexto da tarefa ou em um arquivo do próprio projeto quando solicitado.

Em tarefas de debug, leia o código e seus consumidores para mostrar o erro, a causa e a evidência, ou explicar o fluxo do componente parte por parte quando esse for o pedido. Separe causa confirmada de hipótese e use [debugging-and-troubleshooting.md](references/debugging-and-troubleshooting.md). Se o usuário pedir correção, implemente-a; se pedir somente explicação, não altere código.

Para fazer engenharia reversa, siga [reverse-engineering.md](references/reverse-engineering.md): trace o fluxo específico pedido pelo usuário e explique, em ordem, de onde vêm os dados, como o código os processa e qual comportamento produz, com evidências nos arquivos. Não edite o projeto quando o pedido for apenas de entendimento. Em tarefas de analytics ou busca, consulte respectivamente [analytics.md](references/analytics.md) e [search.md](references/search.md) apenas quando pertinentes.

## Referências sob demanda

- [version-detection.md](references/version-detection.md): sempre no início, para versão, CMS e confiança.
- [architecture.md](references/architecture.md): localizar responsabilidades, rotas, configuração e overrides.
- [component-design.md](references/component-design.md): descobrir UI Components e seções nativas, decidir reutilização/extensão e projetar componentes React legíveis.
- [ui-components.md](references/ui-components.md): catálogo oficial, escolha e estilização dos componentes prontos de `@faststore/ui`.
- [storefront-features.md](references/storefront-features.md): PDP, PLP, busca, SKU, carrinho, sessão, checkout e analytics.
- [cms-and-sections.md](references/cms-and-sections.md): criar ou alterar seção e modelo de conteúdo; separar CMS atual do legado.
- [graphql-and-api.md](references/graphql-and-api.md): query, mutation, API extension, integração e tipos gerados.
- [styling-and-design-system.md](references/styling-and-design-system.md): interface, tema e responsividade.
- [quality-and-testing.md](references/quality-and-testing.md): validação, revisão e cenários de avaliação da skill.
- [seo-performance-accessibility.md](references/seo-performance-accessibility.md): requisitos não funcionais de página ou componente.
- [debugging-and-troubleshooting.md](references/debugging-and-troubleshooting.md): diagnosticar erros com causa e evidência ou explicar o fluxo de um componente existente.
- [reverse-engineering.md](references/reverse-engineering.md): rastrear e explicar passo a passo o fluxo de uma funcionalidade existente.
- [analytics.md](references/analytics.md): preservar e implementar eventos de analytics quando a tarefa envolver rastreamento.
- [search.md](references/search.md): entender estado, facetas, ordenação, paginação e URLs de busca.
- [official-sources.md](references/official-sources.md): índice de fontes e limites de versão; confirme atualidade ao usar.

## Resposta final

Resuma versão e CMS identificados com confiança, arquivos e comportamento alterados, verificações efetivamente feitas e limitações. Após concluir mudanças em uma loja que tenha esses scripts, oriente o usuário a rodar `yarn build` no terminal e, somente se ele passar, `yarn cms-sync`; deixe claro que os comandos ainda não foram executados. Se a loja não tiver esse workflow, indique os comandos reais sem inventar `cms-sync`. Se a tarefa não alterou código, relate o diagnóstico e sua evidência.
