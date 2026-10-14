# Mapa de arquitetura da loja

1. Identifique raiz, pacotes do workspace, ponto de entrada, rotas, configuração, scripts e deploy. Leia a árvore apenas na área relevante, depois siga os imports e consumidores da função a alterar.
2. Em v2 a v4, `@faststore/core` fornece o storefront base; `@faststore/cli` combina o core com customizações em `src`. `@faststore/api` é a camada GraphQL, `@faststore/sdk` gerencia estado de comércio, `@faststore/components` fornece componentes React sem estilo e `@faststore/ui` fornece estilos e componentes visuais. Confirme no major instalado. Em v1, não aplique o modelo de `core`.
3. Localize onde a loja define layout, páginas e rotas, componentes e seções, overrides, estilos, dados, integração, testes e schemas CMS. Distinga código próprio, código do pacote e arquivos gerados. Encontre uma implementação semelhante que rode na mesma versão.
4. Descubra precedência entre props do CMS e overrides no workflow efetivo. A documentação do Headless CMS legado indica que props do CMS podem prevalecer sobre override de código; não transfira essa regra automaticamente ao CMS novo.
5. Para uma página nova, siga o roteamento e a busca de dados existentes. Confirme como o CMS associa Content Type à página, como as seções são resolvidas e como estados e metadados são montados.

## Convenção de organização do projeto atual

Antes de escolher onde criar um arquivo, examine alguns componentes semelhantes e seus imports, exports, hooks, estilos e testes próximos. Veja se a loja organiza por Atomic Design, funcionalidade, rota, domínio, tipo de seção ou outra convenção. Nomes de pastas isolados não bastam: confirme como os arquivos são usados. Projetos podem misturar padrões; siga o da área que será alterada e as instruções locais aplicáveis.

Mantenha a nomenclatura, localização e forma de composição observadas. Não reorganize o projeto para adotar Atomic Design ou outra arquitetura sem solicitação. O uso de Atomic Design dentro de um pacote FastStore não determina a organização do código da loja. Se não houver exemplo próximo, escolha a estrutura mais simples compatível com o repositório e explique a decisão no resumo.

Artefato mental mínimo antes da edição: fluxo `rota → dados/API → estado → seção/componente → CMS/estilo → validação`. Se um elo for desconhecido, siga chamadas e imports antes de criar uma solução paralela. Fontes: [FastStore](https://developers.vtex.com/docs/guides/faststore), [repositório](https://github.com/vtex/faststore), [customização de componentes](https://developers.vtex.com/docs/guides/faststore/developing-and-customizing-components-overview).
