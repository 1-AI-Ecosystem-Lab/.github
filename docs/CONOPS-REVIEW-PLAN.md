# Plano de Revisão dos CONOPS — 1-AI-Ecosystem-Lab

> Escopo: revisão de consistência e profundidade dos CONOPS de todos os projetos da org, tendo o **NEXUS** como baseline e o **README da org** (`1-AI-Ecosystem-Lab/.github`) como fonte de verdade para nomenclatura, camada (layer) e papel de cada componente.

## Nomenclatura canônica (fonte: README da org)

| Nome canônico | Repositório | Camada (Layer) | Status na org |
|---|---|---|---|
| Horizon | `open-webui-custom` *(rename pendente para `horizon`)* | Experience | estável |
| ARGO | `argo-agent-platform` | Agent Platform | ativo |
| NEXUS | `Nexus-congnitive-continuity-infraestructure` | Cognitive Continuity | ativo |
| OR-OmniRouter | `or-omni-router` | Inference Control | beta |
| DataHunter | `DataHunter` | Data Discovery | beta |
| Forge | `forge` | Capability OS | em desenvolvimento |
| DIR | `dir-dynamic-inference-routing` | Cognitive Decision | em desenvolvimento |
| Hydra | `hydra` | Operational Intelligence | em desenvolvimento |

## Status geral por projeto

| Projeto | CONOPS | ADRs reais | Ação |
|---|---|---|---|
| NEXUS | ✅ 22/22 — baseline | 19 | Nenhuma — referência |
| Horizon | ✅ 22/22 | 6 | Fora deste plano — revisão de ADRs (dono: Marco) |
| ARGO | ⚠️ 20/22, gaps estruturais | 20 | Revisão completa |
| DIR | ✅ 22/22, o mais profundo (2032 linhas) | 3 (+ naming inconsistente) | Revisão completa (foco leve) |
| OR-OmniRouter | ⚠️ 23/22, seções rasas | 20+ | Revisão completa |
| DataHunter | ⚠️ 22/22, item 11 sem handoff humano | 0 (só template) | Revisão completa + formalizar ADRs |
| Hydra | ❌ sem `docs/`, sem CONOPS | 0 (sem `docs/`) | Criar estrutura do zero |
| Forge | ❌ sem `docs/`, sem CONOPS | 0 (sem `docs/`) | Criar estrutura do zero |

## Checklist padrão (4 tarefas, aplicada a cada projeto)

### Tarefa 1 — Consistência do README
- [ ] Nome canônico usado (conforme tabela acima)
- [ ] Sigla usada de forma consistente ao longo do documento
- [ ] Camada (layer) declarada bate com a tabela da org
- [ ] "Papel em uma frase" é compatível com o README da org
- [ ] Status (estável / ativo / beta / em desenvolvimento) está atualizado

### Tarefa 2 — Alinhamento CONOPS ↔ README da org
- [ ] Seção 1 (Visão e Motivação) reflete a "limitação identificada" → "como a ACO responde" da tabela da org
- [ ] Papel do componente no CONOPS bate com a camada declarada
- [ ] Vocabulário (IHM/IHIAM, Cognitive Object, ACO, etc.) consistente com o README da org

### Tarefa 3 — Profundidade item a item (22 itens, baseline = NEXUS)
- [ ] Todos os 22 itens presentes com numeração canônica
- [ ] Nenhum item com profundidade muito abaixo da média do NEXUS (~64 linhas/seção) sem justificativa
- [ ] Subitens presentes onde o NEXUS também os tem

### Tarefa 4 — Leitura integral
- [ ] Estrutura lógica: sequência das seções coerente, sem contradição entre elas
- [ ] Escopo/objetivo consistentes (não mistura estágio MVP com produção madura)
- [ ] Gaps estruturais listados explicitamente
- [ ] Links de navegação para outros documentos (ADRs, SRS, sprints) presentes e válidos
- [ ] Lista exaustiva de questões em aberto, cada uma citando a ADR relacionada (existente ou "ADR a criar")

---

## Tarefas específicas por projeto

### 1. ARGO (`argo-agent-platform`)
ADRs disponíveis: 0001–0020 (langgraph, contrato retrieve-knowledge, avaliação de grafos, fallback provider, tool gateway, auditoria, classificação, api-first, health dashboard, log assíncrono, segurança de endpoints abertos, authn gap/interrupt-resume, reranker, jwt/rbac, policy engine, integration registry, arquitetura UI, plataforma de avaliação, studio deploy, prompts como artefatos vivos).

Gap conhecido: CONOPS sem seção equivalente a **"Requisitos Operacionais por Camada"** e sem **"Handoff para Curadoria Humana e Revisão Operacional"**. Ao revisar, checar se ADR-0011 (segurança de endpoints abertos) ou ADR-0012 (authn gap / interrupt-resume) já cobrem esse handoff — pode ser que a decisão exista em ADR mas nunca tenha subido pro CONOPS.

### 2. DIR (`dir-dynamic-inference-routing`)
ADRs disponíveis: `adr-001-scoring-model`, `adr-002-validation-policy`, `adr-003-fallback-policy` (+ template). Nomenclatura de arquivo inconsistente com o padrão da org (`ADR-0001-...` maiúsculo/4 dígitos vs `adr-00X-...` minúsculo/3 dígitos) — endereçar na Tarefa 1.

CONOPS já é o mais completo do ecossistema — foco aqui é Tarefa 1 e 2 (naming/alinhamento), Tarefas 3 e 4 tendem a ser rápidas.

### 3. OR-OmniRouter (`or-omni-router`)
CONOPS tem item extra (23 em vez de 22): **"22. Posição no Ecossistema AIT"** — nome desatualizado, a org não se chama mais "AIT". Corrigir para "1-AI-Ecosystem-Lab" ou "ACO".

Seção 11 (Handoff) é a mais rasa de todo o ecossistema (15 linhas) — cruzar com os ~20 ADRs existentes (ex: ADR-0006 autenticação/segurança do painel) para ver se o processo de handoff já está decidido em ADR e só falta detalhar no CONOPS.

### 4. DataHunter
Único projeto com CONOPS completo (22/22) mas **zero ADRs reais** — só o template. Há decisões já implementadas no código (`analyzer.py`, `downloader.py`, fontes Kaggle/HF/Zenodo, scoring de autoridade) que nunca foram formalizadas.

Gap: item 11 substitui **"Handoff para Curadoria Humana"** por **"Integração com PKGL"**. Confirmar se é uma decisão intencional (curadoria delegada ao PKGL) ou lacuna real — se intencional, documentar como ADR.

Ação: formalizar ADRs retroativas antes ou durante a revisão do CONOPS.

### 5. Hydra
Sem `docs/`, sem CONOPS, sem ADRs — só README (visão/produto, robusto). Camada: Operational Intelligence (observabilidade cognitiva, LLMOps, AgentOps, FinOps, auditoria, drift, qualidade).

Ação:
1. Criar estrutura `docs/` a partir do `ait-ai-system-project-template`
2. Redigir CONOPS usando o NEXUS como referência estrutural, adaptado ao domínio de observabilidade
3. Formalizar como ADRs as decisões já implícitas no README (ex: pipeline "Evento → Coleta → Correlação → Análise → Indicadores → Ação")

### 6. Forge
Mesma situação de Hydra — sem `docs/`, sem CONOPS, sem ADRs, só README robusto. Camada: Capability OS (publica, descobre, governa e compõe elementos executáveis da ACO).

Ação: mesmos 3 passos de Hydra.

---

## Ordem sugerida de execução

1. **Hydra e Forge** — criar estrutura do zero (maior gap, bloqueia qualquer comparação futura)
2. **DataHunter** — formalizar ADRs retroativas + resolver dúvida do item 11
3. **ARGO** — gaps estruturais mais graves entre os que já têm CONOPS
4. **OR-OmniRouter** — corrigir nome desatualizado "AIT" + aprofundar seção de Handoff
5. **DIR** — já é o mais completo; revisão de naming/alinhamento apenas

## Fora de escopo deste plano

- **NEXUS** — considerado baseline, sem revisão necessária
- **Horizon** — CONOPS considerado ok; pendência isolada é a revisão de ADRs, tratada separadamente

---

*Gerado a partir de análise comparativa dos 8 repositórios da org em 2026-07-09.*
