# Componentes React legíveis e sustentáveis

Use SOLID e Clean Code como critérios de decisão, não como exigência de camadas, classes ou arquivos extras. A solução mais simples que expõe responsabilidades e contratos com clareza costuma ser a mais fácil de manter. Antes de criar pastas ou arquivos, observe componentes análogos no projeto atual: localização, nomes, exports, composição, hooks e estilos. Siga o padrão comprovado dessa área, seja Atomic Design ou outra organização, e as APIs da versão instalada. Não imponha a estrutura de outro projeto.

## Antes de criar um componente

1. Procure primeiro no projeto, depois nos [FastStore UI Components](ui-components.md) e, se o bloco precisa ser editável no CMS, na [lista de seções nativas e componentes sobrescrevíveis](https://developers.vtex.com/docs/guides/faststore/reference-list-of-native-sections). Um UI Component e uma seção CMS têm papéis diferentes; confirme qual o pedido exige. Use o pacote e os exports da versão realmente instalada, pois o catálogo atual pode divergir de uma loja antiga.
2. Compare a opção encontrada com o requisito: aparência, comportamento, props, dados, estados, acessibilidade, estilos e edição no CMS. Consulte a página do componente e seus tipos no projeto. Não suponha que uma prop documentada para a seção esteja disponível no UI Component, nem o inverso.
3. Quando houver componente nativo igual ou semelhante e a escolha não tiver sido dada, explique em poucas linhas como funciona e o que já cobre, identifique a diferença concreta e pergunte se o usuário prefere usá-lo, adaptá-lo ou seguir com componente próprio. Apresente a alternativa técnica viável, sem oferecer extensão que a API da versão não suporta. Com a preferência definida, execute a escolha; se o usuário já especificou a abordagem, siga-a.
4. Se faltar apenas comportamento local ou uma prop de apresentação, verifique composição, wrapper ou props existentes antes de duplicar o componente. Se o editor precisa controlar a nova prop de uma seção nativa, confirme o mecanismo de override e o schema do CMS da geração da loja em [cms-and-sections.md](cms-and-sections.md). Quando a estrutura ou o contrato nativo impedirem o requisito, crie componente ou seção próprios seguindo as convenções do projeto. Não altere `node_modules` nem trate uma prop ausente como se já fosse suportada.

Na sugestão, informe o nome do componente, sua função, o que será reaproveitado, o que exigirá código/CMS adicional e a consequência prática de cada escolha. Para overrides, preserve contratos e eventos nativos relevantes; componentes de busca e produto podem afetar analytics. Fonte: [customização de componentes FastStore](https://developers.vtex.com/docs/guides/faststore/developing-and-customizing-components-overview).

## Evoluir um componente do projeto

Quando o usuário pedir ajuda para desenvolver um componente existente, leia sua implementação, consumidores, props, estilos, dados e seção CMS antes de propor mudanças. Identifique a parte que o pedido quer evoluir; explique a decisão técnica de forma breve e implemente a alteração autorizada, ou forneça orientação pontual quando o usuário pedir apenas orientação. Siga a organização, nomes, imports, SCSS, composição e contratos observados naquela área. Corrija o problema no componente ou integração responsável, sem recriá-lo ou refatorar partes alheias à tarefa. Verifique o comportamento afetado e descreva o que ainda dependerá do build e do CMS executados pelo usuário.

## Projetar antes de codificar

1. Descreva em uma frase a responsabilidade do componente e o que suas props representam. Identifique quem fornece dados, quem controla estado e quais efeitos externos existem.
2. Separe apresentação, regra de negócio e acesso a dados quando essa distinção tornar o fluxo mais claro ou permitir teste útil. Um componente pequeno pode continuar unido; não extraia hooks, helpers ou serviços apenas para reduzir linhas.
3. Defina tipos explícitos e estreitos para props, estados e callbacks. Prefira dados derivados a estado duplicado. Dê nomes que expressem a regra da loja; evite booleanos ambíguos, abreviações obscuras e comentários que apenas repetem o código.
4. Faça a renderização revelar o fluxo principal. Trate loading, erro, vazio e sucesso em pontos previsíveis; extraia condicionais complexas para funções ou subcomponentes com nomes claros quando isso facilitar a leitura.

## Composição, pastas e exports

- Deixe a seção principal responsável pela composição e pelo contrato com o CMS. Extraia componentes para partes com estado, efeitos, regras ou evolução próprios, como busca, navegação e ações; mantenha props pequenas e explícitas. Não crie um arquivo por elemento visual apenas para reduzir o tamanho do pai.
- Quando a área do projeto usa uma pasta por componente, reúna implementação, estilos e tipos locais nela. Use `index.ts` para expor a API pública da pasta e importe pela pasta nos consumidores. Preserve o estilo de exportação da área: `export *` reexporta exports nomeados, mas não o `default`; para um componente default, use um reexport explícito ou converta os consumidores de forma coerente.
- Ao mover arquivos, atualize todos os consumidores e confira os caminhos relativos, inclusive de SCSS e tipos. Um SCSS compartilhado pode continuar junto da seção quando layout e breakpoints são coordenados; separe estilos quando tiverem responsabilidade independente.

## Aplicação prática de SOLID

- **Responsabilidade única:** cada componente ou hook deve ter um motivo principal para mudar. Um bloco visual que também busca dados, traduz contratos externos, atualiza carrinho e envia analytics merece fronteiras explícitas quando essas partes evoluem separadamente.
- **Aberto para extensão:** use composição, slots ou props existentes quando houver variação real de comportamento. Não crie um framework de variantes para uma única necessidade.
- **Substituição:** componentes que implementam a mesma interface devem manter semântica de props, acessibilidade e comportamento esperado. Um override não deve quebrar contratos do componente ou da seção original.
- **Segregação de interfaces:** exponha apenas props necessárias a cada consumidor; evite passar objetos enormes de API/CMS quando o componente usa poucos campos.
- **Inversão de dependências:** mantenha detalhes de API, SDK e CMS nas fronteiras adequadas quando a regra puder depender de um contrato tipado mais estável. Não introduza injeção artificial ou indireções sem benefício de manutenção ou teste.

## Revisão humana

Leia o diff como alguém que manterá o componente depois: é possível entender o caso principal sem saltar por muitos arquivos? Cada abstração tem um motivo? Os nomes explicam a intenção? O fluxo de dados e os efeitos são rastreáveis? A revisão local cobre riscos que o build do usuário não observará? Remova duplicação relevante e código morto, mas preserve convenções locais e evite refatoração lateral sem necessidade.
