# Regra de sessão e handoff

> leitor: agente

## Objetivo

Registrar o estado de uma sessão de trabalho para que outra sessão possa
retomar a tarefa sem depender do histórico da conversa.

## Quando salvar

Só crie ou atualize um handoff quando o usuário pedir explicitamente para:

- salvar a sessão;
- salvar um handoff;
- registrar o estado para continuar depois;
- gerar um resumo de retomada.

Não crie handoffs automaticamente ao final de toda tarefa. O handoff não
substitui a spec, o plano, as tasks ou a documentação permanente do projeto.

## Local e unidade de arquivo

- salve os arquivos em `docs/handoff/`;
- cada arquivo representa uma única sessão;
- não misture duas sessões no mesmo arquivo;
- crie o diretório quando ele ainda não existir.

Use o nome `YYYY-MM-DD-<identificador-da-sessao>.md`. O identificador deve ser
curto, estável, minúsculo e usar hífens no lugar de espaços.

## Conteúdo obrigatório

Cada handoff deve conter:

```markdown
# Handoff: <título da sessão>

- Data: <YYYY-MM-DD>
- Escopo: projeto | módulo | serviço | documentação
- Status: em andamento | bloqueada | concluída

## Objetivo

<o que a sessão pretendia realizar>

## O que foi feito

- <alteração ou decisão verificável>

## Estado atual

<estado real ao salvar, incluindo o que ainda falta>

## Arquivos relevantes

- <caminho>: <por que é relevante>

## Comandos e verificações

- `<comando>`: <resultado>

## Bloqueios e decisões pendentes

- <bloqueio, dúvida ou aprovação necessária; escreva "Nenhum" quando não houver>

## Próximos passos

1. <próxima ação executável>
```

Inclua somente fatos observados na sessão, respostas do usuário ou informações
presentes em arquivos lidos. Diferencie claramente fato, hipótese e decisão
pendente. Registre falhas de teste, build e comandos incompletos sem ocultá-las.

## Relação com o SDD

Quando a sessão envolver uma tarefa de produto ou código, referencie os
artefatos existentes de `rules/spec-flow.md`:

- spec em `docs/specs/`;
- plano em `plans/`;
- tasks em `tasks/`.

O handoff deve registrar a última task concluída, a task atual e os critérios
`CA-xx` relacionados quando esses artefatos existirem.

## Segurança e histórico

- não registre senhas, tokens, chaves, dados pessoais desnecessários ou outros
  segredos;
- não reescreva nem apague handoffs de sessões anteriores sem pedido explícito;
- preserve os handoffs no repositório para manter o histórico de decisões;
- não crie commit; essa ação fica com o usuário.
