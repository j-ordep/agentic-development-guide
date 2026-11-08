# Guia de desenvolvimento com agentes de IA

Um guia prático para usar agentes em código que outras pessoas precisam revisar e manter. Comece por uma feature real e trabalhe com mudanças pequenas o suficiente para você entender, verificar e integrar.

## Catálogo

| Se você quer | Leia |
| --- | --- |
| Esclarecer o problema, levantar requisitos e comparar alternativas | [Descoberta de requisitos e arquitetura](descoberta.md) |
| Trabalhar com regras definidas, delegar microentregas e revisar o resultado | [Fluxo de execução](fluxo-de-trabalho.md) |
| Organizar a documentação do projeto e preparar a próxima feature | [Estrutura e modelos copiáveis](modelos.md) |

## O mínimo sobre agentes

O modelo de linguagem gera respostas com base no contexto que recebe. O agente usa o modelo e ferramentas para consultar arquivos, editar código e executar verificações. A janela de contexto limita o que o modelo consegue considerar de uma vez.

## Princípios de trabalho

- **Revise o que a IA produz.** Só aceite uma mudança se conseguir explicar o que ela faz, por que foi feita e como você verificou o resultado.
- **A IA amplifica o que você sabe e pode amplificar seus erros.** Conhecer o domínio ajuda a orientar a solução. Uma premissa errada pode se espalhar por toda a implementação.
- **O objetivo e os trade-offs são responsabilidade do dev.** Explicite o comportamento esperado, os limites, as concessões aceitáveis e como reconhecer que a tarefa está pronta. Peça ao agente que sinalize o que estiver ambíguo.
