# Debug e leitura de componentes

Use o modo que corresponde ao pedido: investigar um defeito ou explicar como um componente já escrito funciona. Nos dois casos, leia o código real e siga seus consumidores, imports e dados antes de concluir. Aponte arquivos e linhas relevantes para que o usuário consiga conferir a explicação.

## Quando há um erro

1. Reúna mensagem de erro, passos, ambiente, versão, CMS e comportamento esperado/observado. Se esses dados não vierem na tarefa, investigue o repositório e reproduza localmente quando possível; peça apenas o detalhe que impedir o diagnóstico. Não armazene URL com token, sessão ou dado privado.
2. Siga o caminho que produz o sintoma: entrada/props e CMS → dados/API → estado/hooks/efeitos → renderização/SCSS → consumidor. Confira console, rede, logs, resposta GraphQL, cache, configuração e código instalado conforme o problema. Compare um caso que funciona. Delimite se a falha vem de dados, contrato, lógica, renderização ou ambiente. Consulte o guia de troubleshooting oficial correspondente ao sintoma, sem aplicar uma solução documentada antes de confirmar a causa no projeto.
3. Mostre ao usuário **onde** ocorre o erro, **por que** aquele trecho causa o comportamento observado e **qual evidência** sustenta a conclusão. Descreva a cadeia causal de modo simples, com referência ao código. Diferencie causa confirmada, hipótese e informação ainda ausente; não atribua erro a um trecho apenas por parecer suspeito.
4. Se a tarefa pedir para resolver o erro, aplique a menor correção completa seguindo os padrões da área e verifique o caso afetado de forma focal quando possível. Se o pedido for só diagnóstico, entregue causa e proposta de correção sem editar o código. Não crie teste de regressão automaticamente; faça-o apenas quando houver risco concreto que a verificação usual não percebe.
5. Relate causa, mudança se houver, evidência e limites da verificação. Após mudança de código, recomende ao usuário o build configurado e, se ele passar e o projeto usar `yarn cms-sync`, recomende esse segundo passo. O agente não executa esses comandos.

## Quando o pedido é “debugar” ou entender um componente

Faça uma leitura guiada do fluxo, na ordem em que o componente trabalha: como é chamado, de onde vêm as props e dados, quais hooks/estados mantém, o que cada condição e efeito fazem, como monta o JSX, onde entra o SCSS, como se conecta ao CMS e quais efeitos externos executa. Agrupe trechos relacionados e explique sua função e consequência prática; não narre linha por linha sem necessidade. Mostre também os pontos em que o comportamento pode mudar por props, dados ausentes, eventos ou ambiente.

Se encontrar um defeito durante a leitura, destaque o trecho, a causa e o impacto com a evidência disponível. Se não houver defeito demonstrado, não invente um. Quando o usuário pedir somente entendimento, entregue a explicação e sugestões pertinentes sem alterar o componente. Quando pedir correção ou melhoria, siga a implementação autorizada e depois explique o que mudou.

## Troubleshooting oficial por sintoma

Comece pelo [índice geral de troubleshooting da VTEX](https://developers.vtex.com/docs/troubleshooting) quando o erro envolver serviços da plataforma ou não couber nas categorias abaixo. Confirme a versão e a geração do CMS da loja; alguns guias tratam apenas do CMS atual ou de um fluxo legado.

| Sintoma | Guia para consultar |
| --- | --- |
| Origem incerta entre base FastStore, API do provedor e código customizado | [Troubleshooting do FastStore](https://developers.vtex.com/docs/guides/faststore/troubleshooting-overview). Compare o comportamento da base e as respostas reais antes de atribuir a falha a uma camada. |
| Regressão que antes funcionava | [Rastreando a origem do erro](https://developers.vtex.com/docs/guides/faststore/troubleshooting-tracing-the-error-source). Use histórico e diff para localizar a mudança; `git bisect` só quando houver reprodução confiável e histórico adequado. |
| Hook indisponível, Provider ausente, estado antigo ou erro de tipos | [Problemas com hooks do FastStore](https://developers.vtex.com/docs/troubleshooting/issues-when-using-faststore-hooks). Confira import, versão, provider, dependências e cache aplicáveis. |
| Campos GraphQL não aparecem, schema/tipos divergem ou geração falha | [Problemas ao estender a API FastStore](https://developers.vtex.com/docs/troubleshooting/issues-during-extending-the-faststore-api-schema). Confira arquivos fonte, geração e ambiente antes de mudar contrato novamente. |
| `cms-sync` falha ou seção não aparece no editor | [Falhas de sincronização do schema CMS](https://developers.vtex.com/docs/troubleshooting/issues-during-cms-schema-sync). Confira raiz do projeto, CLI, permissões, ID da loja, referências do Content Type e geração do CMS. Não execute sync/upload: o usuário fará essa etapa após o build. |
| Loja lenta ou indisponível | [Loja lenta ou indisponível](https://developers.vtex.com/docs/troubleshooting/my-store-is-slow-or-unavailable). Distinga disponibilidade, rede, scripts externos, coleta de dados e customizações antes de alterar o componente. |

Esses guias são pontos de investigação, não substitutos da evidência local. Não altere dependências, publique conteúdo ou faça mudanças remotas apenas porque um artigo sugere esse passo. Para extensões GraphQL, consulte também o contrato da [API FastStore](https://developers.vtex.com/docs/guides/faststore/api-extensions-extending-api-schema) da versão instalada.
