# Regra de testes

> leitor: agente

## Fonte da regra

Esta regra segue as decisões de testes registradas na ADR do projeto e nos scripts do repositório afetado. A documentação de arquitetura é a fonte da escolha das ferramentas e o tooling do projeto é a fonte dos comandos executáveis.

## Matriz obrigatória

### Aplicações e serviços

- use o framework de testes adotado pelo projeto para a app ou serviço que está sendo alterado;
- teste serviços, regras de negócio e fluxos principais sem subir a aplicação inteira quando isso não for necessário;
- teste persistência, integrações e comportamento de dados em ambiente local e realista;
- valide entrada, autenticação, autorização e serialização de erros nos módulos que expõem interfaces ou APIs;
- cubra isolamento de dados, permissões e regras de concorrência quando aplicáveis.

### Frontend e interfaces

- use o framework de testes do frontend adotado no projeto;
- teste componentes, validações e lógica de estado sem depender do navegador quando o comportamento não exigir integração visual;
- use testes E2E para fluxos críticos que dependam do comportamento real do usuário ou do sistema;
- mantenha os testes compatíveis com o stack do projeto e com suas regras de tipagem e build.

### Contrato entre módulos, apps ou pacotes

- publique e valide o contrato do sistema quando houver API, schema, payload ou biblioteca compartilhada;
- gere e confirme artefatos derivados do contrato antes de concluir a tarefa;
- uma alteração de contrato deve incluir verificação e atualização do consumo afetado.

## Caminhos críticos

Não existe meta percentual de cobertura obrigatória. A aprovação depende de testar os caminhos críticos do comportamento alterado, incluindo, quando aplicável:

- autenticação, autorização e proteção de rotas;
- criação, atualização e leitura dos recursos alterados;
- validação de entrada e tratamento de erros;
- integrações, transações e regras de persistência relevantes;
- isolamento de dados e escalabilidade de acesso;
- estados de carregamento, sucesso e erro em interfaces;
- fluxos operacionais cobertos por E2E.

## Execução por escopo

Antes de testar:

1. identifique se a mudança afeta uma parte do projeto, um módulo, um serviço, uma API ou mais de uma área do sistema;
2. leia os scripts do ambiente ou repositório afetado;
3. execute o teste mais estreito que cubra a mudança;
4. execute a suíte relevante quando a alteração cruzar módulos, regras ou contratos;
5. execute o build correspondente conforme `rules/check.md`.

Para mudanças que afetam múltiplos módulos, valide cada lado afetado. Para mudanças de banco ou schema, use também `rules/migration.md`; os testes de integração devem usar ambiente local e não ambiente remoto ou compartilhado.

## Critérios de conclusão

Uma tarefa de código só pode ser considerada validada quando:

- os testes aplicáveis terminarem sem falha;
- novos caminhos críticos tiverem testes ou uma justificativa explícita de por que não são testáveis nesta etapa;
- os testes de isolamento, autorização ou contratos forem preservados para os módulos afetados;
- a verificação de contrato tiver passado quando houver alteração de interface ou forma de dados;
- o build correspondente tiver passado;
- os resultados e a última linha de cada comando relevante forem registrados conforme `rules/check.md`.

Se um teste falhar, pare, explique a causa e o impacto e aguarde aprovação antes de alterar o código. Não masque falhas removendo assertions, reduzindo o escopo do teste ou substituindo uma dependência real por mock sem justificar a mudança.
