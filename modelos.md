# Modelos para começar
## Estrutura de documentação para uma API

Na raiz, o `README.md` apresenta o projeto e como começar. O `AGENTS.md` define o papel do agente e indica onde estão as referências por tarefa. O `task.md` acompanha a feature atual. Em `docs/`, mantenha as informações que alguém precisará consultar para mudar o sistema com segurança.

### Conteúdo mínimo

| Informação | Onde registrar |
| --- | --- |
| Regras de negócio | Em um arquivo de `docs/`, descreva o comportamento esperado, as restrições e as exceções que afetam a implementação. |
| Contexto do projeto | Em `docs/README.md`, explique o problema, para quem o projeto existe e seus limites. |

### O que adicionar quando fizer falta

| Conteúdo opcional | Quando vale manter |
| --- | --- |
| Referência da API | Quando quem consome a API precisa consultar métodos, rotas, entradas, respostas e erros. Reaproveite a referência existente. |
| Visão do sistema | Quando entender como frontend, API, banco e outros serviços se conectam ajudar a avaliar o impacto de uma mudança. |
| Mapa da codebase | Quando explicar pontos de entrada, módulos e responsabilidades ajudar alguém a localizar uma mudança na API. |
| Decisões de arquitetura | Quando entender o contexto, a escolha e suas consequências ajudar a evitar retrabalho ou a reavaliar a decisão. |
| Índice dentro de `docs/README.md` | Quando localizar a referência certa começar a dar trabalho. |

Arquitetura e decisões podem compartilhar um arquivo curto. Separe a descrição de **como funciona hoje** da justificativa de **por que funciona assim**. Crie arquivos próprios quando o volume ou a forma de consulta justificar a divisão. [Leitura complementar sobre níveis de arquitetura](https://c4model.com/diagrams)

Se o projeto mantém uma especificação OpenAPI, como `openapi.yaml`, ou a gera a partir de esquemas no código, indique onde consultá-la e onde atualizar a fonte. Para uma referência simples em Markdown, `api.md` é um nome possível. Regras de negócio e a referência da API podem ficar no mesmo documento quando fizer sentido consultá-las juntas. [Leitura complementar sobre o formato OpenAPI](https://spec.openapis.org/oas/v3.2#openapi-description-structure)

### Quando atualizar

Documente apenas o que alguém precisará consultar para entender ou mudar o sistema. Atualize a referência existente no mesmo PR. Crie um arquivo apenas quando a informação durável precisar de um lugar próprio. Use links para manter uma fonte principal por informação. Quando a interface da API mudar, atualize o contrato. Quando o comportamento esperado mudar, atualize a regra de negócio correspondente. Num refactor interno, confira se alguma referência ou convenção documentada mudou. [Leitura complementar sobre documentação redundante](https://www.thoughtworks.com/pt-br/radar/techniques/ai-driven-documentation-sprawl)

### Integração entre frontend e backend

Mantenha uma referência compartilhada para a interface da API. No frontend, aponte para a OpenAPI da versão integrada, que pode ser consultada no Swagger UI, quando disponível. Use a documentação do frontend para detalhes próprios de consumo. Se a documentação divergir do endpoint, confira o código ou os testes de integração da versão usada e sinalize a diferença ao dev. [Leitura complementar sobre Swagger UI](https://swagger.io/open-source/swagger-ui/)

## AGENTS.md

Peça ao agente que adapte as instruções ao repositório e mostre o diff para revisão. A proposta deve descrever brevemente o papel dele e apontar para o contexto em `docs/README.md`, os comandos reais de verificação e as referências e exemplos de código. Se o projeto já usa skills, indique quando usar cada uma. Mantenha os passos do procedimento na própria skill.

```markdown
# Instruções do repositório

Seu papel é ajudar o dev a investigar, implementar e verificar a microentrega escolhida. Leia `docs/README.md` para entender o contexto do projeto.

## Referências e comandos

- Regras de negócio e contratos aplicáveis — indique os caminhos reais do projeto.
- Verificação — indique os comandos que o projeto usa para testes, lint ou build.

## Regras de trabalho

- Preserve os arquivos de infraestrutura, DevOps e CI/CD, Docker, configuração de ambiente e o `README.md` da raiz. Se a tarefa depender de uma mudança nesses arquivos, avise o dev para que ele a faça.
- Mantenha o `.env` fora de qualquer commit. Antes de commitar, confira os arquivos no stage.
- Antes de editar o código, consulte o `task.md`, as referências em `docs/` e os fluxos afetados no código. Separe o contexto e o checklist temporários das regras de negócio e dos contratos que vão continuar valendo.
- Quando faltarem decisões de negócio ou arquitetura, levante as perguntas que mudam a entrega e compare as opções. Se a proposta, a documentação ou o código divergirem, indique os arquivos, a diferença de comportamento e o impacto. Peça uma decisão ao dev antes de implementar a etapa afetada.
- Ao consumir uma API, consulte a referência da versão integrada. Se houver dúvida ou divergência, verifique o endpoint no código ou nos testes de integração e peça uma definição ao dev antes de mudar o consumidor.
- Quando a abordagem precisar de revisão ou a mudança for difícil de reverter, apresente um plano e aguarde a revisão antes de editar. Use o modo Plan quando estiver disponível.
- A partir do que o dev explicar, registre no `task.md` o objetivo, o aceite e a divisão em microentregas que você recomenda, com suas regras e verificações. O dev pode ajustar essa divisão ao revisar o plano. Execute a etapa autorizada e apresente qualquer ampliação de escopo para decisão antes de executá-la.
- Dimensione cada microentrega pelo contexto necessário para revisar um propósito. Ela pode ser uma alteração pontual, um conjunto de componentes relacionados ou um fluxo delimitado. Agrupe elementos que precisam ser lidos juntos e inclua o uso de uma constante ou struct quando ele for necessário para entender a mudança. Preserve os comportamentos fora do escopo aprovado.
- Rode as verificações aplicáveis à etapa. Cubra o comportamento novo e os fluxos existentes afetados. Para um bug reproduzível, adicione um teste de regressão e confirme que falha pelo motivo esperado antes da correção e passa depois.
- Ao devolver a etapa, informe o que mudou, quais comandos foram executados, os resultados e o que ainda precisa ser conferido, incluindo dependências das próximas etapas. Marque o item no `task.md` após a confirmação do dev e aguarde a autorização para avançar.
- No encerramento, proponha onde registrar o aprendizado validado. Use a referência mantida pelo projeto para regras e contratos e o `AGENTS.md` para instruções recorrentes de trabalho. Apresente o diff de instruções propostas para revisão antes de adotá-las.
- Documente só o necessário. No PR, atualize a fonte existente para regras e contratos afetados. Crie um documento apenas quando a informação durável precisar de um lugar próprio.
- Ao concluir a feature, limpe o contexto específico e os itens concluídos do task.md. Preserve as instruções do arquivo e as pendências adiadas.
```

## docs/README.md

Peça ao agente que registre o contexto confirmado para quem chega ao projeto e aponte para os arquivos que já detalham cada assunto.

```markdown
# Contexto do projeto

## Problema e público

Descreva que problema o projeto resolve e para quem.

## Escopo e limites

Resuma o que o projeto faz e as restrições que orientam mudanças.

## Referências

Indique onde consultar as regras de negócio e outras referências existentes.
```

## docs/regras-de-negocio.md

Peça ao agente que reaproveite a referência de regras do projeto e mantenha as dúvidas de comportamento no `task.md` até você confirmar a definição.

```markdown
# Regras de negócio

## Nome da regra

Descreva quando a regra se aplica, qual comportamento deve ocorrer e quais exceções precisam ser respeitadas. Inclua um exemplo se ajudar a entender.
```

## task.md

O agente mantém este arquivo durante a feature e marca as microentregas após a revisão e a confirmação do dev. No encerramento, preserva a estrutura e os itens abertos de **Deixado para depois**.

```markdown
# Tarefa atual

## Contexto e aceite

Descreva o resultado esperado, os limites da mudança e como verificar o comportamento.

## Regras, contratos e impacto

Aponte para as referências em docs/ e para o código relevante. Registre as regras novas, as decisões confirmadas, as dúvidas em aberto e os fluxos afetados.

## Microentregas

- [ ] Descreva a microentrega, as regras aplicáveis e como conferir a etapa.

## Deixado para depois

Mantenha cada pendência como checkbox aberto.

- [ ] Nome da microentrega adiada
  - Descrição — Registre o que ficou pendente.
  - Status — Indique o que já foi revisado e o que falta resolver.
```
