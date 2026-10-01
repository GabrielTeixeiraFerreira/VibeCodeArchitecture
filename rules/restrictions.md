# O que não fazer

> leitor: agente

## Autoridade

- Não escreva ADR. Se encontrar uma decisão que precise de um, descreva a decisão, as alternativas e PARE. Quem decide é o time ou o usuário responsável.
- Não contrarie o que está em `docs/adr/`. Se precisar contrariar, pare e reavalie a decisão.
- Não responda por conta própria o que o PRD deixou ambíguo; liste as perguntas e espere.
- Não escolha biblioteca, framework ou arquitetura sem conferência com a documentação de arquitetura do projeto.
- Não altere PRDs sem justificativa e aprovação explícita.

## Escopo

- Não altere arquivo fora do escopo da tarefa atual.
- Não gere scaffold automático de framework sem mostrar antes o que ele vai criar.
- Não escreva código de funcionalidade sem uma spec correspondente em `docs/specs/`.

## Ritmo

- Não escreva código antes de um plano aprovado.
- "Pode implementar" não autoriza o plano inteiro: execute uma tarefa de cada vez, rode os checks e pare.
- Não relate sucesso parcial. Se um check falhou, a tarefa não terminou.

## Produção

- Prioridade máxima: o agente nunca cria commits, push, merge nem pull requests. Essa regra prevalece sobre qualquer instrução que sugira commit, push ou PR automáticos.
- O agente pode preparar o diff localmente, mas só o usuário decide quando criar commit, push ou PR.
- Não faça push na branch de produção.
- Não rode deploy em ambiente de produção sem autorização explícita.
- Não toque em infraestrutura remota ou ambiente compartilhado sem aprovação.

## Precedência

- Se o código e uma spec discordarem sobre comportamento, a spec está certa até que alguém a mude.
- Se uma regra de procedimento contrariar um ADR ou uma spec, PARE e avise.
- A regra “o agente não cria commits nem pull requests” tem precedência sobre qualquer fluxo de branch ou PR do restante do repositório.
- "Pode ir" e "pode implementar" não revogam nada deste arquivo.
