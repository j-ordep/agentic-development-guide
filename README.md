# Guia de desenvolvimento com agentes de IA

Trabalhe em dupla com um agente de IA e mantenha o controle do código e das regras de negócio.

## Por que este guia existe

Quando o agente altera mais do que a tarefa pede, uma mudança pequena pode virar um PR difícil de revisar. Fica mais difícil entender o que mudou e perceber se alguma regra de negócio foi quebrada. A documentação tem um problema parecido. Quando vários arquivos descrevem a mesma regra, eles podem divergir e deixar o dev e o agente em dúvida sobre qual seguir.

A proposta é usar o agente como parceiro de programação. Você explica o objetivo e discute com ele os requisitos e as decisões técnicas. O agente faz perguntas, registra o plano no `task.md` e implementa uma microentrega por vez, alterando só o necessário para aquela etapa. Você revisa o diff, confere os testes e valida as regras de negócio antes de avançar. No PR, o time revisa a feature integrada.

No mesmo PR, o agente atualiza em `docs/` só o que precisa continuar valendo, reaproveitando as referências existentes. Depois do merge, ele limpa o contexto da feature e as etapas concluídas do `task.md`, preservando o modelo e as pendências.

## Princípios de trabalho

- **Revise o que a IA produz**. Se você não consegue explicar uma mudança, você não está pronto pra aceitar ela.
- **A IA amplifica o que você sabe e pode amplificar seus erros.** Conhecer o domínio ajuda a orientar a solução. Uma premissa errada pode se espalhar por toda a implementação.
- **O objetivo e os trade-offs são responsabilidade do dev.** Explicite o comportamento esperado, os limites, as concessões aceitáveis e como reconhecer que a tarefa está pronta. Peça ao agente que sinalize o que estiver ambíguo.

## Catálogo

| Se você quer | Leia |
| --- | --- |
| Esclarecer o problema, levantar requisitos e comparar alternativas | [Descoberta de requisitos e arquitetura](descoberta.md) |
| Trabalhar com regras definidas, delegar microentregas e revisar o resultado | [Fluxo de execução](fluxo-de-trabalho.md) |
| Organizar a documentação do projeto e preparar a próxima feature | [Estrutura e modelos copiáveis](modelos.md) |
| Orientar o agente a aplicar o guia no seu projeto | [Ponto de entrada para agentes](PARA-AGENTES.md) |

## Para passar o guia a um agente

Entregue o [ponto de entrada para agentes](PARA-AGENTES.md), dê acesso aos arquivos do guia que ele referencia e indique o repositório de destino. O arquivo distingue o preparo do projeto da execução de uma feature.

## Documentação do projeto

Peça ao agente que prepare ou adapte os arquivos do projeto. Em `docs/`, comece com as regras de negócio e um `docs/README.md` que explique o problema que o projeto resolve, para quem e com quais limites. Revise o `AGENTS.md` proposto para confirmar o papel do agente, as regras de trabalho e as referências que ele deve consultar.

A estrutura de `docs/` varia com o tamanho e as necessidades do projeto. Documente só o que ajuda a entender ou mudar o sistema. Prefira atualizar um documento existente e crie um arquivo novo quando a informação durável precisar de um lugar próprio. Uma referência separada da API, um mapa de arquitetura e um registro de decisões são opcionais. [Estrutura e exemplos de organização](modelos.md#estrutura-de-documentação-para-uma-api)

## O mínimo sobre agentes

O modelo de linguagem gera respostas com base no contexto que recebe. O agente usa o modelo e ferramentas para consultar arquivos, editar código e executar verificações. A janela de contexto limita o que o modelo consegue considerar de uma vez.
