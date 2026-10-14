# Qualidade, validação e avaliação da skill

## Em projetos reais

Leia `package.json` e identifique gerenciador de pacotes, script de build, script de sincronização do CMS e requisitos de ambiente. O usuário executará o build e a sincronização do CMS no próprio terminal; não rode esses comandos nem seus equivalentes durante a implementação. Ao entregar a mudança, recomende primeiro `yarn build` quando for o script do projeto. Se terminar sem erros e o projeto usar `yarn cms-sync`, recomende então esse comando. Não indique `cms-sync` para uma geração de CMS ou um projeto que não o suporte. O build verifica somente o que seu script realmente inclui; não presume interações, conteúdo publicado ou integrações remotas.

Não crie nem execute testes, lint ou type checking separados para toda alteração por padrão. Antes da entrega, faça uma verificação focal adicional somente quando houver risco concreto que o build não observa, como seleção de SKU, atualização do carrinho, renderização visual, contrato de CMS ou resultado de um resolver. Use o menor procedimento local que responda a essa dúvida, automatizado ou manual conforme o projeto. Não invente scripts nem execute deploy como teste.

Revise `git diff` para alterações alheias, artefatos gerados, segredos e regressões. Em componentes, revise clareza das responsabilidades, nomes, fluxo de dados, contratos de props e abstrações conforme [component-design.md](component-design.md). Registre cada comando executado, seu resultado e qualquer limitação; não declare uma verificação que não ocorreu.

Informe que o build e a sincronização do CMS estão pendentes de execução pelo usuário. Se os scripts exigirem credenciais, rede ou outro ambiente específico, mencione o requisito conhecido sem presumir resultado. Não substitua a evidência ausente por uma afirmação de que a funcionalidade funciona.

## Cenários de avaliação da skill

Estes são roteiros de avaliação e critérios de aprovação, não alegações de execução em lojas reais.

| Cenário | Comportamento esperado | Aprovação |
| --- | --- | --- |
| 1. FastStore identificável | Confronta manifesto, lockfile/instalação e arquitetura | Major e CMS com evidências e confiança; usa docs compatíveis |
| 2. Legado ou versão incerta | Investiga estrutura e imports, distingue v1 de v2–v4 sem adivinhar | Declara incerteza e evita API dependente de versão sem confirmação |
| 3. Componente responsivo | Reutiliza design system e padrões locais; separa responsabilidades quando isso torna o fluxo mais claro | Props e nomes compreensíveis, abstrações justificadas; estados, breakpoints, teclado e foco validados |
| 4. Seção CMS | Identifica geração antes de schema e registro | Schema, props e Content Type coerentes; nenhuma publicação implícita |
| 5. Funcionalidade ecommerce | Rastreia dados, estado e regra de negócio | Verificação focal quando necessária, sem API inventada; recomenda ao usuário build e sync na sequência aplicável |
| 6. Bug | Lê o fluxo afetado, aponta trecho, causa e evidência; corrige quando solicitado | Distingue hipótese de causa confirmada; verifica a correção quando possível e recomenda build ao usuário |
| 7. GraphQL/tipos | Altera fonte do contrato e usa geração real | Tipos e operação compatíveis; arquivo gerado não editado à mão |
| 8. Convenções divergentes | Inspeciona componentes análogos e segue a organização da área atual, seja Atomic Design ou outra | Localização, nomes e exports coerentes com a loja; não impõe padrão genérico nem transfere convenção a outra loja |
| 9. Explicação de componente | Percorre chamada, props, dados, estado, efeitos, JSX, SCSS e CMS relevantes | Explica função e consequência de cada parte significativa com referência ao código; não inventa defeito nem edita quando o pedido é só entendimento |
| 10. Engenharia reversa | Mapeia o fluxo solicitado a partir do repositório, sem editar | Liga rota, dados, componente, CMS e estilo com evidências; distingue código de conteúdo publicado |

Para avaliar o comportamento da skill, use os pedidos e critérios em [../evals/scenarios.md](../evals/scenarios.md). Eles exercitam a seleção da skill, análise e limites de edição; não exigem criar testes para todo componente de uma loja. Use um projeto de exemplo sem dados privados ou uma loja disponível sem modificar funcionalidades apenas para testar instalação. Se não houver projeto, limite-se à validação estrutural e à inspeção dos cenários; descreva isso claramente.
