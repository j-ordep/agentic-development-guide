# Fluxo de execução

[Voltar ao catálogo](README.md)

Comece por aqui quando o objetivo, as regras e o aceite da próxima mudança estiverem claros. Em uma base existente, use a arquitetura, as convenções e os contratos do projeto como ponto de partida. Um ajuste localizado e reversível pode caber em uma microentrega. Mudanças em contratos compartilhados ou dados pedem um plano proporcional ao impacto. Se faltar uma decisão que muda o comportamento ou a arquitetura, [comece pela descoberta](descoberta.md).

## 1. Encontre as regras antes de editar

Registre a feature no `task.md`. Inclua o comportamento esperado, os critérios de aceite e os links para as regras e contratos relevantes. Peça ao agente que compare a proposta com `docs/` e com o código que atende os fluxos afetados. Se encontrar um conflito, ele deve mostrar a regra, os arquivos envolvidos e o impacto para o dev decidir antes de executar a etapa afetada.

No filtro de colaboradores, por exemplo, confirme o que acontece quando o usuário informa nome e idade juntos e como o filtro interage com a paginação. Registre a decisão antes de alterar a consulta.

## 2. Divida a execução em microentregas

Associe cada regra ou contrato às etapas que ele afeta. Uma mesma regra pode atravessar várias etapas. Delegue uma etapa por vez e confira o diff local antes de avançar. O tamanho depende do que você consegue entender e revisar em conjunto.

| Microentrega local | O que conferir |
| --- | --- |
| DTO e handler para o filtro por nome | O parâmetro e seu tratamento batem com o contrato previsto. |
| Service e repository | O critério de busca respeita a correspondência definida e a paginação. |
| Integração do filtro | A requisição com nome retorna os resultados esperados e a listagem sem filtro preserva o comportamento existente. |

Idade e tempo de empresa podem entrar em etapas posteriores. A cada etapa, confira as regras que continuam valendo e marque o checkbox no `task.md` após a revisão. Execute as verificações que fazem sentido naquele ponto. Peça ao agente que informe o que executou e o que falta verificar.

## 3. Leve um comportamento integrado ao PR

A revisão local acompanha o trabalho do agente em partes. No PR, o time avalia a feature integrada, os contratos e as evidências de que o comportamento funciona. O filtro pode chegar em um único PR se couber em uma revisão. Se ficar grande, divida-o em incrementos funcionais que possam ser integrados separadamente. Uma listagem com filtro por nome pode ser um incremento antes de adicionar idade e tempo de empresa. [Leitura complementar sobre mudanças pequenas](https://google.github.io/eng-practices/review/developer/small-cls.html)

Antes de abrir o PR, rode os testes aplicáveis e confira se cobrem tanto o comportamento novo quanto os fluxos existentes afetados. No exemplo, verifique que o filtro retorna os resultados esperados e que a listagem sem filtro continua respeitando o contrato. Ao corrigir um bug reproduzível, inclua um teste de regressão e confirme que ele falha antes da correção e passa depois.

## 4. Guarde a lição no lugar certo

Antes de encerrar a feature, peça ao agente que identifique o que a revisão revelou e proponha o destino. O dev decide o que incorporar.

| O que ficou da revisão | Onde registrar |
| --- | --- |
| Uma regressão reproduzível | No teste que cobre o comportamento. |
| Uma regra de negócio esclarecida ou um contrato alterado | Na documentação do projeto, em `docs/`. |
| Um erro recorrente no modo de trabalhar com o agente | Em uma instrução curta no `AGENTS.md`, quando ela se aplicar a futuras tarefas daquele repositório. |

Atualize `docs/` com as regras e os contratos confirmados. Remova do `task.md` o contexto da feature e as etapas concluídas. Preserve a estrutura genérica do arquivo e os itens abertos de **Deixado para depois**, com o status e o que falta resolver. [Leitura complementar sobre melhoria contínua no fluxo](https://ailair.akitaonrails.com/pt-br/workflow/#basics)

## Ferramentas e limites de execução

Use os arquivos de instrução e as permissões do agente disponível no projeto. Codex e OpenCode usam `AGENTS.md`. No Claude Code, confira quais instruções foram carregadas. Um `CLAUDE.md` pode importar o `AGENTS.md` compartilhado. [Codex — Instruções](https://learn.chatgpt.com/docs/agent-configuration/agents-md) · [OpenCode — Instruções](https://opencode.ai/docs/instructions/) · [Claude Code — Instruções](https://code.claude.com/docs/en/memory)

Use um provedor autorizado para o código e os dados do projeto. Dê ao agente acesso apenas ao necessário para a tarefa. Segredos, ações em produção e alterações irreversíveis exigem tratamento separado e autorização explícita. [Referência sobre segurança de agentes](https://cheatsheetseries.owasp.org/cheatsheets/AI_Agent_Security_Cheat_Sheet.html)
