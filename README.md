# Guia de desenvolvimento com agentes de IA

Um guia prático para usar agentes em código que outras pessoas precisam revisar e manter. Comece por uma feature real e trabalhe com mudanças pequenas o suficiente para você entender, verificar e integrar.

## Catálogo

| Se você quer | Leia |
| --- | --- |
| Esclarecer o problema, levantar requisitos e comparar alternativas | [Descoberta de requisitos e arquitetura](descoberta.md) |
| Trabalhar com regras definidas, delegar microentregas e revisar o resultado | [Fluxo de execução](fluxo-de-trabalho.md) |
| Organizar a documentação do projeto e preparar a próxima feature | [Estrutura e modelos copiáveis](modelos.md) |

## Para passar o guia a um agente

Entregue o [ponto de entrada para agentes](PARA-AGENTES.md) e diga em qual repositório ele deve trabalhar. O arquivo indica o que ler e distingue o preparo do projeto da execução de uma feature.

## Documentação do projeto

Comece com um arquivo de regras de negócio em `docs/` e um `docs/README.md` que explique o problema que o projeto resolve, para quem e com quais limites. Use o `AGENTS.md` para descrever o papel do agente, as regras de trabalho e as referências que ele deve consultar.

A estrutura de `docs/` varia com o tamanho e as necessidades do projeto. Documente só o que ajuda a entender ou mudar o sistema. Prefira atualizar um documento existente e crie um arquivo novo quando a informação durável precisar de um lugar próprio. Uma referência separada da API, um mapa de arquitetura e um registro de decisões são opcionais. [Estrutura e exemplos de organização](modelos.md#estrutura-de-documentação-para-uma-api)

## O mínimo sobre agentes

O modelo de linguagem gera respostas com base no contexto que recebe. O agente usa o modelo e ferramentas para consultar arquivos, editar código e executar verificações. A janela de contexto limita o que o modelo consegue considerar de uma vez.

## Princípios de trabalho

- **Revise o que a IA produz**. Se você não consegue explicar uma mudança, você não está pronto pra aceitar ela.
- **A IA amplifica o que você sabe e pode amplificar seus erros.** Conhecer o domínio ajuda a orientar a solução. Uma premissa errada pode se espalhar por toda a implementação.
- **O objetivo e os trade-offs são responsabilidade do dev.** Explicite o comportamento esperado, os limites, as concessões aceitáveis e como reconhecer que a tarefa está pronta. Peça ao agente que sinalize o que estiver ambíguo.
