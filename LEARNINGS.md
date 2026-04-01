# LEARNINGS.md — v2
# Aprendizados registrados ao longo dos projetos
# Atualizado automaticamente pelo agente após cada APROVADO

---

## Como funciona

O agente registra aqui após cada projeto aprovado.
Roberto pode adicionar observações manualmente.
Quanto mais projetos, mais inteligente fica o sistema.

---

## Formato padrão

```markdown
## [DATA] — Título
**Projeto:** nome do projeto
**Problema:** o que aconteceu
**Causa:** por que aconteceu
**Solução:** o que resolveu
**Regra:** o que fazer daqui em diante
```

---

## Aprendizados Registrados

### [2026-03] — Imagens em listagens nunca devem depender de API em tempo real
**Projeto:** Gotas de Amor
**Problema:** Cards com imagens repetidas ou sem imagem na homepage
**Causa:** API do Pexels com rate limit + cache ISR impedindo atualização + pexelsQuery ausente nos documentos do Sanity
**Solução:** Catálogo local de URLs verificadas por categoria, processamento em lotes de 2 com delay de 600ms
**Regra:** Em páginas de listagem, sempre usar catálogo verificado. Nunca depender de API externa em tempo real. Fallback de gradiente sempre implementado.

### [2026-03] — Emojis nunca devem ser usados como ícones em produção
**Projeto:** Gotas de Amor v2
**Problema:** Site gerado com emojis no lugar de ícones — visual não profissional
**Causa:** Skill não especificava padrão de ícones
**Solução:** Substituição por Lucide React
**Regra:** Sempre usar biblioteca SVG (Lucide React, Heroicons). Nunca emojis como ícones. Definir no Design System antes de codar.

### [2026-03] — Documentos importados no Sanity chegam como draft
**Projeto:** Gotas de Amor
**Problema:** 200 mensagens importadas mas não aparecem no site
**Causa:** Importação cria documentos como draft — precisam ser publicados separadamente
**Regra:** Todo script de importação deve incluir etapa de publicação. Verificar no CMS após importar.

### [2026-03] — Deploy não atualiza por causa do cache ISR
**Projeto:** Gotas de Amor
**Problema:** Site continua mostrando versão antiga mesmo após deploy com status Ready
**Causa:** next: { revalidate: 86400 } cacheia o HTML por 24h — novo deploy não invalida cache de fetch
**Solução:** Redeploy sem cache na Vercel ou mudar temporariamente para cache: 'no-store'
**Regra:** Para forçar atualização imediata: Redeploy → desmarcar "Use existing Build Cache"

---

*Novos aprendizados são adicionados automaticamente após cada projeto APROVADO.*
