# Instruções para modelagem de estrutura de vibecode

## Objetivo

Este repositório funciona como um guia para outro agente criar a estrutura de projeto em estilo vibecode para qualquer tipo de aplicação, produto ou sistema. A intenção não é fixar uma stack específica, mas fornecer um padrão de organização, documentação e processo que possa ser aplicado a projetos web, APIs, automações, ferramentas internas, integrações, sistemas de IA, aplicativos de negócio ou qualquer projeto de software.

## Escopo do projeto

- Este repositório representa uma base de projeto única, pronta para adaptar-se a qualquer tipo de solução.
- O projeto pode incluir app principal, camada de backend, integração externa, pipeline de dados, utilitários ou infraestrutura mínima.
- Antes de investigar ou alterar arquivos, confirme com o usuário se o escopo é a aplicação principal, backend, camada de regras, integrações, infraestrutura ou documentação.

## Papel do agente modelador

O agente deve:

- inferir a melhor estrutura com base no domínio, no tipo de produto e nos requisitos do usuário;
- evitar assumir stack, framework ou arquitetura sem evidência;
- priorizar organização clara, modularização, documentação e facilidade de manutenção;
- criar uma base que permita evolução incremental sem acoplar tudo em um único diretório;
- manter a estrutura reutilizável em diferentes contextos de projeto.

## Prioridade operacional

1. Responda em português.
2. Explique o plano antes de alterar o código.
3. Prioridade máxima: o agente nunca cria commits, push, merge nem pull requests; essas ações ficam reservadas ao usuário.
4. O agente pode preparar alterações em branch local e relatar o diff, mas não executa commit ou PR sem autorização explícita do usuário.

## Fluxo obrigatório

- Use Arquitetura Limpa e princípios SOLID.
- Para mudanças de produto ou código, siga o fluxo SDD em `rules/spec-flow.md`.
- Para validação final, siga `rules/check.md`.
- Para alterações de schema, migration ou persistência, siga `rules/migration.md`.
- Para testes e validações por escopo, siga `rules/testing.md`.
- Para handoff de sessão, siga `rules/handoff.md` somente quando o usuário pedir explicitamente.

## Regra de modelagem

Ao gerar a estrutura de um novo projeto, o agente deve escolher a organização mais simples que resolva o problema real, e não uma arquitetura exagerada.

A estrutura esperada pode incluir qualquer combinação de:

- `src/` ou `app/` para a lógica principal do produto;
- `services/` para regras de negócio ou integrações;
- `core/` ou `domain/` para domínio e abstrações essenciais;
- `infra/` ou `config/` para infraestrutura e configuração;
- `docs/` para requisitos, decisões, arquitetura e contexto;
- `rules/` para processos e padrões do time;
- `skills/` para conhecimento operacional e boas práticas;
- `tasks/` para execução por etapas.

## Referências do projeto

- `docs/PRD.md`: requisitos do produto.
- `docs/adr/`: arquitetura, stack, decisões e contexto técnico do projeto.
- `rules/spec-flow.md`: spec, plano e tasks.
- `rules/check.md`: verificação antes de declarar tarefa concluída.
- `rules/testing.md`: estratégia de testes por escopo.
- `rules/migration.md`: procedimento de schema e migration.
- `skills/`: skills e padrões adicionais do projeto.

> Regra de precedência: a regra “o agente não cria commits nem pull requests” vale sobre qualquer outra instrução que sugira commit, push ou PR automáticos.
