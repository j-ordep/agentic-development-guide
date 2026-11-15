# Guia de desenvolvimento com agentes de IA

> **V2 não validada.** O fluxo atual já define objetivos, regras, critérios de aceite e microentregas revisáveis. Ainda estamos avaliando se adotar OpenSpec ou TLC Spec-Driven traz ganhos que compensam a documentação e a manutenção adicionais. O fluxo padrão está na branch [main](https://github.com/j-ordep/agentic-development-guide/tree/main).
>
> Como contraponto, Fábio Akita escreve “Não preciso de framework” ao descrever seu fluxo com objetivos claros, testes e feedback curto. Em sua crítica a SDD, questiona a especificação extensa como padrão para todos e reconhece valor em documentos de desenho para equipes grandes, sistemas legados e trabalho assíncrono. [Relato sobre seu fluxo](https://akitaonrails.com/2026/04/15/como-falar-com-o-claude-code-efetivamente/) · [Crítica a SDD](https://akitaonrails.com/en/2026/08/18/hot-take-harness-loop-engineering-graph-engineering-are-bullshit/)
>
> - **Especificações também podem ser ambíguas.** Um documento detalhado pode deixar decisões importantes em aberto, que aparecem durante a implementação.
> - **Documentação custa manutenção.** Depois de correções e mudanças no código, a especificação pode ficar desatualizada e passar informações erradas ao próximo agente.
> - **Parte dos requisitos é descoberta construindo.** Planejar demais antecipadamente pode aumentar o esforço de corrigir decisões que um incremento pequeno teria revelado.

Trabalhe em dupla com um agente de IA e mantenha o controle do código e das regras de negócio.

Neste guia, a pessoa responsável pela tarefa é quem conduz o trabalho com o agente. Ela pode atuar em desenvolvimento, gestão, produto ou design.

## Por que este guia existe

Quando o agente altera mais do que a tarefa pede, uma mudança pequena pode virar um PR difícil de revisar. Fica mais difícil entender o que mudou e perceber se alguma regra de negócio foi quebrada. A documentação tem um problema parecido. Quando vários arquivos descrevem a mesma regra, eles podem divergir e deixar a pessoa responsável e o agente em dúvida sobre qual seguir.

A proposta é usar o agente como parceiro de programação. Você explica o objetivo e discute com ele os requisitos e as decisões técnicas. O agente faz perguntas, registra o plano no checklist da mudança e implementa uma microentrega por vez, alterando só o necessário para aquela etapa. No fluxo simples, o checklist fica no `task.md`. Você revisa o diff, confere os testes e valida as regras de negócio antes de avançar. No PR, o time revisa a feature integrada.

No mesmo PR, o agente atualiza só as referências necessárias, reaproveitando a documentação existente. No fluxo simples, depois do merge ele limpa o contexto da feature e as etapas concluídas do `task.md`, preservando o modelo e as pendências. Com uma ferramenta de SDD adotada, siga o [procedimento correspondente](sdd.md#se-o-projeto-adotar-uma-ferramenta-de-sdd).

## Princípios de trabalho

- **Revise o que a IA produz**. Se você não consegue explicar uma mudança, você não está pronto pra aceitar ela. Envolva a equipe de desenvolvimento na revisão técnica de código e testes.
- **A IA amplifica o que você sabe e pode amplificar seus erros.** Conhecer o domínio ajuda a orientar a solução. Uma premissa errada pode se espalhar por toda a implementação.
- **O objetivo e os trade-offs são responsabilidade de quem conduz a tarefa.** Explicite o comportamento esperado, os limites, as concessões aceitáveis e como reconhecer que a tarefa está pronta. Peça ao agente que sinalize o que estiver ambíguo.

## Catálogo

| Se você quer | Leia |
| --- | --- |
| Esclarecer o problema, levantar requisitos e comparar alternativas | [Descoberta de requisitos e arquitetura](descoberta.md) |
| Trabalhar com regras definidas, delegar microentregas e revisar o resultado | [Fluxo de execução](fluxo-de-trabalho.md) |
| Organizar a documentação do projeto e preparar a próxima feature | [Estrutura e modelos copiáveis](modelos.md) |
| Avaliar uma ferramenta de SDD e seguir com o fluxo disponível no projeto | [SDD, OpenSpec e TLC Spec-Driven](sdd.md) |
| Orientar o agente a aplicar o guia no seu projeto | [Ponto de entrada para agentes](PARA-AGENTES.md) |

## Para passar o guia a um agente

Entregue o [ponto de entrada para agentes](PARA-AGENTES.md), dê acesso aos arquivos do guia que ele referencia e indique o repositório de destino. O arquivo distingue o preparo do projeto da execução de uma feature.

## Documentação do projeto

Peça ao agente que prepare ou adapte os arquivos do projeto. Em `docs/`, comece com as regras de negócio e um `docs/README.md` que explique o problema que o projeto resolve, para quem e com quais limites. Se as regras já estiverem em especificações mantidas pelo projeto, indique esse caminho no índice. Revise o `AGENTS.md` proposto para confirmar o papel do agente, as regras de trabalho e as referências que ele deve consultar.

A estrutura de `docs/` varia com o tamanho e as necessidades do projeto. Documente só o que ajuda a entender ou mudar o sistema. Prefira atualizar um documento existente e crie um arquivo novo quando a informação durável precisar de um lugar próprio. Uma referência separada da API, um mapa de arquitetura e um registro de decisões são opcionais. [Estrutura e exemplos de organização](modelos.md#estrutura-de-documentação-para-uma-api)

## O mínimo sobre agentes

O modelo de linguagem gera respostas com base no contexto que recebe. O agente usa o modelo e ferramentas para consultar arquivos, editar código e executar verificações. A janela de contexto limita o que o modelo consegue considerar de uma vez.
