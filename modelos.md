# Modelos para começar

[Voltar ao catálogo](README.md)

## Estrutura de documentação para uma API

Use esta estrutura como ponto de partida e adapte os caminhos aos arquivos que o projeto já mantém.

```text
README.md
AGENTS.md
task.md
docs/
  regras-de-negocio.md
  contratos-api.md
```

- **`README.md`** explica para que serve o projeto e como começar.
- **`AGENTS.md`** dá as instruções de trabalho e aponta para as referências por tarefa. Ao mudar um endpoint, por exemplo, consulte o contrato e as regras do domínio afetado.
- **`task.md`** reúne o contexto temporário e as microentregas da feature atual.
- **`docs/`** guarda o comportamento esperado, as exceções e os contratos da API, com parâmetros, respostas e erros relevantes. Regras e contratos podem ficar juntos se isso facilitar a leitura. Se o contrato já estiver em OpenAPI, aponte para a especificação existente.

Registre decisões de arquitetura quando a justificativa ajudar uma mudança futura. Adicione um `docs/README.md` quando a quantidade de arquivos justificar um índice. [Leitura complementar sobre documentação de projeto](https://akitaonrails.com/2026/05/30/boas-praticas-projetos-codigo-aberto-llm-o-minimo/)

## AGENTS.md

Adapte as instruções ao repositório. Inclua os caminhos reais das regras de negócio, dos contratos e dos exemplos de código, além dos comandos que o projeto já usa para verificar mudanças.

```markdown
# Instruções do repositório

- Antes de editar, leia o task.md. Separe o contexto e o checklist temporários das regras de negócio e dos contratos que vão continuar valendo. Consulte docs/ e confira como o código e os fluxos dependentes se comportam hoje.
- Quando faltarem decisões de negócio ou arquitetura, levante as perguntas que mudam a entrega e compare as opções. Se a proposta, a documentação ou o código divergirem, indique os arquivos, a diferença de comportamento e o impacto. Peça uma decisão ao dev antes de implementar a etapa afetada.
- Mapeie as regras para as microentregas e execute somente a etapa selecionada pelo dev. Preserve os comportamentos fora do escopo aprovado.
- Rode as verificações aplicáveis à etapa. Cubra o comportamento novo e os fluxos existentes afetados. Para um bug reproduzível, adicione um teste de regressão e confirme que falha antes da correção e passa depois.
- Ao devolver a etapa, informe o que mudou, quais comandos foram executados, os resultados e o que ainda precisa ser conferido. Aguarde a revisão do dev antes de avançar.
- No encerramento, proponha onde registrar o aprendizado validado. Use docs/ para regras e contratos e o AGENTS.md para instruções recorrentes de trabalho. Submeta novas instruções à revisão do dev.
- Com a feature concluída, registre em docs/ as definições confirmadas e limpe o contexto específico e os itens concluídos do task.md. Preserve as instruções do arquivo e as pendências adiadas.
```

## task.md

Use o arquivo para trabalhar na feature atual. Ao encerrar, mantenha a estrutura e os itens abertos de **Deixado para depois**. O dev marca as microentregas revisadas.

```markdown
# Tarefa atual

## Contexto e aceite

Descreva o resultado esperado, os limites da mudança e como verificar o comportamento.

## Regras, contratos e impacto

Aponte para as referências em docs/ e para o código relevante. Registre as regras novas, as decisões confirmadas, as dúvidas em aberto e os fluxos afetados.

## Microentregas

- [ ] Descreva a microentrega, as regras aplicáveis e como conferir a etapa.

## Deixado para depois

Mantenha cada pendência como checkbox aberto, com descrição, status e o que falta resolver.
```

Por exemplo, se o filtro por tempo de empresa ficar para depois, mantenha um item como este.

```markdown
- [ ] Definir o cálculo do tempo de empresa.
  - Descrição — A listagem deverá aceitar um filtro por tempo de vínculo.
  - Status — Revisado. Falta definir como tratar períodos de afastamento.
```
