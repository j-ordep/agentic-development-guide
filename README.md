# Guia de desenvolvimento com agentes de IA

Um guia prático para usar agentes em código que outras pessoas precisam revisar e manter. Comece por uma feature real e trabalhe com mudanças pequenas o suficiente para você entender, verificar e integrar.

## Catálogo

| Se você quer | Leia |
| --- | --- |
| Planejar uma feature, delegar microentregas e revisar o resultado | [Fluxo de trabalho](fluxo-de-trabalho.md) |
| Preparar o repositório e organizar a próxima feature | [Modelos de AGENTS.md e task.md](modelos.md) |

## O mínimo sobre agentes

O modelo de linguagem gera respostas com base no contexto que recebe. O agente usa o modelo e ferramentas para consultar arquivos, editar código e executar verificações. A janela de contexto limita o que o modelo consegue considerar de uma vez. Dê ao agente o objetivo, as regras relevantes e uma forma de verificar a saída. Use o diff e os resultados das verificações para decidir o que aceitar.
