# skill: content — v3
# Quando usar: criação de textos, importação em lote, conteúdo para CMS
# Gatilho: "criar conteúdo", "mensagens", "textos", "importar", "CMS"

---

## FASE 1 — BRIEFING

**Regra:** Máximo 1 pergunta se algo crítico faltar. Assume e declara o resto.

### Perguntas obrigatórias

1. **Objetivo:** Para que serve o conteúdo? (mensagens, artigos, produtos, FAQs)
2. **Tom de voz:** Como deve soar? (formal, informal, inspiracional, técnico, persuasivo)
3. **Público:** Quem vai ler? (idade, perfil, contexto)
4. **Destino:** Onde vai publicar? (site, app, CMS, redes sociais)

### Modo PADRÃO (além das obrigatórias)
5. **Volume:** Quantos textos precisa?
6. **Categorias:** Tem categorias ou temas definidos?
7. **Estrutura:** Cada texto precisa de quê? (título, subtítulo, tags, SEO)
8. **Palavras-chave SEO:** Tem termos alvo por categoria?

### Padrões inteligentes

| Decisão | Padrão |
|---------|--------|
| SEO | Sempre otimizado para Google |
| Slug | Sempre gerado do título (kebab-case, sem acentos) |
| Publicação | Sempre verificar se publicado (não draft) |
| Lorem Ipsum | NUNCA — conteúdo sempre realista e contextualizado |

---

## FASE 2 — DEFINIÇÃO

```
"Vou criar [X] textos em [Y] categorias.
Tom: [escolha + exemplo de frase no tom]
Formato: [estrutura de cada texto]
SEO: [estratégia de palavras-chave]

Confirma para começar?"
```

---

## FASE 3 — EXECUÇÃO

### Copywriting — Benefícios, Nunca Funcionalidades

| Funcionalidade ❌ | Benefício ✅ |
|---|---|
| "Sistema de mensagens" | "Encontre a palavra certa para cada momento" |
| "200 categorias" | "De bom dia a declaração de amor — tudo em um lugar" |
| "Compartilhamento integrado" | "Envie pelo WhatsApp com 1 clique" |

**Regras universais:**
- Voz ativa e direta
- Numerais para números: "8 categorias" não "oito categorias"
- Evite superlativas vazias: "incrível", "revolucionário", "melhor do mundo"
- Termine CTAs com ação: "Ver mensagens", "Copiar texto", "Compartilhar agora"

**Tom por segmento:**

| Segmento | Tom | Evite |
|---|---|---|
| Mensagens afetivas | Caloroso, genuíno, humano | Artificialidade, clichês |
| Conteúdo religioso | Respeitoso, inspirador | Imposição, exclusividade |
| Motivacional | Direto, energético | Promessas vazias |
| Institucional | Claro, confiável | Jargão excessivo |

### Estrutura JSON para Importação

```json
[
  {
    "titulo": "Título direto e claro (3-8 palavras)",
    "texto": "Conteúdo completo. Nunca truncar no meio.",
    "categoria": "nome-da-categoria",
    "tags": ["tag1", "tag2", "tag3"],
    "destaque": false,
    "seoTitle": "Título SEO — máx 60 caracteres",
    "seoDescription": "Descrição para o Google — máx 160 caracteres"
  }
]
```

### Regras de Criação

**Títulos:**
- 3 a 8 palavras, diretos e descritivos
- Evitar genéricos: "Mensagem bonita", "Texto legal"
- Varie o início: não repita a mesma abertura em sequência

**Textos:**
- Completos — nunca truncar
- Uma ideia central por texto
- Tom consistente dentro da categoria
- Realistas — sem Lorem Ipsum, sem placeholders

**Categorias e Slugs:**
```typescript
function slugify(text: string): string {
  return text
    .toLowerCase()
    .normalize('NFD')
    .replace(/[\u0300-\u036f]/g, '')
    .replace(/[^a-z0-9\s-]/g, '')
    .trim()
    .replace(/\s+/g, '-')
}
// "Fé e Espiritualidade" → "fe-e-espiritualidade"
```

### Importação no Sanity

1. Gera JSON com conteúdo
2. Script `scripts/import-content.ts` com token Editor
3. Lotes de 10 com delay 200ms
4. Verifica contagem de importados e erros
5. **Publica** — documentos chegam como draft

```typescript
const doc = {
  _type: 'mensagem',
  titulo: item.titulo,
  slug: { _type: 'slug', current: slugify(item.titulo) },
  texto: item.texto,
  categoria: item.categoria,
  tags: item.tags,
  destaque: item.destaque ?? false,
}
```

---

## FASE 4 — CHECKLIST TÉCNICO

- [ ] Sem erros de português
- [ ] Todos os textos completos (nenhum truncado)
- [ ] Títulos únicos (sem duplicatas)
- [ ] Tom consistente na categoria
- [ ] Slugs únicos e em kebab-case
- [ ] Documentos publicados (não apenas draft)
- [ ] seoTitle ≤ 60 caracteres
- [ ] seoDescription ≤ 160 caracteres

---

## FASE 5 — APROVAÇÃO DO ROBERTO

```
"✅ [X] textos importados em [Y] categorias.

Acesse: [URL do site ou CMS]

1. O tom está certo?
2. As categorias estão corretas?
3. Tem algo para ajustar?

Responda APROVADO ou AJUSTES: [o que mudar]"
```
