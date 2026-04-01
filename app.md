# skill: app — v3
# Quando usar: app mobile, PWA, aplicativo desktop
# Gatilho: "criar app", "aplicativo", "PWA", "mobile", "Android", "iOS"

---

## FASE 1 — BRIEFING

**Regra:** Máximo 1 pergunta se algo crítico faltar. Para o resto, assuma e declare.

### Perguntas SEMPRE obrigatórias

1. **Plataforma:** Android, iOS ou ambos?
2. **Objetivo:** O que o app faz? Qual problema resolve?
3. **Distribuição:** Loja (Play Store/App Store) ou uso interno/web?
4. **Offline:** Precisa funcionar sem internet?
5. **Identidade visual:** Tem logo e cores? Referências visuais?

### Modo PADRÃO (além das obrigatórias)
6. **Login:** Precisa de autenticação?
7. **Dados:** Onde ficam os dados? (local, nuvem, API)
8. **Funcionalidades:** Liste as 3 principais ações do usuário
9. **APIs externas:** Integra com algum serviço?
10. **Manutenção:** Quem vai atualizar? Com que frequência?

### Padrões inteligentes

| Decisão | Padrão |
|---------|--------|
| PWA antes de nativo | Sempre — só vai nativo se necessário |
| Mobile-first | Sempre SIM |
| SEO (PWA) | Máxima performance no Google |
| Ícones | Lucide React — nunca emojis |
| Touch targets | Mínimo 44×44px — obrigatório |
| Acessibilidade | WCAG 2.2 AA |
| Erro ao usuário | Sempre mensagem amigável — nunca erro técnico |

---

## FASE 2 — DEFINIÇÃO

```
"Com base no que você me disse:
- Tipo: [PWA / React Native + motivo]
- Stack: [escolha + motivo]
- Identidade: [direção visual escolhida]
- Autenticação: [escolha + motivo]

Confirma para começar?"
```

### Escolha da Stack

| Situação | Stack |
|----------|-------|
| App simples, sem loja | PWA (Next.js ou Vite) |
| Android + iOS | React Native + Expo |
| Dados offline pesados | React Native + SQLite |
| App corporativo | React Native + Supabase |
| Protótipo rápido | PWA com HTML/JS |

---

## FASE 3 — EXECUÇÃO

### Imagens no App — Hierarquia

1. Roberto tem imagens próprias → usa elas
2. Fotos de contexto → `https://picsum.photos/seed/[nome]/400/300`
3. Avatares → `https://i.pravatar.cc/64?img=[1-70]`
4. Ícones → sempre SVG via Lucide React
5. **Nunca:** placeholder `#ccc`, imagem quebrada, emoji como ícone

### Acessibilidade Mobile — Obrigatório

```jsx
// Botão acessível
<button
  aria-label="Adicionar item ao favoritos"
  onClick={handleFavorite}
  style={{ minWidth: 44, minHeight: 44 }} // touch target
>
  <Heart aria-hidden="true" />
</button>

// Imagem acessível
<img src={url} alt="Descrição real da imagem" width={400} height={300} />

// Ícone decorativo
<Star aria-hidden="true" />
```

### PWA — Checklist de Implementação

- [ ] `manifest.json` completo (nome, ícones 192×192 e 512×512, cores, start_url)
- [ ] Service Worker registrado
- [ ] Funciona offline (pelo menos tela de fallback)
- [ ] HTTPS obrigatório
- [ ] Meta viewport configurado
- [ ] Touch targets ≥ 44×44px em todos os botões

### APIs Externas

- Todas as chaves em `.env`
- Retry com delay exponencial
- Tratamento de erro com mensagem amigável ao usuário
- Rate limit respeitado com delay entre requests

### Foco Visível — Mobile

```css
/* Obrigatório em todos os elementos interativos */
button:focus-visible,
a:focus-visible,
input:focus-visible {
  outline: 2px solid var(--color-accent);
  outline-offset: 2px;
}
/* Nunca: outline: none; sem substituto */
```

---

## FASE 4 — CHECKLIST TÉCNICO

### Funcionalidade
- [ ] Funciona em celular real (não só simulador)
- [ ] Funciona offline (se aplicável)
- [ ] Login funcionando (se aplicável)
- [ ] Erros com mensagem amigável ao usuário

### Visual
- [ ] Funciona em 320px mínimo
- [ ] Ícones SVG (nenhum emoji)
- [ ] Touch targets ≥ 44×44px
- [ ] Contraste de cores adequado

### SEO (PWA)
- [ ] Meta tags configuradas
- [ ] sitemap.xml gerado
- [ ] robots.txt configurado
- [ ] Score PageSpeed ≥ 90

### Entrega
- [ ] .env.example criado
- [ ] README com instruções de instalação e teste no celular

---

## FASE 5 — APROVAÇÃO DO ROBERTO

```
"✅ Checklist técnico concluído.

Instale o app no seu celular:
[Instruções de como acessar/instalar]

1. O visual está como esperava?
2. As funcionalidades estão funcionando?
3. Funciona bem no celular?

Responda APROVADO ou AJUSTES: [o que mudar]"
```
