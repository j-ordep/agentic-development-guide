# Ponto de entrada para agentes

Use este arquivo quando o dev pedir para aplicar o guia em um repositório. Confirme o projeto de destino e o acesso às páginas vinculadas. Leia as instruções locais, o contexto e as regras de negócio que já existirem. Se houver conflito com o guia, aponte a diferença ao dev antes de alterar a parte afetada.

## O que ler

1. [README do guia](README.md) para entender os princípios de trabalho e a separação entre contexto, regras e tarefa.
2. [Estrutura e modelos](modelos.md) para consultar os arquivos copiáveis e os limites de atuação.
3. [Fluxo de execução](fluxo-de-trabalho.md) para entender como planejar, implementar e devolver uma microentrega. Quando faltarem decisões de negócio ou arquitetura, leia também [Descoberta](descoberta.md).

## Se a tarefa for preparar o repositório

Adapte estes modelos ao projeto de destino. Reaproveite arquivos que já cumprem a mesma função e preserve as regras locais.

| Arquivo de destino | O que preparar |
| --- | --- |
| `AGENTS.md` | Papel do agente, regras, comandos reais de verificação e caminhos para as referências. [Modelo](modelos.md#agentsmd) |
| `docs/README.md` | Problema, público e limites do projeto. [Modelo](modelos.md#docsreadmemd) |
| `docs/regras-de-negocio.md` | Regras confirmadas ou links para a referência de regras existente. [Modelo](modelos.md#docsregras-de-negociomd) |
| `task.md` | Estrutura reutilizável para a feature atual e as pendências adiadas. Preserve o conteúdo de uma tarefa que já esteja em andamento. [Modelo](modelos.md#taskmd) |

Preencha com o que puder confirmar no projeto. Leve ao dev as dúvidas sobre comportamento ou comandos. Aplique os limites do modelo de `AGENTS.md` ao preparar o repositório e apresente para revisão o diff dos arquivos criados ou adaptados.

## Se a tarefa for trabalhar em uma feature

A partir da conversa com o dev, registre no `task.md` o objetivo, as regras afetadas e como conferir cada etapa. Apresente o plano para revisão e siga o fluxo de execução para implementar, manter o checklist e atualizar as referências duráveis.
