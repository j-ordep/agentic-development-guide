# Modelos para começar

[Voltar ao catálogo](README.md)

## AGENTS.md

Adapte as instruções ao repositório. Inclua os caminhos reais das regras de negócio, dos contratos e dos exemplos de código, além dos comandos que o projeto já usa para verificar mudanças.

```markdown
# Instruções do repositório

- Antes de editar, leia o task.md e localize em docs/ as regras de negócio e os contratos afetados. Confira o comportamento atual no código e os fluxos que dependem dele.
- Se a proposta, a documentação ou o código entrarem em conflito, indique os arquivos, a diferença de comportamento e o impacto. Peça uma decisão ao dev antes de implementar a etapa afetada.
- Mapeie as regras para as microentregas e execute somente a etapa selecionada pelo dev. Preserve os comportamentos fora do escopo aprovado.
- Ao devolver a etapa, informe o que mudou, quais verificações foram executadas e o que ainda precisa ser conferido. Aguarde a revisão do dev antes de avançar.
- No encerramento, proponha onde registrar o aprendizado validado. Use um teste para cobrir uma regressão reproduzível, docs/ para regras e contratos e o AGENTS.md para instruções recorrentes de trabalho. Submeta novas instruções à revisão do dev.
- Com a feature concluída, registre em docs/ as definições confirmadas e limpe o contexto específico e os itens concluídos do task.md. Preserve as instruções do arquivo e as pendências adiadas.
```

## task.md

Use o arquivo para trabalhar na feature atual. Ao encerrar, mantenha a estrutura e os itens abertos de **Deixado para depois**. O dev marca as microentregas revisadas.

```markdown
# Tarefa atual

## Contexto e aceite

Descreva o resultado esperado, os limites da mudança e como verificar o comportamento.

## Regras, contratos e impacto

Aponte para as referências em docs/ e para o código relevante. Registre as regras novas, os conflitos encontrados e os fluxos afetados.

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
