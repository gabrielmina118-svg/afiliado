# Skill: affiliate-wedding-design-system

## Propósito
Fornecer a fundação visual, design tokens e padrões de componentes para o ecossistema de Casamento (Portal Público "Pegue e Monte DIY" e Dashboard de Operações). Toda proposta visual, mock HTML ou componente React DEVE seguir rigorosamente esta especificação.

---

## 1. Design Tokens (Cores & Semântica)

### Paleta Pública (Inspiração Editorial & Acolhedora)
- **Primary / Ação Principal:**
  - `terracotta-500`: `#C87D65` (CTA principal, botões de compra, links em destaque)
  - `terracotta-600`: `#B56B54` (Hover do CTA, estados ativos)
  - `terracotta-50`: `#FAF3F0` (Superfícies de destaque sutil, tags de categoria)
- **Secondary / Economia & Destaques:**
  - `sage-500`: `#7B8E7B` (Badges de economia, frete grátis, cupons da Shopee)
  - `sage-100`: `#EBF0EB` (Fundo de tags de desconto)
  - `sage-700`: `#4D5E4D` (Texto em tags verdes para contraste acessível)
- **Superfícies & Fundos:**
  - `surface-canvas`: `#FDFBF7` (Fundo global da página pública - Warm Sand / Creme)
  - `surface-card`: `#FFFFFF` (Fundo puro dos cartões e modais)
  - `surface-muted`: `#F5F1EB` (Divisores, caixas de input desativadas)
- **Tipografia & Contraste:**
  - `text-main`: `#2D2A26` (Texto de títulos e corpo principal - alto contraste)
  - `text-muted`: `#7E7871` (Metadados, descrições secundárias, preços riscados)
  - `text-accent`: `#C87D65` (Preços com desconto em destaque)

### Paleta do Dashboard (`apps/dashboard`)
- **Superfícies:** `zinc-50` (`#FAFAFA`) para fundo geral, `white` (`#FFFFFF`) para cartões de métricas.
- **Bordas:** `zinc-200` (`#E4E4E7`).
- **Acentos:** Mesma identidade em `terracotta-500` para manter coerência de marca nos botões de ação e gráficos.

---

## 2. Tipografia

- **Títulos & Hero Headings (Serifa Editorial):**
  - Família: `Playfair Display`, `Cormorant Garamond` ou classe `font-serif`.
  - Uso: Título do cenário (ex: *"Mesa do Bolo Boho Chic Econômica"*), slogans e cabeçalhos de seções de destaque.
  - Peso: `font-semibold` (600) ou `font-bold` (700).
- **Interface, Preços & Dashboard (Sans-Serif Funcional):**
  - Família: `Inter`, `Plus Jakarta Sans` ou classe `font-sans`.
  - Uso: Textos corridos, botões, especificações dos itens da Shopee, tabelas e gráficos.
  - Hierarquia de Preços:
    - Preço Economia Total: `text-2xl font-bold text-terracotta-600`
    - Preço Riscado (Aluguel tradicional): `text-sm line-through text-muted`

---

## 3. Raios de Borda e Sombras

- **Raios de Borda (Border Radius):**
  - Cards de Cenário: `rounded-3xl` (24px) para estética moderna e suave.
  - Cards de Itens de Produto: `rounded-2xl` (16px).
  - Botões de CTA: `rounded-full` (estilo pill) ou `rounded-xl` (12px).
- **Elevações (Shadows):**
  - Padrão Card: `shadow-sm border border-[#EFEAE2]`
  - Hover: `hover:shadow-md hover:-translate-y-0.5 transition-all duration-200`

---

## 4. Padrões de Componentes Core

### A. `ScenarioCard` (Card do Ambiente Completo)
- **Composição:**
  1. Imagem de capa do cenário em proporção 4:3 com bordas arredondadas.
  2. Badge flutuante no topo da imagem: *"Economia Estimada: -68%"*.
  3. Título serifado em 2 linhas max.
  4. Comparativo visual:
     - `Aluguel Tradicional: R$ 1.800,00`
     - `Comprando na Shopee: R$ 380,00`
  5. Contador de itens: *"Contém 9 itens recomendados"*.
  6. CTA: *"Ver Lista e Montar"*.

### B. `ShopeeItemRow` (Linha do Produto Individual no Cenário)
- **Composição:**
  1. Miniatura 1:1 (80x80px no mobile, 96x96px no desktop) com lazy loading e aspect-ratio fixo.
  2. Nome do produto limpo (máximo 2 linhas com `line-clamp-2`).
  3. Preço promocional destacado + badge *"Frete Grátis"* (se houver).
  4. Botão de clique direto: Ícone da sacola + *"Ver na Shopee"*, estilizado em terracotta e com área de toque de no mínimo 44x44px.

### C. `ComparisonBox` (Régua de Economia do Cenário)
- Container com fundo `terracotta-50` ou `sage-50` com borda suave.
- Resumo claro:
  - *"Valor Total do Aluguel: R$ [X]"*
  - *"Custo Total Shopee: R$ [Y]"*
  - **Destaque:** *"Você economiza R$ [X - Y] e os itens ficam com você para revender ou guardar."*

---

## 5. Configuração Base para Tailwind CSS (`tailwind.config.ts`)

```typescript
import type { Config } from "tailwindcss";

const config: Config = {
  theme: {
    extend: {
      colors: {
        terracotta: {
          50: "#FAF3F0",
          500: "#C87D65",
          600: "#B56B54",
        },
        sage: {
          100: "#EBF0EB",
          500: "#7B8E7B",
          700: "#4D5E4D",
        },
        surface: {
          canvas: "#FDFBF7",
          card: "#FFFFFF",
          muted: "#F5F1EB",
        },
        brand: {
          text: "#2D2A26",
          muted: "#7E7871",
        },
      },
      fontFamily: {
        serif: ["var(--font-playfair)", "serif"],
        sans: ["var(--font-inter)", "sans-serif"],
      },
      borderRadius: {
        "3xl": "24px",
      },
    },
  },
};

export default config;