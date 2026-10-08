# Passo 0: Checklist de Insumos & Pré-requisitos (Antes do Código)

Preencha ou valide cada um dos 5 blocos abaixo. Quando todos estiverem respondidos, você terá o insumo exato para disparar a skill `/grill-with-docs` sem interrupções para decidir regras no meio do caminho.

---

## Bloco 1: Credenciais & Infraestrutura Técnica
*O que a IA precisará para montar a conexão e arquitetura sem travar:*

- [ ] **Variáveis da Shopee Affiliate Open API:**
  - `SHOPEE_APP_ID`: (Obtido no painel da Shopee Affiliate Open Platform)
  - `SHOPEE_APP_SECRET`: (Chave secreta para assinatura SHA256)
  - `SHOPEE_GRAPHQL_ENDPOINT`: `https://open-api.affiliate.shopee.com.br/graphql`
- [ ] **Estratégia de Tracking de Sub-IDs:**
  - `sub_id_1`: Nome do canal/app (ex: fixo como `casamento`)
  - `sub_id_2`: Tipo de tela/origem (ex: `cenario-detalhe`, `vitrine-home`, `link-bio`)
  - `sub_id_3`: Slug/ID do cenário específico (ex: `mesa-bolo-boho`)
  - `sub_id_4`: ID do vídeo/short (se o clique veio do YouTube Shorts ou Reels)
- [ ] **Banco de Dados & Storage (se houver):**
  - Supabase / PostgreSQL URL e chaves de acesso (para salvar cenários, métricas de vídeos e produtos).
  - Storage para uploads de capas/vídeos (ex: bucket do Supabase ou Cloudinary).

---

## Bloco 2: Benchmark Visual & Estrutura de Concorrentes
*O que olhar nos outros sites antes de desenhar o visual:*

- [ ] **Referências de Layout para Inspecionar:**
  - **Pinterest:** Olhar a hierarquia de fotos de casamento (iluminação quente, foco no detalhe ou visão ampla da mesa montada).
  - **Mercado Livre / Shopee:** Onde ficam as etiquetas de *"Mais Vendido"*, *"Frete Grátis"* e o destaque de desconto (`% OFF`).
  - **Sites de Pegue e Monte Tradicional:** Como apresentam os kits (foto grande do cenário e lista de itens em tópicos abaixo).
- [ ] **Elementos Visuais Obrigatórios na Tela de Cenário:**
  - Foto principal do cenário pronto (proporção 4:3 ou 16:9 vertical).
  - Caixa de destaque: **"Comparativo de Economia"** (Preço Aluguel Local vs. Comprando na Shopee).
  - Lista dos 8 a 12 produtos necessários com foto, título curto, preço unitário e botão *"Ver na Shopee"*.
  - Botão mestre fixo no rodapé do mobile: *"Comprar todos os itens necessários"*.

---

## Bloco 3: Regras de Negócio dos "Cenários Pegue e Monte"
*As decisões que a IA precisa saber com antecedência:*

- [ ] **Cálculo de Preço e Economia:**
  - O valor de referência de "Aluguel Médio" será cadastrado manualmente por você para cada cenário? (Sim/Não)
  - O valor "Total Shopee" deve ser a soma automática dos preços retornados pela API da Shopee? (Sim/Não)
- [ ] **Tratamento de Indisponibilidade (Edge Cases):**
  - O que fazer se 1 item da lista de 10 estiver sem estoque na Shopee?
    - *Opção A:* Ocultar o cenário inteiro.
    - *Opção B:* Exibir badge *"Item substituto recomendado"* ou riscar apenas aquele item da soma total.
- [ ] **Atualização de Preços da Shopee:**
  - De quanto em quanto tempo os preços devem ser recalculados? (Ex: ISR com cache de 6 a 12 horas para não estourar rate limit da API).

---

## Bloco 4: Estrutura do Dashboard Unificado (`apps/dashboard`)
*O que você quer gerenciar no painel interno:*

- [ ] **Gestão de Cenários:**
  - Tela de cadastro simples: Título do cenário, Foto principal, Valor estimado de aluguel e campo para colar 10 links/IDs de produtos da Shopee.
- [ ] **Gestão do Funil de Vídeos Dark:**
  - Cadastro do vídeo: Título do Short/Reel, Link do vídeo postado, Cenário atrelado a ele.
- [ ] **Métricas Desejadas em Tela:**
  - Views dos vídeos (via YouTube Data API).
  - Cliques gerados daquele vídeo para o site (via Sub-ID).
  - Vendas estimadas / Comissões geradas (via Shopee API).

---

## Bloco 5: Ordem Cronológica de Execução (Roteiro Mental)

Siga rigorosamente esta sequência. Você só passa para o próximo item quando o anterior estiver feito:

1. **Etapa A (Design do Cenário - Público):**
   - Preencher as referências visuais do Bloco 2.
   - Chamar o Claude para fazer a spec visual e o mock interativo em HTML (`docs/mocks/mock-cenario.html`).
   - Validar no navegador do celular se a tela de casamento ficou bonita e clara.

2. **Etapa B (Integração Shopee API):**
   - Inserir as chaves do Bloco 1.
   - Fazer a rota de backend que recebe o ID de 10 produtos e retorna fotos, preços e links com Sub-IDs dinâmicos.

3. **Etapa C (Página de Destino dos Vídeos / Link da Bio):**
   - Criar a rota rápida `/cenarios/[slug]` para onde o link da bio do YouTube Shorts/Instagram vai mandar a noiva.

4. **Etapa D (Dashboard Operacional):**
   - Criar o painel para você cadastrar novos cenários sem precisar mexer em código.
   - Adicionar as telas de métricas e controle de postagens.



   -------------------------------
   Enviar o prompt para o claude

   Claude, antes de iniciar qualquer proposta de arquitetura ou código, execute a rotina abaixo:

1. LEITURA PRÉVIA OBRIGATÓRIA:
   - Leia atentamente o ficheiro \docs\Passo_zero_requisitos.md
   - Inspecione a estrutura atual do monorepo em apps/ e packages/.

2. EXECUÇÃO DA SKILL /grill-with-docs:
   - Carregue e execute estritamente as diretrizes de docs/skills/grill-with-docs.md.
   - Considere todas as respostas e variáveis já preenchidas no Passo 0 como premissas consolidadas (não pergunte o que já está respondido lá).
   - Inicie a sabatina atacando apenas as lacunas não preenchidas, os trade-offs de desempenho (Core Web Vitals), edge cases de estoque da Shopee e a arquitetura das chamadas à API.

Apresente os [DOCS ANALISADOS] e envie até 3 perguntas críticas para fecharmos a Etapa 1 do nicho de Casamento.
```[cite: 1]

---