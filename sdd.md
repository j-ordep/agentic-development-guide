# SDD e OpenSpec

Proposta da v2, em avaliação. Considere a necessidade da mudança e o processo já adotado pela equipe ao escolher esse fluxo.

O desenvolvimento orientado por especificações (SDD) explicita o comportamento esperado, os cenários e os critérios de aceite para orientar a implementação e a revisão. O agente ajuda a esclarecer e registrar essas definições, que evoluem com as decisões confirmadas. O fluxo simples do guia já registra objetivo, regras e aceite no `task.md`.

O OpenSpec organiza especificações mantidas e propostas de mudança, com tarefas para o agente implementar. A ferramenta acompanha planejamento, execução e encerramento no repositório. [Visão do fluxo do OpenSpec](https://openspec.dev/docs/quickstart)

## Quando avaliar uma ferramenta de SDD

O agente pode recomendar sua avaliação quando identificar um benefício concreto, como alinhar várias regras e exceções, registrar a mudança de um contrato compartilhado ou manter uma referência entre pessoas e sessões. Explique o motivo relacionado à tarefa e o esforço de documentação que a ferramenta acrescenta. Uma mudança localizada com aceite claro pode seguir o fluxo simples.

Na descoberta, esclareça as decisões necessárias para o próximo incremento e registre o que for confirmado. Durante a execução, mantenha essas definições alinhadas ao comportamento aprovado.

## Se a ferramenta estiver ausente ou ainda sem aprovação

Confira nas instruções e nos arquivos do projeto qual fluxo está adotado e se a ferramenta está disponível no ambiente em que o agente trabalha. A disponibilidade da ferramenta e a autorização para usá-la são verificações distintas. Siga a [diretriz de aprovação para skills](fluxo-de-trabalho.md#uso-de-skills) e peça aprovação antes de instalar, configurar ou executar uma ferramenta nova.

Se a mudança justificar a recomendação e a escolha do fluxo estiver em aberto, apresente-a uma vez durante o planejamento. Use uma mensagem como esta, preenchendo o motivo com o contexto real da tarefa.

> Esta mudança altera um contrato compartilhado e envolve vários cenários. O guia sugere avaliar o OpenSpec para manter essas definições alinhadas. Posso seguir com `task.md` e microentregas ou você prefere avaliar a adoção do OpenSpec?

Se o fluxo atual já estiver autorizado, prossiga com ele e apresente a sugestão como uma opção para avaliação. Registre a escolha no checklist da mudança e retome a decisão quando a pessoa responsável pedir ou o escopo mudar de forma relevante. O fluxo simples continua com descoberta, regras e aceite explícitos, microentregas, revisão e verificações.

A pessoa que conduz a tarefa pode atuar em gestão, produto ou design. A revisão técnica de código e testes envolve a equipe de desenvolvimento, como no restante do guia.

## Se o projeto adotar OpenSpec

O checklist principal da mudança passa a ser `openspec/changes/<mudanca>/tasks.md`. O `task.md` da raiz é opcional e pode ser removido quando esse checklist assumir sua função. Antes de removê-lo, transfira tarefas e pendências para o checklist ou backlog mantido pelo projeto e atualize as referências ao arquivo. Se mantido, ele pode apontar para o checklist principal. Indique no `docs/README.md` onde consultar as especificações mantidas em `openspec/specs/` e reaproveite as referências existentes para manter uma fonte por informação.

Peça ao agente que prepare a proposta e os cenários, esclareça as decisões em aberto e proponha microentregas com contexto suficiente. O desenho técnico deve acompanhar as necessidades da mudança. [Artefatos e critérios do schema padrão](https://openspec.dev/docs/schemas/spec-driven)

A skill de implementação do OpenSpec normalmente percorre as tarefas até terminar ou encontrar um bloqueio. Ao autorizar a execução, delimite a microentrega, a pausa para revisão e a confirmação necessária para marcar seu checkbox. Confira esse comportamento no piloto de adoção. [Skill de implementação](https://github.com/Fission-AI/OpenSpec/blob/main/skills/openspec-apply-change/SKILL.md)

No encerramento, revise a implementação e as verificações, sincronize as mudanças confirmadas com as especificações mantidas e arquive a proposta conforme o processo do projeto. O OpenSpec preserva os artefatos da mudança no histórico. Esse custo de manutenção faz parte da avaliação de adoção. [Arquivamento e manutenção do histórico](https://openspec.dev/docs/quickstart)
