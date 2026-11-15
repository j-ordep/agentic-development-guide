# SDD, OpenSpec e TLC Spec-Driven

Proposta da v2, em avaliação. O fluxo padrão do guia está na branch [main](https://github.com/j-ordep/agentic-development-guide/tree/main). Esta página detalha alternativas para quem solicitar a avaliação de SDD.

O desenvolvimento orientado por especificações (SDD) explicita o comportamento esperado, os cenários e os critérios de aceite para orientar a implementação e a revisão. O agente ajuda a esclarecer e registrar essas definições, que evoluem com as decisões confirmadas. O fluxo simples do guia já registra objetivo, regras e aceite no `task.md`.

OpenSpec e TLC Spec-Driven fornecem procedimentos para especificar, implementar e verificar uma mudança. Escolha a alternativa conforme o projeto e o nível de automação autorizado.

## Quando avaliar uma ferramenta de SDD

Quando a pessoa responsável solicitar essa análise, avalie o benefício de alinhar várias regras e exceções, registrar a mudança de um contrato compartilhado ou manter uma referência entre pessoas e sessões. Explique também o esforço de documentação acrescentado. A escolha de uma ferramenta depende da aprovação para aquele projeto e finalidade.

Na descoberta, esclareça as decisões necessárias para o próximo incremento e registre o que for confirmado. Durante a execução, mantenha essas definições alinhadas ao comportamento aprovado.

## Alternativas a avaliar

| Alternativa | O que acrescenta | O que considerar |
| --- | --- | --- |
| OpenSpec | Specs mantidas, propostas de mudança e checklist de implementação. | Atualização das specs e histórico das mudanças. [Documentação](https://openspec.dev/docs/quickstart) |
| TLC Spec-Driven | Rastreabilidade entre requisitos, tarefas e commits, com verificação por um segundo agente. | Automação de commits e verificações que precisa ser conciliada com o processo da equipe. [Documentação](https://agent-skills.techleads.club/tlc-spec-driven/) |

## Se a ferramenta estiver ausente ou ainda sem aprovação

Confira nas instruções e nos arquivos do projeto qual fluxo está adotado e se a ferramenta está disponível no ambiente em que o agente trabalha. A disponibilidade da ferramenta e a autorização para usá-la são verificações distintas. Siga a [diretriz de aprovação para skills](fluxo-de-trabalho.md#uso-de-skills) e peça aprovação antes de instalar, configurar ou executar uma ferramenta nova.

Se a pessoa tiver solicitado a avaliação e a escolha estiver em aberto, apresente as opções uma vez durante o planejamento. Use uma mensagem como esta, preenchendo o motivo com o contexto real da tarefa.

> Você pediu para avaliar SDD nesta mudança, que altera um contrato compartilhado. Posso continuar com `task.md` e microentregas ou você prefere avaliar a adoção de OpenSpec ou TLC Spec-Driven?

Se o fluxo atual já estiver autorizado, prossiga com ele. Registre a decisão no checklist da mudança e retome a avaliação de SDD quando a pessoa responsável solicitar. O fluxo simples continua com descoberta, regras e aceite explícitos, microentregas, revisão e verificações.

A pessoa que conduz a tarefa pode atuar em gestão, produto ou design. A revisão técnica de código e testes envolve a equipe de desenvolvimento, como no restante do guia.

## Se o projeto adotar uma ferramenta de SDD

Registre a alternativa e o escopo aprovados nas instruções do projeto. Use um checklist principal por mudança e mantenha as pausas de revisão local das microentregas. A pessoa responsável valida os critérios de aceite, e a equipe de desenvolvimento faz a revisão técnica do código e dos testes.

### OpenSpec

O checklist principal da mudança passa a ser `openspec/changes/<mudanca>/tasks.md`. O `task.md` da raiz é opcional e pode ser removido quando esse checklist assumir sua função. Antes de removê-lo, transfira tarefas e pendências para o checklist ou backlog mantido pelo projeto e atualize as referências ao arquivo. Se mantido, ele pode apontar para o checklist principal. Indique no `docs/README.md` onde consultar as especificações mantidas em `openspec/specs/` e reaproveite as referências existentes para manter uma fonte por informação.

Peça ao agente que prepare a proposta e os cenários, esclareça as decisões em aberto e proponha microentregas com contexto suficiente. O desenho técnico deve acompanhar as necessidades da mudança. [Artefatos e critérios do schema padrão](https://openspec.dev/docs/schemas/spec-driven)

A skill de implementação do OpenSpec normalmente percorre as tarefas até terminar ou encontrar um bloqueio. Ao autorizar a execução, delimite a microentrega, a pausa para revisão e a confirmação necessária para marcar seu checkbox. Confira esse comportamento no piloto de adoção. [Skill de implementação](https://github.com/Fission-AI/OpenSpec/blob/main/skills/openspec-apply-change/SKILL.md)

No encerramento, revise a implementação e as verificações, sincronize as mudanças confirmadas com as especificações mantidas e arquive a proposta conforme o processo do projeto. O OpenSpec preserva os artefatos da mudança no histórico. Esse custo de manutenção faz parte da avaliação de adoção. [Arquivamento e manutenção do histórico](https://openspec.dev/docs/quickstart)

### TLC Spec-Driven

O TLC é distribuído como uma skill. Seu procedimento documentado começa pela especificação e inclui desenho técnico e lista de tarefas conforme a complexidade. A execução prevê commits atômicos e uma verificação independente por subagente. Confira o procedimento da versão escolhida e seus requisitos antes de aprovar o uso. [Procedimento e código-fonte](https://agent-skills.techleads.club/tlc-spec-driven/)

Combine previamente as pausas para revisão, a autorização de commits e o uso do verificador. A aprovação para usar a skill deve esclarecer essas ações. Se o procedimento conflitar com as regras do projeto ou com a revisão de cada microentrega, apresente o conflito para decisão antes de executar a parte afetada.

Use os artefatos previstos pela versão aprovada do TLC como referência para a mudança e indique seus caminhos nas instruções do projeto. O `task.md` da raiz pode ser removido após transferir tarefas e pendências e atualizar suas referências, ou pode apontar para o checklist mantido.

## Como avaliar a adoção

Compare o fluxo atual com a alternativa escolhida em mudanças delimitadas. Para observar o efeito da ferramenta, mantenha modelo, esforço e ambiente comparáveis. Registre retrabalho, mudanças fora do escopo, esforço de revisão e documentação a manter.

Uma avaliação publicada pelo autor do vídeo usa um único PRD e encontra resultados próximos entre algumas configurações. O artigo distingue os modelos comparados e informa que os gates de engenharia das execuções com framework ficaram sem execução. Esses limites pedem validação no próprio projeto. [Vídeo sobre o benchmark](https://www.youtube.com/watch?v=gK1atE0ssfg) · [Análise escrita e metodologia](https://www.techleads.club/c/blog/spec-driven-em-2026-testei-speckit-superpowers-tlc-e-openspec-contra-um-modelo-puro-analise-completa)

Confira se os testes comprovam os critérios de aceite e execute as verificações do projeto. A quantidade de testes e uma pontuação de avaliação são informações complementares à evidência de que o comportamento funciona.
