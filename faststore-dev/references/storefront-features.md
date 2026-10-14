# Funcionalidades de storefront

Em toda mudança, identifique primeiro o fluxo existente, o contrato GraphQL/API, o estado no SDK e os eventos de analytics suportados pelo major instalado. Preserve regras comerciais, moeda, seller, disponibilidade, preço, sessão e canal de vendas já aplicados pela loja.

| Área | Verifique antes de alterar | Regressões principais |
| --- | --- | --- |
| PDP | Rota e dados de produto, variações/SKUs, disponibilidade, seller, preço, SEO e seção CMS | SKU incompatível, preço desatualizado, compra sem seleção válida |
| PLP e busca | Query, filtros, ordenação, paginação, URL compartilhável e estados vazios | Filtro perdido ao navegar, contagem ou ordenação incorreta |
| Carrinho | Estado SDK, itemId/SKU, quantidade, estoque, promoções, persistência e feedback | Duplicação, totais divergentes, ação durante loading |
| Sessão | Identidade, região, trade policy, cookies e fronteira servidor/cliente | Vazamento de estado entre usuários ou preços por canal |
| Checkout | Contrato e URL de transição presentes no projeto | Perda de itens ou contexto; retorno inconsistente |
| Analytics | Eventos já usados, consentimento, dados mínimos e deduplicação | Eventos duplicados ou dados pessoais enviados indevidamente |
| Integrações | Autenticação, limites, falhas, cache e ambiente | Segredo no cliente, degradação sem tratamento |

Para construir a funcionalidade, reutilize fluxos nativos compatíveis e seus tipos. Se precisar ampliar dados, use [graphql-and-api.md](graphql-and-api.md). Cubra carregamento, erro recuperável, vazio e sucesso. Antes da entrega, confira diretamente a transição de estado ou regra comercial alterada quando houver uma forma local simples de fazê-lo; não exija uma suíte de testes para cada mudança. Recomende ao usuário que execute o build e, se passar, o sync do CMS quando suportado. Não presuma hook, mutation ou evento de SDK por nome; confira exports e documentação do major. Ponto de entrada: [FastStore SDK e arquitetura](https://developers.vtex.com/docs/guides/faststore) e [código oficial](https://github.com/vtex/faststore).
