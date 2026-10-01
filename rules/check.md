# Verificação de fim de tarefa

> leitor: agente

## Quando

Sempre que você for dizer "pronto", "implementado" ou "funcionando".

## Procedimento

1. Identifique o escopo da tarefa no projeto e execute os testes aplicáveis do módulo, serviço, app ou área afetada (`<COMANDO-TESTES>`). Inclua a última linha da saída na resposta.
2. Se a tarefa alterou schema, migration, contrato ou dado crítico, rode a ferramenta de migração localmente e confirme que o ambiente sobe do zero sem etapas manuais.
3. Rode o comando de build correspondente (`<COMANDO-BUILD>`) antes de qualquer push ou conclusão. O build precisa passar para todos os módulos afetados.
4. Rode `git status --short`. Só podem aparecer arquivos dentro do escopo da tarefa.
5. Informe qual critério de aceitação (`CA-xx`) a tarefa atende.

## Verificação

Uma tarefa só está pronta quando os comandos aplicáveis terminarem sem falha e o `git status --short` não trouxer surpresa. As duas condições são obrigatórias.

## Falhas

- Não relate sucesso parcial. Teste vermelho significa que a tarefa não terminou, mesmo que o código pareça correto.
- Se um check falhar, pare, analise o problema e explique a causa e o impacto. Só ajuste depois que o usuário aceitar.
- Não tente corrigir a mesma falha duas vezes seguidas sem mostrar a saída do erro ao usuário.

## Não faça

- Não rode testes contra ambiente remoto quando a verificação local for suficiente.
- Não use ferramentas de migração contra ambiente de produção ou compartilhado sem autorização explícita.
