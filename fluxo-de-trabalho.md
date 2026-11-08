# Fluxo de execução

Comece por aqui quando o objetivo, as regras e o aceite da próxima mudança estiverem claros. Em uma base existente, use a arquitetura, as convenções e os contratos do projeto como ponto de partida. Um ajuste localizado e reversível pode caber em uma microentrega. Mudanças em contratos compartilhados ou dados pedem um plano proporcional ao impacto. Se faltar uma decisão que muda o comportamento ou a arquitetura, [comece pela descoberta](descoberta.md).

## 1. Encontre as regras antes de editar

Registre a feature no `task.md`. Inclua o comportamento esperado, os critérios de aceite e os links para as regras e contratos relevantes. Oriente o agente a ler o contexto do projeto em `docs/README.md` e a seguir as instruções e referências do `AGENTS.md`. Se a mudança afetar componentes, integrações ou uma decisão anterior, consulte os registros disponíveis, como `architecture.md` ou `design-decisions.md`. Compare a proposta com a documentação relevante e com o código que atende os fluxos afetados. Se encontrar um conflito, ele deve mostrar a regra, os arquivos envolvidos e o impacto para o dev decidir antes de executar a etapa afetada.

### Quando usar o modo Plan

Use o modo Plan quando precisar revisar a abordagem antes de permitir edições. Ele ajuda na descoberta e também em bases existentes, quando a mudança cruza módulos, afeta contratos ou tem consequências difíceis de reverter. Peça ao agente que indique os pontos de impacto, as decisões em aberto, as microentregas e como verificar cada uma.

Revise o plano e registre no `task.md` as decisões e etapas aprovadas. Antes de autorizar a execução, delimite a microentrega que o agente deve implementar. Para um ajuste localizado, reversível e com aceite claro, siga direto para a etapa de execução com uma verificação definida. [Leitura complementar sobre planejamento proporcional à tarefa](https://learn.chatgpt.com/docs/learn/best-practices)

## 2. Divida a execução em microentregas

Associe cada regra ou contrato às etapas que ele afeta. Uma mesma regra pode atravessar várias etapas. Delegue uma etapa por vez e confira o diff local antes de avançar. O tamanho depende do que você consegue entender e revisar em conjunto.

A cada etapa, confira as regras que continuam valendo e marque o checkbox no `task.md` após a revisão. Execute as verificações que fazem sentido naquele ponto. Peça ao agente que informe o que executou e o que falta verificar.

## 3. Leve um comportamento integrado ao PR

A revisão local acompanha o trabalho do agente em partes. No PR, o time avalia a feature integrada, os contratos e as evidências de que o comportamento funciona. Reúna a feature em um PR quando ela couber em uma revisão. Se ficar grande, divida-a em incrementos funcionais que possam ser integrados separadamente. [Leitura complementar sobre mudanças pequenas](https://google.github.io/eng-practices/review/developer/small-cls.html)

Antes de abrir o PR, rode os testes aplicáveis e confira se cobrem tanto o comportamento novo quanto os fluxos existentes afetados. Ao corrigir um bug reproduzível, inclua um teste de regressão e confirme que ele falha antes da correção e passa depois.

## 4. Guarde a lição no lugar certo

Antes de encerrar a feature, peça ao agente que identifique o que a revisão revelou e proponha o destino. O dev decide o que incorporar.

| O que ficou da revisão | Onde registrar |
| --- | --- |
| Uma regressão reproduzível | No teste que cobre o comportamento. |
| Uma regra de negócio esclarecida ou um contrato alterado | Na fonte mantida pelo projeto para essa informação. |
| Um erro recorrente no modo de trabalhar com o agente | Em uma instrução curta no `AGENTS.md`, quando ela se aplicar a futuras tarefas daquele repositório. |

Documente no mesmo PR as mudanças nas regras e nos contratos, na fonte mantida pelo projeto. Remova do `task.md` o contexto da feature e as etapas concluídas. Preserve a estrutura genérica do arquivo e os itens abertos de **Deixado para depois**, com o status e o que falta resolver. [Leitura complementar sobre melhoria contínua no fluxo](https://ailair.akitaonrails.com/pt-br/workflow/#basics)

## Ferramentas e limites de execução

Use os arquivos de instrução e as permissões do agente disponível no projeto. Codex e OpenCode usam `AGENTS.md`. No Claude Code, confira quais instruções foram carregadas. Um `CLAUDE.md` pode importar o `AGENTS.md` compartilhado. [Codex — Instruções](https://learn.chatgpt.com/docs/agent-configuration/agents-md) · [OpenCode — Instruções](https://opencode.ai/docs/instructions/) · [Claude Code — Instruções](https://code.claude.com/docs/en/memory)

Use um provedor autorizado para o código e os dados do projeto. Dê ao agente acesso apenas ao necessário para a tarefa. Segredos, ações em produção e alterações irreversíveis exigem tratamento separado e autorização explícita. [Referência sobre segurança de agentes](https://cheatsheetseries.owasp.org/cheatsheets/AI_Agent_Security_Cheat_Sheet.html)
