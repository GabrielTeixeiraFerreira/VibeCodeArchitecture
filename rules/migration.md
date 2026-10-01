# Mudança de schema

> leitor: agente

## Quando

Qualquer tarefa que precise criar, alterar ou remover tabela, coluna, índice, constraint, política de acesso ou seed que afete o contrato do banco ou do armazenamento persistente — inclusive quando a mudança parecer trivial.

## Procedimento

1. Antes de gerar qualquer coisa: escreva a alteração pretendida na resposta e PARE. O usuário aprova ou corrige a proposta antes da execução.
2. Gere a migration pela CLI ou ferramenta oficial do projeto. Uma migration por tarefa. Se a mudança exigir SQL bruto para regras de acesso, políticas, triggers ou ajustes de dados, mantenha esse SQL dentro da mesma migration.
3. Toda tabela nova deve seguir as convenções de segurança e governança do projeto, incluindo regras explícitas de acesso ou proteção quando aplicável. Estrutura sem regra clara não entra no repositório.
4. Se a tabela ou entidade já tem dado, explique o que acontece com as linhas existentes. Coluna obrigatória nova precisa de default ou de uma etapa de preenchimento.
5. Aplique a migração localmente e rode os testes ou validações relevantes do sistema afetado.

## Verificação

A migração deve ser aplicada em ambiente local de forma limpa e reprodutível, sem erro e sem passos manuais adicionais.

## Não faça

- Não altere schema por ferramenta visual, SQL avulso ou edição manual fora do fluxo de migration.
- Não edite migration que já foi aplicada ou compartilhada no repositório principal. Escreva a próxima versão.
- Não toque em ambiente remoto ou compartilhado sem autorização explícita.
- Não substitua a migration por alterações aplicadas apenas em ambiente local sem registro no repositório.
