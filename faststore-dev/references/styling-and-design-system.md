# Estilo e design system

SCSS é o padrão adotado por esta skill para novas estilizações em projetos FastStore. Antes de editar, identifique como a loja o usa: `@faststore/ui`, tema, tokens, mixins, módulos SCSS e overrides. Use SCSS na camada adequada; se a área existente usa outra técnica de modo consistente, siga essa convenção sem converter outros arquivos. Leia estilos de componentes análogos e a configuração de build; a implementação da loja pode ter customizações próprias.

## Descobrir o fluxo de SCSS da loja

1. Localize os arquivos `.scss`/`.sass`, seus imports e os pontos de entrada. Veja quais estilos são globais, módulos de componente, tema ou overrides; não deduza isso apenas pelo nome da pasta.
2. Siga um componente existente do JSX até o SCSS aplicado: classes, imports, tokens/variáveis, mixins, nesting, estados e breakpoints. Observe como o build compila esses arquivos e a ordem em que estilos entram na página.
3. Compare ao menos um segundo exemplo na mesma área. Se houver padrões mistos, escolha a convenção do componente ou seção alterada. Registre qualquer diferença que afete especificidade, escopo ou precedência.
4. Ao customizar, edite a camada usada pelo projeto e reutilize seus tokens e mixins. Em componentes novos, prefira SCSS com o mesmo escopo e localização dos componentes análogos. Evite seletores globais amplos, `!important` e nesting profundo quando uma regra local clara resolver. Não reorganize estilos existentes nem migre arquivos alheios à tarefa.
5. Ao entregar, peça ao usuário que rode o build configurado; se passar e a loja usar `yarn cms-sync`, peça que rode o sync em seguida. Para uma mudança visual que o build não consegue confirmar, confira apenas os estados e larguras afetados quando houver prévia disponível.

1. Reutilize tokens, tipografia, espaçamento, cores e estados do tema existente; só adicione token quando representar uma decisão compartilhada.
2. Coloque estilos na camada e convenção local corretas, preservando encapsulamento e precedência. Não copie estilos de uma versão ou loja diferente como se fossem universais.
3. Teste largura estreita, intermediária e larga conforme breakpoints reais da loja. Verifique textos longos, imagens, densidade de produtos, estados vazios e controles de toque.
4. Garanta foco visível, contraste, semântica e comportamento sem mouse. Prefira componente acessível existente quando sua API confirmar o caso de uso.
5. Revise custo de CSS, imagens e fontes para não comprometer carregamento. Evite mudar layout global para resolver um componente isolado.

Fontes de orientação e confirmação: [FastStore UI](https://developers.vtex.com/docs/guides/faststore), [customização de componentes](https://developers.vtex.com/docs/guides/faststore/developing-and-customizing-components-overview) e estilos do pacote instalado.
