# Detecção de versão e geração de CMS

## Procedimento

1. Encontre a raiz da loja e leia `package.json`, workspace, scripts, gerenciador de pacotes e configurações. Em monorepo, analise o pacote da loja, não só a raiz.
2. Compare as versões declaradas de `@faststore/core`, `@faststore/cli`, `@faststore/api`, `@faststore/sdk`, `@faststore/ui`, `@faststore/components` e `next` com lockfile e, se houver, `node_modules` instalado. Um intervalo no manifesto não equivale à versão resolvida. Se lockfile e instalação divergirem, registre a divergência.
3. Examine estrutura e imports: presença de `@faststore/core`, personalizações em `src`, framework Gatsby ou Next, arquivos de configuração FastStore, rotas, overrides, organização GraphQL e geração de tipos.
4. Examine CMS separadamente: `cms/faststore/sections.json` e `content-types.json` indicam Headless CMS legado; arquivos `cms_component__*.jsonc` e `cms_content_type__*.jsonc`, schema com `$base` e workflow do Content plugin indicam CMS atual. Alguns projetos podem conter indícios de ambos. Não conclua CMS apenas pelo major do FastStore.
5. Consulte a documentação da versão detectada e o código instalado para confirmar qualquer API, import ou comando necessário.

## Interpretação

| Indício | Interpretação | Limite |
| --- | --- | --- |
| `@faststore/core` com major resolvido 2, 3 ou 4 | Evidência forte do major correspondente | Confira se o pacote efetivamente usado pela loja é esse |
| Ausência de `core`, Gatsby ou Next e starter antigo | Pode ser v1 | Exige confirmação por lockfile, código ou histórico |
| Next 16 gerenciado por `@faststore/cli`, GraphQL explícito | Compatível com v4 | Não deduza v4 só da versão do Next |
| `src` de customização separado do `core` | Arquitetura v2 a v4 | Não distingue v2, v3 e v4 |
| Schema JSON legado ou JSONC novo | Indício da geração do CMS | Arquivos das duas gerações podem coexistir |

A documentação oficial descreve v1, v2, v3 e v4. V1 não usa `@faststore/core`; v2/v3 compartilham arquitetura; v4 a mantém, centraliza dependências no CLI e explicita GraphQL. A página atual diz que v4 usa Next 16. Isso é contexto para investigação, não regra para inferir o major de uma loja antiga.

## Confiança e decisão

- **Alta:** major resolvido no lockfile ou instalado, coerente com manifesto, código e configuração; CMS corroborado por schema e workflow.
- **Média:** manifesto e estrutura coerentes, mas sem lockfile/instalação verificável, ou CMS indicado por arquivos sem configuração de entrega.
- **Baixa:** só nomes de arquivos, Next, README ou suposição; ou evidências conflitantes.

Registre evidência e caminho para cada conclusão. Com confiança baixa, investigue histórico de dependências, imports usados, scripts e documentação correspondente; limite a mudança ao que é independente de versão até resolver o contrato. Fonte: [versões e suporte](https://developers.vtex.com/docs/guides/faststore/getting-started-faststore-versions-and-support-levels).
