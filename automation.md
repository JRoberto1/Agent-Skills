# skill: automation — v2
# Quando usar: scripts, integrações, automações, bots, processamento de dados
# Gatilho: "automatizar", "script", "integração", "bot", "processar dados", "API"

---

## FASE 1 — BRIEFING

### Escolha o modo:
**[RÁPIDO]** → 5 perguntas. Para scripts simples.
**[PADRÃO]** → 10 perguntas. Para automações completas.
**[COMPLETO]** → Todos os blocos. Para sistemas complexos.

---

### Perguntas SEMPRE obrigatórias

1. **O que faz:** Descreva em uma frase o que a automação deve fazer
2. **Disparo:** O que inicia a automação? (horário fixo, evento, manual, webhook)
3. **Entrada:** Qual é o dado de entrada? (arquivo, API, banco de dados, formulário)
4. **Saída:** Qual é o resultado esperado? (arquivo, e-mail, banco, API, relatório)
5. **Frequência:** Roda uma vez ou repetidamente? Com que intervalo?

---

### Perguntas do modo PADRÃO

6. **Onde roda:** Local, servidor, nuvem? (define a linguagem e estrutura)
7. **APIs:** Integra com algum serviço externo? Tem as credenciais?
8. **Volume:** Quantos itens processa por vez? (define estratégia de lotes)
9. **Erros:** O que fazer se falhar? (para tudo, pula o item, tenta de novo)
10. **Logs:** Precisa de registro do que foi processado?

---

### Perguntas do modo COMPLETO

11. **Segurança:** Processa dados sensíveis? (CPF, cartão, senha)
12. **Notificação:** Deve avisar quando terminar ou falhar?
13. **Reversão:** Precisa desfazer em caso de erro?
14. **Monitoramento:** Precisa de alertas em tempo real?
15. **Escalabilidade:** Volume pode crescer muito no futuro?

---

### Padrões inteligentes

| Decisão | Padrão assumido |
|---------|----------------|
| Linguagem padrão | Python (mais versátil para automação) |
| Tratamento de erro | Sempre — nunca para no primeiro erro |
| Log de execução | Sempre — sucesso e erro registrados |
| Variáveis de ambiente | Sempre em .env |
| Retry em falha de API | Sempre — 3 tentativas com delay exponencial |
| Processamento em lote | Sempre que volume > 10 itens |

---

## FASE 2 — DEFINIÇÃO

Após briefing, agente apresenta e justifica:

```
"Com base no que você me disse, escolhi:
- Linguagem: [Python/Node.js + motivo]
- Disparo: [cron/webhook/manual + motivo]
- Estratégia de erros: [continua/para/retry + motivo]
- Hospedagem: [local/GitHub Actions/servidor + motivo]

Confirma para começar?"
```

---

### Escolha de Linguagem

| Situação | Linguagem |
|----------|-----------|
| Script simples, uso local | Python |
| Integração com APIs web | Python ou Node.js |
| Automação de navegador | Python + Playwright |
| Processamento de Excel/CSV | Python + pandas |
| Webhook/servidor leve | Node.js + Express |
| Integração com Google Workspace | Python + gspread |

---

### Escolha de Hospedagem/Agendamento

| Situação | Solução |
|----------|---------|
| Roda no computador de Roberto | Script local + agendador Windows |
| Roda na nuvem (grátis) | GitHub Actions |
| Roda na nuvem (pago, simples) | Railway ou Render |
| Roda em servidor existente | crontab Linux |
| Trigger por evento externo | Webhook + servidor leve |

---

## FASE 3 — EXECUÇÃO

### Estrutura Padrão de Script Python

```python
#!/usr/bin/env python3
"""
Nome: [nome do script]
Função: [o que faz em uma linha]
Autor: Roberto via Claude Code
Data: [data de criação]
"""

import os
import time
import logging
from dotenv import load_dotenv

# Configuração de log
logging.basicConfig(
    level=logging.INFO,
    format='%(asctime)s - %(levelname)s - %(message)s'
)
log = logging.getLogger(__name__)

load_dotenv()

def main():
    log.info("Iniciando automação...")
    sucessos = 0
    erros = 0
    
    itens = obter_itens()
    log.info(f"Total a processar: {len(itens)}")
    
    for i, item in enumerate(itens):
        try:
            processar(item)
            sucessos += 1
            log.info(f"✅ [{i+1}/{len(itens)}] {item} processado")
        except Exception as e:
            erros += 1
            log.error(f"❌ [{i+1}/{len(itens)}] Erro em {item}: {e}")
    
    log.info(f"Finalizado: {sucessos} ok, {erros} erros")

def processar(item):
    """Processa um item individual"""
    pass

def obter_itens():
    """Retorna lista de itens para processar"""
    pass

if __name__ == "__main__":
    main()
```

### Processamento em Lote (Padrão)

```python
def processar_em_lotes(lista, tamanho=10, delay=0.5):
    """Processa lista em lotes respeitando rate limits"""
    for i in range(0, len(lista), tamanho):
        lote = lista[i:i + tamanho]
        for item in lote:
            processar(item)
        log.info(f"Lote {i//tamanho + 1} concluído")
        if i + tamanho < len(lista):
            time.sleep(delay)
```

### Retry com Delay Exponencial (Padrão para APIs)

```python
def chamar_api(url, max_tentativas=3):
    for tentativa in range(max_tentativas):
        try:
            response = requests.get(url, timeout=10)
            if response.status_code == 200:
                return response.json()
            elif response.status_code == 429:
                wait = 2 ** tentativa
                log.warning(f"Rate limit. Aguardando {wait}s...")
                time.sleep(wait)
            else:
                log.error(f"Erro {response.status_code}")
                return None
        except Exception as e:
            if tentativa == max_tentativas - 1:
                raise e
            time.sleep(2 ** tentativa)
    return None
```

---

## FASE 4 — CHECKLIST TÉCNICO

### Funcionalidade
- [ ] Script roda sem erros em dado real (não mock)
- [ ] Não para no primeiro erro — processa todos os itens
- [ ] Log claro: o que foi processado, o que deu erro
- [ ] Tratamento de rate limit implementado (se usa API)
- [ ] Timeout configurado em todas as chamadas de rede

### Segurança
- [ ] Nenhuma chave de API no código
- [ ] .env.example criado com todas as variáveis
- [ ] .env no .gitignore
- [ ] Dados sensíveis não aparecem nos logs

### Qualidade
- [ ] Testado com volume real de dados
- [ ] Testado com dados inválidos/faltando
- [ ] Resultado final verificado manualmente

### Documentação
- [ ] README com instruções de instalação e uso
- [ ] Variáveis de ambiente documentadas
- [ ] Exemplo de como rodar o script

---

## FASE 5 — APROVAÇÃO DO ROBERTO

```
"✅ Checklist técnico concluído.

A automação foi testada com dados reais.
Resultado: [X processados, Y erros]

Verifique o resultado em: [onde ver o resultado]

1. O resultado está correto?
2. Tem algo para ajustar?

Responda APROVADO ou AJUSTES: [o que mudar]"
```

---

## Problemas Comuns e Soluções

| Problema | Causa | Solução |
|----------|-------|---------|
| Script para no primeiro erro | Sem try/except | Envolva cada item em try/except |
| API retorna 429 | Rate limit excedido | Implemente delay entre requests |
| Credenciais não encontradas | .env não carregado | Verifique load_dotenv() no início |
| Script lento com muitos itens | Sem lotes | Implemente processamento em lote |
| Resultado inconsistente | Sem log | Adicione logging detalhado |
| Dados corrompidos | Sem validação | Valide entrada antes de processar |
