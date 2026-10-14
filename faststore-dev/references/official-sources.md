# Fontes oficiais verificadas

Confira atualidade, versão e código instalado no momento de cada tarefa. O guia geral pode descrever a versão corrente e não o major da loja.

| Fonte | Uso e limite |
| --- | --- |
| [FastStore](https://developers.vtex.com/docs/guides/faststore) | Visão geral e pacotes; pode refletir versão atual |
| [Storefront Development](https://developers.vtex.com/docs/storefront-development) | Distinguir FastStore, Store Framework e CMS Portal |
| [Versões e suporte](https://developers.vtex.com/docs/guides/faststore/getting-started-faststore-versions-and-support-levels) | Diferenças v1–v4 e suporte; confira mudanças recentes |
| [Repositório FastStore](https://github.com/vtex/faststore) | Pacotes e código da branch atual; para loja antiga, compare tag/versão instalada |
| [Starter oficial](https://github.com/vtex/starter.store) | Apontado pelo README do FastStore; a página individual não pôde ser recuperada nesta consulta. Confirme disponibilidade antes de usar; não o aplique mecanicamente a legado |
| [CMS para FastStore](https://developers.vtex.com/docs/guides/cms-for-faststore-storefronts) | CMS atual e ponte para documentação legada |
| [Escolha de customização no CMS](https://developers.vtex.com/docs/guides/customizing-faststore-with-cms) | Quando editar conteúdo, fazer override, criar seção ou alterar modelo |
| [Arquitetura de schema CMS](https://developers.vtex.com/docs/guides/understanding-cms-architecture-and-schema-declarations) | JSON legado versus JSONC atual, Content plugin |
| [Componentes e seções CMS](https://developers.vtex.com/docs/guides/understanding-components-and-sections) | Content Types, seções e componentes no CMS atual |
| [Nova seção no CMS](https://developers.vtex.com/docs/guides/faststore/developing-and-customizing-components-creating-a-new-section-cms) | Seção React, schema JSONC, registro e sync no CMS atual |
| [Override no CMS](https://developers.vtex.com/docs/guides/faststore/developing-and-customizing-components-overriding-a-native-component-cms) | Override, ID da loja, schema dos campos nativos e sincronização |
| [Headless CMS legado](https://developers.vtex.com/docs/guides/faststore/headless-cms-overview) | Workflow legado; não usar como guia do CMS atual |
| [Configuração do Headless CMS](https://developers.vtex.com/docs/guides/faststore/integration-setting-up-the-headless-cms) | `sections.json`, tipos nativos e workspace de desenvolvimento |
| [Scopes no Headless CMS](https://developers.vtex.com/docs/guides/faststore/headless-cms-managing-content-with-scopes-and-requiredscopes) | Relação `scopes`/`requiredScopes` e disponibilidade de seção |
| [Sincronização legada](https://developers.vtex.com/docs/guides/faststore/overrides-syncing-components-with-the-headless-cms) | `sections.json` e sync no Headless CMS legado |
| [Customização de componentes](https://developers.vtex.com/docs/guides/faststore/developing-and-customizing-components-overview) | Escolha entre props, estilos, overrides e seções, separada por CMS |
| [FastStore UI Components](https://developers.vtex.com/docs/guides/faststore/components-index) | Catálogo de componentes visuais; confirme exports e props na versão instalada |
| [Seções nativas e componentes sobrescrevíveis](https://developers.vtex.com/docs/guides/faststore/reference-list-of-native-sections) | Seções e pontos de override; não confundir com o catálogo de UI Components |
| [API FastStore](https://developers.vtex.com/docs/guides/faststore/faststore-api-overview) | Contratos GraphQL; confirme schema no major instalado |
| [Analytics FastStore](https://developers.vtex.com/docs/guides/faststore/analytics-overview) | Emissão e interceptação de eventos; envio ao provedor requer integração |
| [Busca FastStore](https://developers.vtex.com/docs/guides/faststore/search-overview) | Estado, facetas, ordenação e URL; confirme hooks no pacote instalado |
| [Extensão de schema](https://developers.vtex.com/docs/guides/faststore/api-extensions-extending-api-schema) | TypeDefs e resolvers atuais; imports podem variar |
| [Troubleshooting VTEX](https://developers.vtex.com/docs/troubleshooting) | Índice de problemas da plataforma; filtre pelo sintoma e pela solução FastStore |
| [Troubleshooting FastStore](https://developers.vtex.com/docs/guides/faststore/troubleshooting-overview) | Separar problemas da base, da API do provedor e de customizações |
| [Troubleshooting CMS](https://developers.vtex.com/docs/troubleshooting/issues-during-cms-schema-sync) | Diagnosticar geração, upload e seção ausente no CMS atual; o usuário executa o sync |
| [Skills da VTEX](https://github.com/vtex/skills) | Índice oficial de skills, incluindo `faststore-storefront`; repositório não copiado |
| [Skills do Codex](https://developers.openai.com/codex/skills) | Formato, descoberta, invocação e instalação global |

Para APIs específicas, encontre a página oficial correspondente e compare com a versão instalada antes de implementar. Exemplos e regras de outras skills não substituem a leitura do projeto nem as preferências de execução desta skill.
