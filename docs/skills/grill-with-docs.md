# Skill: /grill-with-docs (Matt Pocock Methodology)

## Gatilho de Execução
Comando: `/grill-with-docs` ou invocação direta desta skill.

## Diretiva Primária
Você NÃO é um chatbot fazendo brainstorming informal. Você está executando a skill oficial `/grill-with-docs`.
Sua função é confrontar a ideia do usuário diretamente com:
1. Os arquivos de arquitetura do projeto (`CONTEXT.md`, `AGENTS.md`, `package.json`).
2. A documentação da Shopee Affiliate Open API.
3. As limitações do Next.js / Turborepo e Core Web Vitals.

## Protocolo de Execução Obrigatório

### Fase 1: Análise Silenciosa de Docs
Antes de emitir qualquer resposta, leia os arquivos locais pertinentes e liste no início:
- `[DOCS ANALISADOS]`: Liste os caminhos inspecionados (ex: `apps/casamento/...`, `packages/ui/...`).

### Fase 2: O Grill Socrático (Máximo 3 perguntas cirúrgicas)
Não faça perguntas óbvias ou abertas ("O que você acha?"). Suas perguntas DEVEM apontar um risco ou trade-off real baseado em código/docs:
- **Exemplo de pergunta ruim:** "Como você quer que o card de produto apareça?"
- **Exemplo de pergunta /grill-with-docs:** "No schema da Shopee API, `productOfferV2` não retorna as dimensões da imagem em tempo real. Se renderizarmos a lista de 10 itens do cenário sem placeholders com aspect-ratio fixo, teremos Layout Shift (CLS) crítico no mobile. Como trataremos o fallback de imagem no card antes de chamar a API?"

### Fase 3: Registro de Decisão
Assim que o usuário responder, você sintetiza:
- **Premissas Aceitas**
- **Riscos Mitigados**
- **Decisão Arquitetural Consolidada**