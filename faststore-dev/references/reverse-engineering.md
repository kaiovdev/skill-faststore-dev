# Engenharia reversa de uma loja FastStore

Use quando o pedido for entender a arquitetura, reconstruir o fluxo de uma funcionalidade ou documentar uma loja existente. Comece pelo escopo perguntado; se for amplo, produza primeiro um panorama curto e aprofunde apenas os fluxos relevantes. A leitura do repositório mostra a implementação, mas não comprova por si só o conteúdo publicado no CMS nem o comportamento em produção.

1. Confirme raiz, versão, geração do CMS e organização local com [version-detection.md](version-detection.md) e [architecture.md](architecture.md). Separe código da loja, dependências, arquivos gerados e configuração de ambiente.
2. Parta de uma rota, seção ou interação concreta e siga imports e consumidores. Rastreie `rota → dados/API/GraphQL → estado e hooks → seção/componente → CMS → SCSS/tema`, incluindo eventos de analytics e efeitos externos quando existirem. Não presuma que um nome de arquivo corresponde ao que é renderizado.
3. Para cada ligação importante, registre o arquivo, o símbolo ou a configuração que a demonstra. Classifique como confirmado, inferido ou não verificado. Se houver acesso legítimo a uma prévia ou à loja, use a observação para confirmar comportamento visual e conteúdo, distinguindo-a do que o código prova.
4. Entregue um mapa legível dos fluxos pedidos, pontos de extensão, dependências e riscos relevantes para a próxima tarefa. Se o usuário quiser reproduzir ou modificar uma funcionalidade, explique primeiro seu contrato e onde ela se conecta; depois siga o fluxo normal de implementação.

Não edite a loja em um pedido apenas de mapeamento. Não copie nomes de clientes, URLs privadas, credenciais ou observações de um repositório para as referências globais da skill. Limite a conclusão ao que foi inspecionado; um mapa parcial deve dizer quais rotas ou integrações ficaram fora do escopo.
