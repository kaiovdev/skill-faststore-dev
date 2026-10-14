# Busca, filtros e paginação

Leia esta referência quando a tarefa tocar PLP, resultado de busca, facetas, ordenação ou paginação. Comece pela implementação da loja e pelo major instalado. Preserve o estado compartilhado, URL navegável e integração com dados; um controle visual não deve criar um estado paralelo ao mecanismo de busca existente.

O [módulo Search](https://developers.vtex.com/docs/guides/faststore/search-overview) documenta o uso de `SearchProvider`, estado e serialização da URL. A página de [`useSearch`](https://developers.vtex.com/docs/guides/faststore/search-use-search) descreve operações para termo, facetas, ordenação e página. Confirme os exports e tipos no pacote instalado antes de usar qualquer hook ou método citado na documentação atual.

Ao alterar um filtro ou ordenação, rastreie `interação → estado de busca → URL → query → lista de produtos`. Confira se voltar/avançar, compartilhamento do link, paginação e estado vazio continuam coerentes. Faça verificação focal apenas do fluxo afetado; o usuário executará o build ao final da mudança.
