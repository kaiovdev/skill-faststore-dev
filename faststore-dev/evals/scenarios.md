# Cenários de avaliação da skill

Use estas solicitações em sessões novas com projetos de exemplo sem dados privados. Avalie o comportamento observado, não a presença literal de palavras na resposta. Os cenários não são testes de componentes da loja e não afirmam que algum build foi executado.

| Pedido de exemplo | Preparação mínima | Comportamento esperado |
| --- | --- | --- |
| “Mapeie como a PDP desta loja recebe dados e renderiza a seção de produto.” | Projeto FastStore com PDP e CMS identificáveis | A skill é acionada; entrega fluxo com referências ao código, distingue conteúdo publicado de implementação e não edita arquivos. |
| “Explique o que cada parte deste componente faz.” | Componente FastStore existente com props, hook e SCSS | Percorre chamada, dados, estado, renderização e estilos; não inventa defeito nem modifica o projeto. |
| “Crie uma newsletter customizada.” | Loja com Newsletter nativa ou UI Component semelhante | Compara a opção existente e seus limites, explica alternativas e pede preferência se a abordagem ainda não estiver definida. |
| “Adicione analytics de sucesso à newsletter.” | Loja FastStore com handler de analytics | Confere emissão e encaminhamento ao provedor, dispara sucesso só após resposta válida e evita dados pessoais no payload. |
| “Corrija o filtro de marca que perde o estado ao navegar.” | PLP FastStore com estado e URL de busca | Rastreia interação, estado, URL e query; corrige a causa no fluxo existente com verificação focal. |
| “Crie um componente React em um projeto sem FastStore.” | Projeto React genérico | A skill não é acionada por semelhança superficial de tecnologia. |

Após mudanças na skill, execute apenas os cenários que exercitam as regras alteradas e alguns de fronteira. Registre falhas observadas e ajuste instruções específicas; não acrescente uma regra global por causa de um único caso sem evidência de repetição.
