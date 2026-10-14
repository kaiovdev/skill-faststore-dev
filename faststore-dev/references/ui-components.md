# FastStore UI Components

Use esta referência ao criar ou adaptar interface. A VTEX oferece muitos componentes prontos em `@faststore/ui`; consulte o [catálogo oficial completo](https://developers.vtex.com/docs/guides/faststore/components-index) antes de implementar um equivalente. O catálogo organiza componentes em atoms, molecules e organisms, mas essa classificação **não define** como o projeto da loja deve organizar seus próprios arquivos.

## Encontrar um candidato

| Necessidade | Pontos de partida no catálogo |
| --- | --- |
| Ações e formulários | [Button](https://developers.vtex.com/docs/guides/faststore/atoms-button), Input, SelectField, Checkbox, Toggle |
| Camadas e feedback | [Modal](https://developers.vtex.com/docs/guides/faststore/molecules-modal), Alert, Toast, Skeleton, EmptyState |
| Produtos e compra | ProductCard, ProductPrice, BuyButton, QuantitySelector, SKU Selector |
| Busca e listagem | [Search Input](https://developers.vtex.com/docs/guides/faststore/organisms-search-input), [Filter](https://developers.vtex.com/docs/guides/faststore/organisms-filter), Product Grid, Product Shelf |
| PDP e conteúdo visual | [ImageGallery](https://developers.vtex.com/docs/guides/faststore/organisms-image-gallery), Hero, Carousel |

Os nomes acima são exemplos para pesquisa, não garantia de export ou disponibilidade em todas as versões. Consulte a página individual e o código/tipos de `@faststore/ui` instalado. Verifique props, composição, estados, acessibilidade, eventos, dependências e se a loja já oferece um wrapper ou seção com o comportamento necessário. Se o requisito envolve edição no CMS, compare também as [seções nativas e pontos de override](https://developers.vtex.com/docs/guides/faststore/reference-list-of-native-sections): um UI Component pode ser usado dentro de uma seção sem ser, por si só, uma seção registrável no CMS.

## Reutilizar, adaptar ou criar

1. Se o componente atende, use-o segundo os imports, estilos e padrões da loja. Se existir candidato igual ou semelhante e a escolha não estiver explícita, explique ao usuário como funciona e peça a preferência conforme [component-design.md](component-design.md).
2. Se faltar uma prop, determine onde ela é necessária: no componente de UI, no wrapper da loja ou no schema da seção CMS. Tente props existentes, composição ou wrapper quando preservarem o contrato. Para nova prop editável no CMS, confira o override e o schema da geração instalada em [cms-and-sections.md](cms-and-sections.md).
3. Crie um componente próprio quando o contrato ou a estrutura do nativo não permitir o requisito sem adaptação frágil. Preserve o comportamento comercial, acessibilidade e analytics relevante ao substituir partes nativas.

## SCSS dos componentes prontos

Um import React de `@faststore/ui` não garante que o estilo esteja carregado. Antes de adicionar imports SCSS, confira o tema e os estilos já incluídos no projeto para evitar duplicação. A VTEX mostra imports de estilos específicos em módulos `.module.scss`; adapte o caminho à versão instalada e à camada SCSS da loja. Para ajustar aparência, prefira tokens e `data-fs-*` documentados, com seletores restritos ao componente, seguindo [styling-and-design-system.md](styling-and-design-system.md). Fontes: [importação de estilos](https://developers.vtex.com/docs/guides/faststore/using-themes-importing-ui-components-styles), [atributos de dados](https://developers.vtex.com/docs/guides/faststore/styling-data-attributes).
