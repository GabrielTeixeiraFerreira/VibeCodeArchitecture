# Template de modelagem para vibecode

Template genérico para instruir outro agente a estruturar projetos em vibecode para qualquer tipo de solução, independentemente do domínio, do público ou da stack tecnológica.

## Objetivo

Este repositório serve como base para que um agente crie a organização correta de um projeto a partir de requisitos, arquitetura, dados, integrações e critérios de entrega. Ele foi pensado para ser aplicável a:

- produtos web ou mobile;
- APIs e serviços backend;
- automações e workflows;
- ferramentas internas, dashboards e sistemas de negócio;
- integrações, plataformas de dados e fluxos de operação;
- projetos com IA, automação ou processamento técnico.

## Filosofia da estrutura

O agente não deve adotar uma estrutura fixa apenas porque ela é comum. Em vez disso, ele deve:

- entender o problema real;
- separar responsabilidades por domínio e camada;
- criar módulos fáceis de evoluir;
- manter documentação viva e alinhada ao produto;
- estabelecer regras claras para validação, revisão e expansão.

## Estrutura sugerida

```text
/
├── src/
│   ├── app/
│   ├── domain/
│   ├── services/
│   ├── infra/
│   └── shared/
├── docs/
│   ├── PRD.md
│   └── adr/
├── rules/
│   ├── spec-flow.md
│   ├── check.md
│   ├── testing.md
│   ├── migration.md
│   ├── handoff.md
│   └── restrictions.md
├── skills/
├── tasks/
├── AGENTS.md
├── README.md
├── LICENSE
├── package.json
├── .gitignore
└── .env.example
```

## Como usar esse template

1. Entenda o problema e o tipo de projeto.
2. Identifique a camada principal: aplicação, backend, serviço, domínio ou infraestrutura.
3. Defina a divisão por responsabilidade em vez de forçar uma estrutura rígida.
4. Gere a estrutura mínima necessária para entregar valor real.
5. Crie a documentação de produto, arquitetura e validação antes de codificar de forma ampla.
6. Mantenha a organização simples, coerente e adaptável.

## Saída esperada do agente

Ao finalizar a modelagem, o agente deve ter criado ou sugerido:

- estrutura de diretórios coerente com o tipo de projeto;
- documentação inicial de requisitos e arquitetura;
- regras de desenvolvimento e validação;
- critérios de progresso e verificação;
- separação clara entre product, business logic, infra e utilitários.

## Regra principal

O objetivo não é um template rígido, e sim uma base inteligente para qualquer tipo de projeto, pronta para ser adaptada por outro agente sem depender de um produto, stack ou contexto específico.
