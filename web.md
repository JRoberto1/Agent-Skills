# skill: web — v3
# Quando usar: qualquer site, portal, landing page, blog, sistema web
# Gatilho: "criar site", "landing page", "portal", "blog", "sistema web"

---

## FASE 1 — BRIEFING

### Escolha o modo:
**[RÁPIDO]** → 1 pergunta máxima. Assume com criatividade e declara as suposições.
**[PADRÃO]** → 5 perguntas essenciais. Para a maioria dos projetos.
**[COMPLETO]** → Todos os blocos. Para projetos críticos.

Se Roberto não escolher, use **PADRÃO**.
**Regra de ouro:** Faça no máximo 1 pergunta se algo crítico faltar. Para o resto, assuma e declare.

---

### Perguntas SEMPRE obrigatórias

1. **Objetivo:** Qual o tipo e objetivo do site? (vendas, institucional, portfólio, blog, sistema)
2. **Público:** Quem vai usar? (perfil, faixa etária, país)
3. **Identidade visual:** Tem logo e cores? Se sim, em qual formato?
4. **Referências:** Tem sites que admira? (links ou screenshots — isso muda tudo no visual)
5. **Hospedagem:** Onde vai hospedar? (Vercel, Hostgator, outro)

---

### Padrões inteligentes (assume sem perguntar, informa ao usuário)

| Decisão | Padrão |
|---------|--------|
| Mobile-first | Sempre SIM |
| SEO | Sempre máxima performance no Google |
| Acessibilidade | WCAG 2.2 AA |
| Ícones | Lucide React ou SVG inline — nunca emojis |
| Imagens | Catálogo verificado — nunca API em tempo real para listagens |
| Performance | Score mínimo 90 no PageSpeed |
| Fonte Inter genérica | NUNCA — escolha fonte com intenção |
| Gradiente roxo/azul | NUNCA — é marca registrada de AI slop |

---

## FASE 2 — DEFINIÇÃO (Declara antes de codar)

Após briefing, apresenta e justifica:

```
"Com base no que você me disse:
- Direção de design: [nome] — [motivo]
- Stack: [escolha] — [motivo]
- Fontes: [display] + [corpo]
- Paleta: [cores com hex]
- Imagens: [estratégia]
- Seções: [lista]

Confirma para começar?"
```

---

## DIREÇÕES DE DESIGN — Escolha Uma, Execute com Convicção

### Mapa por Contexto

| Contexto | Direção |
|----------|---------|
| SaaS, tech, startup B2B | `editorial-minimal` ou `dark-tech` |
| Agência criativa, portfólio | `brutalist-modern` |
| Moda, joalheria, hotel, luxo | `luxury-refined` |
| Música, entretenimento, gaming | `retro-futuristic` |
| Saúde, wellness, alimentação | `organic-natural` |
| App B2C, edtech, produto jovem | `playful-bold` |
| Portal de conteúdo, mensagens | `editorial-minimal` ou `organic-natural` |

---

### DNA de Cada Direção

**`editorial-minimal`** — Stripe, Linear, Vercel
- Paleta: branco + preto + 1 accent frio
- Fontes: `Syne` ou `Cabinet Grotesk` 700–900, `letter-spacing: -0.03em`
- Sombras máximas: `0 1px 3px rgba(0,0,0,0.08)`
- Grid assimétrico no hero (60/40)
- Espaçamento: `padding: clamp(6rem, 12vw, 10rem) 0`

**`brutalist-modern`** — agências criativas, portfólios ousados
- Paleta: fundo creme/off-white + preto + 1–2 cores vibrantes em bloco
- Fontes: `Space Grotesk` 900, headlines que sangram fora do container
- Bordas: `3px solid #0A0A0A` + sombra offset: `4px 4px 0 #0A0A0A`
- Hover: `translate(-2px, -2px)` com sombra crescendo
- Botões: `text-transform: uppercase; letter-spacing: 0.1em`

**`luxury-refined`** — moda, joalheria, hotelaria premium
- Paleta: off-white quente + preto suave + dourado queimado `#92784D`
- Fontes: `Cormorant Garamond` 300 (nunca bold no display!) + `Jost` no corpo
- Espaçamento extravagante: `padding: clamp(8rem, 16vw, 14rem) 0`
- Decoração: `border-top: 1px solid rgba(0,0,0,0.1)`
- Proibido: mais de 3 cores, elementos piscando, ícones genéricos

**`retro-futuristic`** — entretenimento, música, gaming
- Paleta: fundo escuro `#0D0D1A` + neon pink + cyan + dourado
- Fontes: `Orbitron` display + `Share Tech Mono` corpo
- Glow: `text-shadow: 0 0 20px rgba(255,45,120,0.6)`
- Grain texture em pseudo-element sobre toda a página

**`organic-natural`** — wellness, food, sustentabilidade, mensagens
- Paleta: creme `#F5F0E4` + marrom escuro + laranja terra `#C4561A`
- Fontes: `Playfair Display` display + `Lora` corpo (serif em ambos)
- Formas blob: `border-radius: 60% 40% 30% 70% / 60% 30% 70% 40%`
- Animação respirando: `animation: breathe 4s ease-in-out infinite`

**`dark-tech`** — ferramentas técnicas, SaaS dark, developer tools
- Paleta: `#0A0A0A` fundo + surfaces `#111` e `#1A1A` + accent esmeralda ou âmbar
- Fontes: `DM Sans` ou `IBM Plex Sans` + `JetBrains Mono` decorativo
- Cards: `border: 1px solid rgba(255,255,255,0.08)`
- Glassmorphism só em nav/modais: `backdrop-filter: blur(12px)`

**`playful-bold`** — apps B2C, edtech, produtos jovens
- Paleta: fundo quente claro + 3–4 accent colors
- Fontes: `Nunito` 900 ou `Righteous`
- Border-radius: `20px` cards, `9999px` botões
- Sombras coloridas: `box-shadow: 0 8px 24px rgba(255,75,110,0.3)`

---

### Regras Universais de Design

❌ **NUNCA:**
- Fonte Inter como padrão sem intenção
- Gradiente roxo/azul em fundo branco (AI slop)
- `transition: all` — liste propriedades explicitamente
- `outline: none` sem substituto de foco visível
- Lorem Ipsum — conteúdo deve ser realista e contextualizado
- Emojis como ícones

✅ **SEMPRE:**
- `clamp()` para tipografia fluida — nunca `px` fixo em fontes
- `prefers-reduced-motion` em toda animação
- Conteúdo de placeholder realista e contextualizado

---

## FASE 3 — EXECUÇÃO

### Escolha de Stack

| Situação | Stack |
|----------|-------|
| Site simples, hospedagem básica | HTML + Tailwind CSS |
| Site com conteúdo gerenciável | Next.js 15 + Sanity + Vercel |
| E-commerce | Next.js + Stripe |
| Sistema com usuários | Next.js + Supabase |
| Blog/portal de conteúdo | Next.js + Sanity + Vercel |

**Regra:** use a stack mais simples que resolve. Não use Next.js se HTML resolve.

---

### CSS Base (copie e adapte)

```css
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

:root {
  --color-bg:      #FAFAF8;
  --color-text:    #1A1A1A;
  --color-muted:   #6B6B6B;
  --color-accent:  #E8522A;
  --color-surface: #F0EDE8;
  --color-border:  rgba(0,0,0,0.08);
  --font-display:  'Playfair Display', serif;
  --font-body:     'Plus Jakarta Sans', sans-serif;
  --radius:        12px;
  --transition:    220ms cubic-bezier(0.4, 0, 0.2, 1);
  --max-w:         1200px;
}

body {
  font-family: var(--font-body);
  background: var(--color-bg);
  color: var(--color-text);
  line-height: 1.6;
  -webkit-font-smoothing: antialiased;
}

h1 { font-size: clamp(2.5rem, 6vw, 5rem);  font-family: var(--font-display); line-height: 1.1; }
h2 { font-size: clamp(1.75rem, 4vw, 3rem); font-family: var(--font-display); line-height: 1.2; }
h3 { font-size: clamp(1.125rem, 2vw, 1.5rem); }

.container { width: 100%; max-width: var(--max-w); margin: 0 auto; padding: 0 clamp(1rem, 5vw, 2rem); }
section    { padding: clamp(4rem, 10vw, 8rem) 0; }
.grid-auto { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 1.5rem; }

/* Scroll reveal */
.reveal { opacity: 0; transform: translateY(20px); }
@media (prefers-reduced-motion: no-preference) {
  .reveal.is-visible { animation: fadeUp 0.6s ease forwards; }
  @keyframes fadeUp   { to { opacity: 1; transform: translateY(0); } }
}
@media (prefers-reduced-motion: reduce) {
  .reveal { opacity: 1; transform: none; }
}
```

```javascript
// Scroll animations — nunca scroll events
const io = new IntersectionObserver(
  entries => entries.forEach(e => e.isIntersecting && e.target.classList.add('is-visible')),
  { threshold: 0.1 }
);
document.querySelectorAll('.reveal').forEach(el => io.observe(el));
```

---

### Imagens — Hierarquia de Decisão

**1. Roberto tem imagens próprias?** → usa elas

**2. Não tem → usa estas fontes verificadas (sem API):**

```html
<!-- Fotos de lugares/produtos (seeds consistentes) -->
<img src="https://picsum.photos/seed/hero/800/600" alt="..." width="800" height="600">
<!-- Seeds: hero, team1, team2, office, product, about, banner -->

<!-- Avatares de depoimentos -->
<img src="https://i.pravatar.cc/64?img=23" alt="Foto de Ana Costa" width="64" height="64" loading="lazy">
<!-- img=1 até img=70 para variedade -->

<!-- Logos placeholder de clientes -->
<div class="logo-placeholder" style="width:110px;height:30px;background:currentColor;opacity:0.15;border-radius:4px;"></div>
```

**3. Hero sem foto — fundo rico em CSS puro:**
```css
background:
  radial-gradient(at 20% 50%, hsl(28,100%,74%) 0px, transparent 55%),
  radial-gradient(at 80% 10%, hsl(189,100%,65%) 0px, transparent 55%),
  radial-gradient(at 50% 90%, hsl(340,80%,75%)  0px, transparent 55%);
```

**NUNCA:** `[IMAGEM AQUI]`, `background: #ccc`, `src=""` ou cards sem imagem/fallback

**Para listagens com API (Pexels):**
- Processa em lotes de 2 com delay de 600ms
- Cache ISR 24h (revalidate: 86400)
- Fallback de gradiente sempre implementado

---

### Seções — Use Só o Que Faz Sentido

```
Nav          → Sticky. Logo + links + CTA. Transparente → opaco no scroll.
Hero         → Proposta de valor em 1 frase + CTA. Seção mais importante.
Social Proof → Logos, números, depoimento. Logo após o hero.
Features     → Benefícios (nunca funcionalidades).
How It Works → Máximo 4 passos com verbos de ação.
Pricing      → Plano destacado com badge "Mais Popular".
FAQ          → Objeções reais, respostas diretas e curtas.
CTA Final    → Reforço + eliminador de risco ("sem cartão", "cancele quando quiser").
Footer       → Links agrupados, contato, copyright.
```

---

### Copywriting — Benefícios, Nunca Funcionalidades

| Funcionalidade ❌ | Benefício ✅ |
|---|---|
| "Dashboard em tempo real" | "Veja exatamente onde está seu dinheiro agora" |
| "Relatórios automáticos" | "Pare de montar planilhas toda segunda-feira" |
| "Integração com CRM" | "Seus dados de vendas sempre atualizados" |

**Regras universais:**
- Voz ativa: "Instale em 2 minutos" não "A instalação pode ser feita em 2 minutos"
- CTAs específicos: "Começar Gratuitamente" não "Continuar" ou "Avançar"
- Eliminador de risco: "Sem cartão de crédito · Cancele quando quiser"
- Nunca Lorem Ipsum — invente conteúdo realista e contextualizado

**Tom por segmento:**

| Segmento | Tom | Evite |
|---|---|---|
| B2B Enterprise | Formal, confiável, ROI | Gírias |
| B2B SMB | Direto, prático | Jargão corporativo |
| B2C Lifestyle | Aspiracional, empático | Termos técnicos |
| Saúde/Finanças | Cuidadoso, claro | Promessas exageradas |

---

### SEO — Sempre Máxima Performance no Google

```typescript
// Next.js — app/layout.tsx
export const metadata = {
  title: { default: 'Nome do Site', template: '%s | Nome do Site' },
  description: 'Descrição principal (máx 160 caracteres)',
  openGraph: {
    title: 'Nome do Site',
    description: 'Descrição para redes sociais',
    url: 'https://seusite.com.br',
    siteName: 'Nome do Site',
    images: [{ url: '/og-image.png', width: 1200, height: 630 }],
    locale: 'pt_BR',
    type: 'website',
  },
  alternates: { canonical: 'https://seusite.com.br' },
  robots: { index: true, follow: true },
}
```

Obrigatório em todo projeto:
- sitemap.xml dinâmico
- robots.txt configurado
- Core Web Vitals: LCP ≤2.5s, INP ≤200ms, CLS ≤0.1
- Google Search Console verificado e sitemap submetido

---

### Acessibilidade — Checklist

- [ ] `<button>` para ações, `<a>` para navegação — nunca `<div onClick>`
- [ ] Todo `<img>` tem `alt` descritivo (ou `alt=""` se decorativo)
- [ ] Ícones decorativos: `aria-hidden="true"`
- [ ] Botão com só ícone tem `aria-label`
- [ ] Menu mobile com `aria-expanded` e `aria-controls`
- [ ] Foco visível: `:focus-visible` — nunca só `outline:none`
- [ ] Skip link como primeiro elemento: `<a href="#main" class="skip-link">Ir ao conteúdo</a>`
- [ ] Contraste ≥ 4.5:1 texto normal, ≥ 3:1 texto grande
- [ ] Touch targets ≥ 44×44px

---

### Mobile — Navegação (Componente Padrão)

```html
<header class="site-header" id="site-header">
  <nav class="nav container">
    <a href="/" class="nav-logo">Logo</a>
    <ul class="nav-links" role="list">
      <li><a href="#features">Recursos</a></li>
    </ul>
    <button class="nav-hamburger" aria-label="Abrir menu" aria-expanded="false" aria-controls="mobile-nav">
      <span></span><span></span><span></span>
    </button>
  </nav>
  <div id="mobile-nav" class="mobile-nav" hidden>...</div>
</header>
```

```css
.site-header { position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  transition: background var(--transition), box-shadow var(--transition); }
.site-header.scrolled { background: rgba(255,255,255,0.92);
  backdrop-filter: blur(12px); box-shadow: 0 1px 0 rgba(0,0,0,0.08); }
@media (max-width: 768px) {
  .nav-links { display: none; }
  .nav-hamburger { display: flex; }
}
```

```javascript
// Scroll + menu mobile
const header = document.getElementById('site-header');
window.addEventListener('scroll', () =>
  header.classList.toggle('scrolled', window.scrollY > 20), { passive: true });

const hamburger = document.querySelector('.nav-hamburger');
const mobileNav = document.getElementById('mobile-nav');
hamburger.addEventListener('click', () => {
  const isOpen = !mobileNav.hidden;
  mobileNav.hidden = isOpen;
  hamburger.setAttribute('aria-expanded', String(!isOpen));
});
document.addEventListener('keydown', e => {
  if (e.key === 'Escape' && !mobileNav.hidden) {
    mobileNav.hidden = true;
    hamburger.setAttribute('aria-expanded', 'false');
    hamburger.focus();
  }
});
```

---

### Sanity CMS — Setup (quando necessário)

```bash
# Na pasta do projeto
npx sanity@latest init --env .env.local
# Select project → seu projeto | dataset → production
# Editor MCP → Claude Code | Studio path → /studio
```

**Importação em lote:**
- Script `scripts/import-content.ts` com token Editor
- Lotes de 10, delay 200ms
- Publicar após importar (chegam como draft)

---

## FASE 4 — CHECKLIST TÉCNICO

### Visual e Design
- [ ] Direção de design aplicada consistentemente
- [ ] Nenhum emoji como ícone
- [ ] Nenhum gradiente roxo/azul genérico
- [ ] Conteúdo realista (sem Lorem Ipsum)
- [ ] Fontes carregando do Google Fonts

### Performance
- [ ] Build sem erros (`npm run build`)
- [ ] Imagens todas com alt text e sem quebra
- [ ] Score PageSpeed ≥ 90 mobile e desktop
- [ ] Nenhum `transition: all`

### SEO
- [ ] Meta title único por página
- [ ] Meta description única por página
- [ ] Open Graph configurado
- [ ] sitemap.xml acessível
- [ ] robots.txt configurado

### Responsividade
- [ ] Funciona em 320px (mobile pequeno)
- [ ] Funciona em 768px (tablet)
- [ ] Funciona em 1280px (desktop)
- [ ] Touch targets ≥ 44×44px
- [ ] Menu mobile funcional

### Acessibilidade
- [ ] Foco visível em todos os elementos interativos
- [ ] Skip link presente
- [ ] Contraste adequado
- [ ] Ícones com aria-label

### Deploy
- [ ] Variáveis de ambiente na plataforma
- [ ] .env.example criado
- [ ] README atualizado
- [ ] Domínio apontando corretamente

---

## FASE 5 — APROVAÇÃO DO ROBERTO

```
"✅ Checklist técnico concluído.

Direção aplicada: [nome da direção]
Acesse [URL] e avalie:

1. O visual está com a identidade que você esperava?
2. O conteúdo faz sentido para o seu público?
3. Funciona bem no celular?
4. Tem algo para ajustar?

Responda APROVADO ou AJUSTES: [o que mudar]"
```

**Se AJUSTES:** executa, refaz checklist, volta para aprovação.
**Se APROVADO:** commit final + atualiza LEARNINGS.md + encerra.

---

## Problemas Comuns e Soluções

| Problema | Causa | Solução |
|----------|-------|---------|
| Visual genérico "AI slop" | Sem direção de design definida | Escolher direção antes de codar |
| Imagens repetindo | Rate limit ou fallback igual | Catálogo picsum com seeds únicos |
| Imagens quebrando na listagem | API em tempo real | Catálogo verificado + fallback gradiente |
| Build falha na Vercel | ESLint ou TypeScript | Rode build local antes do push |
| Deploy não atualiza | Cache ISR | Redeploy sem cache |
| Site não aparece no Google | Não indexado | Submeta sitemap no Search Console |
| Fonte não carrega | Import incorreto | Google Fonts no layout com display=swap |
| Menu mobile não funciona | aria-expanded não atualizado | Use o componente padrão desta skill |
