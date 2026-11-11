# Fluxo de execução

Comece por aqui quando o objetivo, as regras e o aceite da próxima mudança estiverem claros. Em uma base existente, use a arquitetura, as convenções e os contratos do projeto como ponto de partida. Um ajuste localizado e reversível pode caber em uma microentrega. Mudanças em contratos compartilhados ou dados pedem um plano proporcional ao impacto. Se faltar uma decisão que muda o comportamento ou a arquitetura, [comece pela descoberta](descoberta.md).

## 1. Encontre as regras antes de editar

Explique a feature ao agente e peça que ele registre no `task.md` o comportamento esperado, os critérios de aceite, as regras e os contratos relevantes e a divisão em microentregas. Revise as regras e o plano antes de autorizar a primeira etapa. [Leitura complementar sobre elaborar uma especificação em conversa](https://code.claude.com/docs/en/best-practices#brainstorm-with-claude-first)

Peça ao agente que siga o `AGENTS.md` e consulte `docs/README.md`, a documentação relevante e o código dos fluxos afetados. Se existirem registros de arquitetura ou decisões que ajudem a entender o impacto, peça que ele os consulte também. Se houver uma regra em aberto ou uma divergência entre a proposta, as docs e o código, o agente deve mostrar a dúvida, os arquivos envolvidos e o impacto para você decidir antes de executar a etapa afetada.

### Quando usar o modo Plan

Use o modo Plan quando precisar revisar a abordagem antes de permitir edições. Ele ajuda na descoberta e também em bases existentes, quando a mudança cruza módulos, afeta contratos ou tem consequências difíceis de reverter. Peça ao agente que indique os pontos de impacto, as decisões em aberto, as microentregas e como verificar cada uma.

Revise o plano e peça ao agente que registre no `task.md` as decisões e etapas aprovadas. Antes de autorizar a execução, delimite a microentrega que o agente deve implementar. Para um ajuste localizado, reversível e com aceite claro, siga direto para a etapa de execução com uma verificação definida. [Leitura complementar sobre planejamento proporcional à tarefa](https://learn.chatgpt.com/docs/learn/best-practices)

## 2. Divida a execução em microentregas

No planejamento, peça ao agente que proponha microentregas com um propósito claro, associe as regras e os contratos às etapas afetadas e indique como conferir cada uma. Você ajusta ou aceita essa divisão ao revisar o plano. O tamanho depende do contexto necessário para entender a mudança e da sua capacidade de revisá-la em conjunto.

Uma alteração pontual, um conjunto de componentes relacionados e um fluxo delimitado são referências de tamanho que podem se sobrepor. Uma etapa pode corrigir uma validação, incluir um DTO com o handler que o recebe ou implementar um comportamento pelas camadas existentes. Agrupe o que precisa ser lido junto. Quando o sentido de uma constante ou struct depender de seu uso, inclua esse uso na mesma etapa.

Para uma etapa já autorizada, o agente segue o recorte definido. Se precisar ampliar o escopo, ele apresenta a proposta para você decidir antes de executar a ampliação. Delegue uma etapa por vez e confira o diff local antes de avançar.

A cada etapa, confira as regras que continuam valendo. Peça ao agente que execute as verificações aplicáveis e informe o que ainda falta verificar, incluindo o que depende das próximas etapas. Após a revisão, confirme a conclusão para que ele marque o item no `task.md`.

## 3. Leve um comportamento integrado ao PR

A revisão local acompanha o trabalho do agente em partes. No PR, o time avalia a feature integrada, os contratos e as evidências de que o comportamento funciona. Reúna a feature em um PR quando ela couber em uma revisão. Se ficar grande, divida-a em incrementos funcionais que possam ser integrados separadamente. [Leitura complementar sobre mudanças pequenas](https://google.github.io/eng-practices/review/developer/small-cls.html)

Antes de abrir o PR, rode os testes aplicáveis e confira se cobrem o comportamento novo e os fluxos existentes afetados. Use testes unitários para regras que podem ser verificadas isoladamente e testes de integração quando a mudança depender do encaixe entre partes do sistema. Ao corrigir um bug reproduzível, confirme que o teste de regressão falha pelo motivo esperado antes da correção e passa depois. [Leitura complementar sobre testes](https://martinfowler.com/articles/practical-test-pyramid.html)

## 4. Guarde a lição no lugar certo

Antes de encerrar a feature, peça ao agente que identifique o que vale preservar e proponha onde registrar. A pessoa responsável decide o que incorporar.

| Informação | Onde registrar |
| --- | --- |
| Uma regressão reproduzível | No teste que cobre o comportamento. |
| Uma regra de negócio esclarecida ou um contrato alterado | Na fonte mantida pelo projeto para essa informação. |
| Uma decisão cujo motivo será útil em mudanças futuras | Na referência existente sobre o assunto, com o resultado da pesquisa e as alternativas descartadas que ajudam a explicar a escolha. |
| Um erro recorrente no modo de trabalhar com o agente | Em uma instrução curta no `AGENTS.md`, quando ela se aplicar a futuras tarefas daquele repositório. |

Peça ao agente que atualize só o necessário nas referências do projeto e inclua essas mudanças no mesmo PR. Se ele propuser uma mudança no `AGENTS.md`, revise o diff antes de adotá-la como instrução permanente. Na conclusão da feature, peça que ele limpe o contexto e as etapas concluídas do `task.md`, preservando a estrutura e os itens abertos de **Deixado para depois**, com o status e o que falta resolver. [Leitura complementar sobre melhoria contínua no fluxo](https://ailair.akitaonrails.com/pt-br/workflow/#basics) · [Leitura complementar sobre registrar decisões e pesquisa](https://akitaonrails.com/2026/09/17/falando-um-pouco-sobre-minhas-skills-de-ia/)

## Ferramentas e limites de execução

Use os arquivos de instrução e as permissões do agente disponível no projeto. Codex e OpenCode usam `AGENTS.md`. No Claude Code, confira quais instruções foram carregadas. Um `CLAUDE.md` pode importar o `AGENTS.md` compartilhado. [Codex — Instruções](https://learn.chatgpt.com/docs/agent-configuration/agents-md) · [OpenCode — Instruções](https://opencode.ai/docs/instructions/) · [Claude Code — Instruções](https://code.claude.com/docs/en/memory)

Use um provedor autorizado para o código e os dados do projeto. Dê ao agente acesso apenas ao necessário para a tarefa. Segredos, ações em produção e alterações irreversíveis exigem tratamento separado e autorização explícita. [Referência sobre segurança de agentes](https://cheatsheetseries.owasp.org/cheatsheets/AI_Agent_Security_Cheat_Sheet.html)
