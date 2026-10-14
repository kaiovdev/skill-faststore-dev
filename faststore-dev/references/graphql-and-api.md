# GraphQL, API e tipos

1. Siga a operação existente desde a página até fragment, query/mutation, schema, resolver e origem dos dados. Compare com o schema e exports do `@faststore/api` instalado. Registre nullability, variáveis, autenticação e cache.
2. Para dados adicionais, verifique se o campo já existe ou se um fragment compatível basta. Quando precisar de extensão, confirme o padrão do projeto e da versão para `typeDefs` e resolvers. A documentação atual descreve `src/graphql/vtex/typeDefs/*.graphql` e `src/graphql/vtex/resolvers/` para extensão VTEX e uma área `thirdParty` para provedores externos; isso não prova suporte em toda versão.
3. Faça o resolver respeitar o contrato GraphQL: tipo, campos opcionais, erros, timeout, autenticação e retorno em falha. Nunca coloque credenciais em código cliente nem exponha dados privados em erro ou analytics.
4. Encontre a fonte dos tipos gerados e o script real de geração. Modifique schema/operação fonte, execute geração se disponível e revise o diff gerado. Não edite artefato gerado manualmente. Se geração exige rede ou ambiente ausente, relate o bloqueio e não invente tipos.
5. Valide sintaxe/schema, tipos, resposta real ou fixture confiável e estados de erro. Em mutation, verifique efeito, idempotência quando relevante e atualização/invalidação de estado. Evite overfetching.

Confirme imports e nomes de tipos na versão efetivamente instalada; exemplos da documentação podem evoluir. Fontes: [FastStore API](https://developers.vtex.com/docs/guides/faststore/faststore-api-overview), [extensões de API](https://developers.vtex.com/docs/guides/faststore/api-extensions-overview), [estender schema](https://developers.vtex.com/docs/guides/faststore/api-extensions-extending-api-schema).
