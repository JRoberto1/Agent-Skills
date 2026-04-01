# skill: debug — v3
# Quando usar: algo quebrou, erro, comportamento inesperado
# Gatilho: "não funciona", "erro", "quebrou", "não aparece", "não carrega"

---

## Regra Principal

**Nunca tente a mesma solução mais de 2 vezes.**
Identifique a causa raiz antes de tentar de novo.
**Corrija cirurgicamente — não jogue fora o que funciona.**

---

## FASE 1 — DIAGNÓSTICO

Antes de qualquer correção:

1. O que exatamente está acontecendo? (erro completo)
2. O que deveria acontecer?
3. Quando começou? (após qual mudança)
4. Acontece sempre ou às vezes?
5. Local, produção ou ambos?

---

## FASE 2 — LEITURA DO ERRO

```bash
# Build Next.js
npm run build 2>&1 | head -50

# Lint
npm run lint 2>&1
```

**No navegador:** DevTools (F12) → Console → filtre por Errors → o primeiro é o mais importante

**Na rede:** DevTools → Network → Fetch/XHR → clique no erro → veja Response e Status

**Na Vercel:** Deployments → clique no deploy com erro → leia as últimas linhas antes de "Error"

---

## FASE 3 — DIAGNÓSTICO POR TIPO

### Imagens não carregando
1. Abra a URL da imagem direto no navegador
2. Status 200 → problema no componente
3. Status 403 → API key inválida
4. Status 429 → rate limit → implemente delay de 600ms entre lotes de 2
5. Status 000 → rede local bloqueando → teste em produção

### Visual "AI Slop" / Genérico
1. Verifica se foi aplicada uma direção de design (web.md)
2. Verifica se há emojis como ícones → substitui por Lucide SVG
3. Verifica se há gradiente roxo/azul → substitui pela paleta da direção
4. Verifica se há Lorem Ipsum → substitui por conteúdo realista

### Deploy não atualiza
1. `git log --oneline -3` → confirme push
2. Status na Vercel → se Error, leia log
3. Status Ready mas site antigo → Ctrl+Shift+R
4. Ainda antigo → cache ISR → Redeploy sem cache

### Variável de ambiente não funciona
1. Está em `.env.local`? (não `.env`)
2. Next.js browser: precisa de `NEXT_PUBLIC_`
3. Vercel: Settings → Environment Variables
4. Após adicionar: novo deploy obrigatório

### Menu mobile não funciona
1. `aria-expanded` está sendo atualizado?
2. `hidden` do painel está alternando?
3. Use o componente padrão da `skills/web.md`

---

## FASE 4 — CORREÇÃO

1. Identifica causa raiz (não sintoma)
2. Propõe solução antes de executar
3. Executa correção
4. Testa que resolveu
5. Confirma que não quebrou nada mais

**Se travar após 2 tentativas:**
```
"Tentei [X] e [Y], o problema persiste.
Preciso saber: [pergunta específica para diagnosticar]"
```

---

## FASE 5 — REGISTRO

Após resolver, registra no `LEARNINGS.md`:

```markdown
## [DATA] — [Título]
**Problema:** o que quebrou
**Causa raiz:** por que aconteceu
**Solução:** o que resolveu
**Prevenção:** como evitar no futuro
```

---

## Referência Rápida

| Erro | Causa | Solução |
|------|-------|---------|
| `let` never reassigned | ESLint | Troque por `const` |
| Cannot find module | Import errado | Verifique o caminho |
| Hydration mismatch | Server ≠ client | Verifique dados dinâmicos SSR |
| 429 Too Many Requests | Rate limit | Lotes de 2 com 600ms de delay |
| CORS error | Backend não permite | Configure CORS no servidor |
| Blank page after deploy | Erro runtime | Abra console do navegador |
| Build local ok, Vercel falha | Variável faltando | Verifique Env Variables Vercel |
| Imagens repetindo | Fallback igual | Seeds únicos no picsum |
| Site não atualiza | Cache ISR | Redeploy sem cache |
| Visual genérico | Sem direção de design | Aplicar direção da web.md |
