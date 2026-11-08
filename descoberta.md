# Descoberta de requisitos e arquitetura

[Voltar ao catálogo](README.md)

Comece por aqui quando a próxima mudança depender de regras, dados ou decisões técnicas em aberto. Isso é comum no início de um projeto e também acontece quando um sistema existente ganha um fluxo novo. Use o agente para investigar, fazer perguntas e comparar opções.

## Trabalhe em pequenas etapas de descoberta

1. **Entenda o problema.** Quem precisa do resultado, o que faz hoje e como saberemos que melhorou? Que dados e exemplos reais já existem? Separe fatos, hipóteses e dúvidas.
2. **Resolva as perguntas que mudam a entrega.** Peça ao agente que agrupe as dúvidas por impacto. Em um projeto existente, ele também deve ler `docs/` e o código relevante para descobrir o que já foi decidido. No exemplo do filtro, vale esclarecer quem pode consultar os dados, quais campos são necessários e como combinar os critérios.
3. **Compare as opções relevantes.** Para cada alternativa, peça ao agente que explique custo, risco e dificuldade de reverter. A equipe decide o escopo e a arquitetura necessária para o primeiro incremento. Se uma dúvida pedir evidência, trate um protótipo isolado ou a verificação de um contrato como uma microentrega de descoberta.

## Passe para execução quando a próxima entrega estiver clara

Use o `task.md` para marcar as etapas de descoberta já revisadas e registrar o objetivo, as decisões confirmadas e como verificar a primeira microentrega. Para o filtro, ela pode ser uma listagem paginada com campos e acesso definidos. Quando uma dúvida impedir a etapa seguinte, volte à descoberta para resolver aquele ponto. [Ir para o fluxo de execução](fluxo-de-trabalho.md)

[Leitura complementar sobre requisitos, contratos e critérios de aceite](https://www.thoughtworks.com/pt-br/insights/blog/agile-engineering-practices/spec-driven-development-unpacking-2025-new-engineering-practices)
