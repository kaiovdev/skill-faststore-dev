# Engenharia reversa de uma loja FastStore

Use quando o usuário pedir para entender como uma página, componente, seção, interação ou integração funciona. Investigue **o fluxo solicitado**, sem transformar um pedido pontual em inventário da loja inteira. Se o pedido for amplo, apresente primeiro os fluxos principais e aprofunde os que importam para a pergunta.

## Padrão de investigação

1. **Delimite a pergunta e o ponto de entrada.** Identifique a rota, seção, componente, evento ou ação mencionada. Confirme raiz, versão, CMS e organização local com [version-detection.md](version-detection.md) e [architecture.md](architecture.md), apenas até o nível necessário para interpretar esse fluxo.
2. **Siga as conexões reais.** Localize quem chama ou registra o ponto de entrada e acompanhe imports, props, schemas, hooks e consumidores. Para uma interação, comece também pelo evento do usuário e siga o handler até a alteração de estado ou chamada externa. Não deduza execução só pelo nome de um arquivo.
3. **Reconstrua a cadeia causal.** Explique de onde vêm os dados (CMS, props, API/GraphQL, SDK ou estado local), como são transformados, quais condições e efeitos mudam o caminho e o que o componente renderiza ou atualiza. Inclua SCSS/tema, analytics e integrações apenas quando afetarem o comportamento pedido. A ordem pode variar: uma ação do carrinho começa no clique; uma página pode começar na rota ou no CMS.
4. **Confira cada elo importante.** Aponte arquivo e símbolo ou linha que sustentam a ligação. Compare código da loja, dependência instalada e configuração quando necessário. Diferencie comportamento confirmado pelo código, inferência e ponto não verificado. O repositório sozinho não comprova conteúdo publicado no CMS nem comportamento em produção; se houver prévia disponível, relate essa observação separadamente.

## Como explicar ao usuário

Comece com uma frase que responda diretamente à pergunta. Depois apresente o fluxo na ordem em que acontece, em poucos passos: **entrada → origem dos dados → processamento/estado → resultado visível ou efeito externo**. Em cada passo, diga **o que o código faz**, **por que isso leva ao próximo passo** e **onde conferir**. Acrescente CMS, SCSS, variantes e pontos de extensão quando fizerem diferença para aquele fluxo. Para caminhos alternativos, explique a condição que seleciona cada um; não descreva arquivos isolados sem mostrar a ligação entre eles.

Feche com lacunas relevantes e impacto prático para a tarefa do usuário. Um diagrama curto pode ajudar quando houver várias camadas, mas não substitui a explicação e as referências ao código. Se o usuário pedir alteração, use o mapa para localizar o contrato responsável e siga o fluxo normal de implementação; se pedir apenas entendimento, não edite a loja.

Não copie nomes de clientes, URLs privadas, credenciais ou observações de um repositório para as referências globais da skill. Limite a conclusão ao que foi inspecionado; um mapa parcial deve dizer quais rotas ou integrações ficaram fora do escopo.
