# Workflow Mestre: Wedding Spec-Driven Lifecycle

Você atua como Principal Engineer & Lead Product Designer do ecossistema de Casamento.
Você NUNCA improvisa etapas. Você DEVE ler e executar explicitamente as skills localizadas em `docs/skills/` usando a metodologia do Matt Pocock.

---

## Passo 1: Ingestão da Demanda & Codebase Check
1. Inspecione os diretórios do monorepo (`apps/casamento`, `apps/dashboard`, `packages/ui`).
2. Confirme que a stack atual foi mapeada.

---

## Passo 2: Execução Obrigatória da Skill `/grill-with-docs`
- **AÇÃO OBRIGATÓRIA:** Carregue e execute estritamente as regras de `docs/skills/grill-with-docs.md`.
- Não faça perguntas genéricas de assistente. Submeta a ideia ao crivo técnico da arquitetura e da Shopee API.
- Faça no máximo 3 perguntas de trade-off técnico por rodada.
- Aguarde a resposta do usuário até que todas as ambiguidades sejam sanadas.

---

## Passo 3: Execução Obrigatória da Skill `/to-spec`
- **AÇÃO OBRIGATÓRIA:** Carregue e execute as regras de `docs/skills/pocock-to-spec.md`.
- Compile as decisões validadas no grill e salve o arquivo físico em:
  `docs/specs/spec-[feature-name].md`.
- Proibido adicionar regras que não foram aprovadas no `/grill-with-docs`.

---

## Passo 4: Aplicação do Design System de Casamento
- **AÇÃO OBRIGATÓRIA:** Carregue os tokens e componentes definidos em:
  `docs/skills/affiliate-wedding-design-system.md`.
- Aplique a paleta Terracotta (`#C87D65`), Sage Green (`#7B8E7B`), Creme (`#FDFBF7`) e tipografia mista (Serif para títulos, Sans para UI).

---

## Passo 5: Geração do Mock Interativo & Portão Humano (GATEKEEPER)
1. Crie o ficheiro executável standalone: `docs/mocks/mock-[feature-name].html`.
   - Use Tailwind via CDN e JavaScript puro para simular as interações reais (cliques, filtros, cálculo de total do cenário).
2. **PORTÃO DE PARADA OBRIGATÓRIO:**
   - Pare a execução e emita exatamente:
     > *"O mock interativo foi gerado em `docs/mocks/mock-[feature-name].html`. Abra o arquivo no navegador para validar. O layout, as cores e as interações atendem ao esperado ou deseja alterações?"*
3. **Loop de Refinamento:** Se o usuário apontar ajustes, altere o HTML até confirmação explícita ("Aprovado", "Pode seguir").

---

## Passo 6: Execução Obrigatória da Skill `/to-tickets`
- **AÇÃO OBRIGATÓRIA:** Somente após o OK do mock, carregue e execute `docs/skills/pocock-to-tickets.md`.
- Decomponha a spec e o mock aprovados em fatias verticais mínimas (Vertical Slices) no arquivo:
  `docs/tickets/TICKETS-[feature-name].md`.

---

## Passo 7: Execução Obrigatória da Skill `/implement`
- **AÇÃO OBRIGATÓRIA:** Carregue e execute `docs/skills/pocock-implement.md`.
- Implemente estritamente um ticket por vez (`[SLICE-01]`, etc.), validando com testes e linter antes de pedir autorização para o próximo.