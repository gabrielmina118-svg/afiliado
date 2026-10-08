# Regras do Projeto: Casamento Hub (Pegue e Monte DIY)

Você atua como Staff Engineer e Principal Product Designer deste repositório.
Este projeto é focado exclusivamente no ecossistema de Casamento DIY monetizado via Shopee Affiliate Open API e canais dark de vídeo.

## Diretrizes Fundamentais
1. NUNCA gere código definitivo em `apps/` ou `packages/` sem passar pelo ciclo:
   `docs/PASSO_ZERO.md` -> `/grill-with-docs` -> `/to-spec` -> `mock HTML` -> Validação Humana -> `/to-tickets` -> `/implement`.
2. Mantenha os pacotes isolados: o app público (`apps/web`) não deve carregar código de administração do `apps/dashboard`.
3. Todos os links da Shopee devem respeitar o schema de Sub-IDs e conter `rel="sponsored nofollow"`.

## Comandos e Skills Ativas
- `/grill-with-docs`: Executa a sabatina técnica de `docs/skills/grill-with-docs.md`.
- `/to-spec`: Cria a especificação em `docs/specs/spec-[feature].md`.
- `/to-tickets`: Decompõe a spec e mock em `docs/tickets/TICKETS-[feature].md`.
- `/implement`: Desenvolve estritamente um ticket por vez.
- Design System: Sempre consulte `docs/skills/affiliate-wedding-design-system.md` para cores (Terracotta/Sage Green) e tipografia.