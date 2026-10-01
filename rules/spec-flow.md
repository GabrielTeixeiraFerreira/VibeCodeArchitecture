# Fluxo de desenvolvimento orientado por especificação

> leitor: agente

## Objetivo

Toda mudança de produto ou código deve seguir o processo SDD (Spec-Driven
Development): especificação, plano, tarefas, implementação e verificação.
O código deve ser consequência dos requisitos registrados, não a fonte
principal de decisão do comportamento.

## Quando aplicar

Use este fluxo para:

- criar ou alterar uma funcionalidade em uma parte do projeto;
- alterar contratos entre módulos, serviços, integrações ou bibliotecas compartilhadas;
- criar ou alterar schema, migration, autenticação, autorização ou integrações;
- corrigir um bug que mude comportamento observável.

Para mudanças puramente editoriais, de documentação ou de configuração sem
efeito comportamental, registre a justificativa na resposta e siga diretamente
para a verificação aplicável.

## Ordem obrigatória

### 1. Entender o escopo

Antes de investigar ou editar código:

1. confirme o escopo da mudança no projeto e quais áreas, módulos ou serviços serão afetados;
2. leia os documentos do produto e da arquitetura relevantes;
3. identifique o comportamento atual, os pontos de entrada e as restrições;
4. registre dúvidas que não possam ser resolvidas pelo repositório.

Se o escopo ou o comportamento esperado estiver ambíguo, pergunte ao usuário
antes de escrever a especificação.

### 2. Escrever a spec

Crie uma especificação em `docs/specs/<identificador>.md` contendo, no mínimo:

- contexto e problema;
- objetivo e fora de escopo;
- usuários ou sistemas envolvidos;
- comportamento esperado;
- regras de negócio e estados relevantes;
- critérios de aceitação numerados como `CA-01`, `CA-02`, etc.;
- riscos, dependências e dúvidas abertas.

Cada critério de aceitação deve ser observável e verificável. Não escreva
requisitos que não tenham origem no pedido do usuário ou em um documento lido
no repositório. Quando a decisão depender do usuário, pare e peça aprovação.

### 3. Escrever o plano

Depois da spec, crie `plans/<identificador>.md` com:

- arquivos ou módulos que serão criados ou alterados;
- abordagem técnica compatível com a arquitetura do projeto;
- ordem de execução;
- estratégia de testes e build;
- impacto em dados, contratos, segurança e operação;
- relação entre cada etapa e os critérios `CA-xx`.

O plano não deve introduzir requisitos novos. Se revelar uma decisão de
produto ou arquitetura ausente, atualize a spec e aguarde a aprovação
necessária antes de implementar.

### 4. Decompor em tasks

Crie `tasks/<identificador>.md` com tarefas pequenas, ordenadas e executáveis.
Cada tarefa deve conter:

- identificador único, como `T-01`;
- descrição da mudança;
- arquivos ou área afetada;
- critérios `CA-xx` atendidos;
- comando ou verificação esperada;
- estado: `pendente`, `em andamento`, `bloqueada` ou `concluída`.

Uma task deve ser concluída em uma alteração coerente e validada. Não agrupe
mudanças sem relação apenas para reduzir a quantidade de tasks.

### 5. Aprovar antes de implementar

Apresente ao usuário o resumo da spec, do plano e das tasks. Não implemente
quando houver decisão de produto, arquitetura, segurança ou schema pendente.
Comece a editar somente após o usuário aprovar ou autorizar explicitamente a
execução.

### 6. Implementar e manter rastreabilidade

Execute as tasks na ordem definida. Ao encontrar uma mudança de escopo:

1. pare a task atual;
2. atualize spec, plano e tasks afetados;
3. explique o impacto e peça aprovação quando necessário;
4. só então retome a implementação.

Não marque uma task como concluída sem executar sua verificação. Não crie
commits; essa ação fica com o usuário.

### 7. Verificar e encerrar

Ao final:

1. execute os testes e o build aplicáveis;
2. siga `rules/check.md`;
3. para schema ou migration, siga também `rules/migration.md`;
4. confirme que cada `CA-xx` foi atendido ou registre a razão de não ter sido;
5. rode `git status --short` e confira se só há alterações no escopo;
6. atualize os estados das tasks;
7. informe os comandos executados e a última linha de cada saída relevante.

Falha em teste, build ou verificação impede declarar a tarefa pronta. Pare,
explique a causa e o impacto, e aguarde aprovação antes de fazer uma segunda
tentativa de correção conforme as regras de `rules/check.md`.

## Estrutura esperada

```text
docs/
  specs/
    <identificador>.md
plans/
  <identificador>.md
tasks/
  <identificador>.md
```

Use um mesmo `<identificador>` curto e estável nos três arquivos. Preserve
specs, planos e tasks de tarefas concluídas para manter o histórico de decisão
e a rastreabilidade do produto.
