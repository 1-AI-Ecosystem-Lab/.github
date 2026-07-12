# Plano de Revisão dos CONOPS — 1-AI-Ecosystem-Lab

> Escopo: revisão de consistência e profundidade dos CONOPS de todos os projetos da org, tendo o **NEXUS** como baseline e o **README da org** (`1-AI-Ecosystem-Lab/.github`) como fonte de verdade para nomenclatura, camada (layer) e papel de cada componente.

## Raiz do problema de nomenclatura (fonte corrigida em 2026-07-12)

Boa parte do drift de nomenclatura encontrado nos projetos (org antiga, "AIT Standard", integrações com "PKGL") **não é independente por projeto — vem de uma fonte comum**: o template `2-AI-System/ait-ai-system-project-template` (usado para gerar a estrutura `docs/` de todos os projetos) documentava, em `ECOSSISTEMA.md`, um ecossistema anterior de 5 projetos sob a org extinta `1-AI-DECISION-LAB` (`open-webui-custom`, `DIR`, `OR`, `PKGL`, `DataHunter`), com o padrão de 8 camadas batizado de "AIT Standard".

**PKGL foi renomeado/evoluído para NEXUS** — confirmado: mesmos verbos operacionais ("Catalogar · Preparar · Distribuir") e o clone local órfão `PKGL-personal-knowledge-governance-layer` (remote `1-AI-DECISION-LAB`, extinto) já tem o README do NEXUS como conteúdo.

O template já foi corrigido: `ECOSSISTEMA.md` reduzido a ponteiro para este plano e para o `aco-cognitive-architecture`, "AIT Standard" renomeado para **ACO Component Layer Model**. Falta propagar a correção para os projetos que herdaram a nomenclatura antiga — isso agora faz parte da Tarefa 1 de cada projeto abaixo.

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

## Arquitetura Transversal do ACO (fonte: `aco-cognitive-architecture`)

**Fato novo (2026-07-11):** o repositório [`aco-cognitive-architecture`](https://github.com/1-AI-Ecosystem-Lab/aco-cognitive-architecture), pasta `docs/03-arquitetura`, contém **15 ADRs ratificados (Aceito)** com impacto transversal — obrigatórios para todos os componentes, não apenas orientação. README e CONOPS de cada projeto passam a ter um **terceiro critério de conformidade**, além do alinhamento com o próprio README da org: alinhamento com estas decisões cross-component.

| ADR (aco) | Decisão | Vincula |
|---|---|---|
| ADR-0001 | Evolution Governance Record + protocolo de interop como contrato obrigatório entre componentes | todos |
| ADR-0002 | Taxonomia de autoevolução (§6 da RFC-0001) como ontologia obrigatória de classificação | todos que classificam tarefas/agentes (ARGO, DIR) |
| ADR-0003 | Critério de escopo: quando uma decisão de componente exige RFC/ADR cross-component da ACO | todos — usar antes de aceitar qualquer ADR local |
| ADR-0004 | **ACO Interop Envelope** como contrato obrigatório entre componentes (`governance_metadata`/`security_context`/`payload`) | todos que trocam mensagens entre componentes |
| ADR-0005 | Contrato de exportação mínimo do Hydra como interface obrigatória (adoção opcional por tenant) | Hydra (dono) + todos que exportam evidência |
| ADR-0006 | **ACO Identity Context** como contrato obrigatório de identidade cross-component | todos que propagam identidade/roles entre componentes |
| ADR-0007 | Autoevolução como capacidade transversal, não componente monolítico | todos |
| ADR-0008 | Forge como autoridade de publicação de artefatos executáveis | Forge (dono) + todos que publicam artefatos |
| ADR-0009 | Hydra como autoridade de evidência, avaliação e rollback | Hydra (dono) + todos que fazem autoevolução |
| ADR-0010 | Evolução produtiva exige rollout progressivo e regressão contínua | todos que fazem autoevolução |
| ADR-0011 | Separação entre memória episódica, reflexão, conhecimento e procedimento | NEXUS (dono) |
| ADR-0012 | NEXUS como autoridade de curadoria na fronteira de reutilização de memória (gate sempre HITL) | NEXUS (dono) + todos que reutilizam memória |
| ADR-0013 | Políticas críticas não podem ser autoalteradas pelo agente que elas governam | ARGO (policy engine), DIR (validation policy) |
| ADR-0014 | Agentic Workstream como objeto compartilhado, **Horizon como dono** | Horizon (dono) + ARGO (produz workstream) |
| ADR-0015 | Tipologia de casos de uso de sistemas cognitivos autoevolutivos como taxonomia oficial | todos |

> Nota de numeração: ADR-0012 e ADR-0014 desta arquitetura **não** têm relação com o ADR-0012 e ADR-0014 do Horizon (`open-webui-custom`) — são numerações independentes em repositórios distintos.

## Status geral por projeto

| Projeto | CONOPS | ADRs reais | Conformidade ACO transversal | Ação |
|---|---|---|---|---|
| NEXUS | ✅ 22/22 — baseline | 19 | dono de ADR-0011/0012 — checar se já refletidos localmente | Nenhuma — referência |
| Horizon | ✅ 22/22 | 6 (+ 2 em Proposta) | **pendências concretas mapeadas** — ver seção dedicada abaixo | Aplicar `RECONCILIACAO-HORIZON.md` |
| ARGO | ⚠️ 20/22, gaps estruturais | 20 | checar ADR-0002/0013 (policy engine) e ADR-0014 (produz workstream) | Revisão completa + Tarefa 0 |
| DIR | ✅ 22/22, o mais profundo (2032 linhas) | 3 (+ naming inconsistente) | checar ADR-0002/0013 (validation/fallback policy) | Revisão completa (foco leve) + Tarefa 0 |
| OR-OmniRouter | ⚠️ 23/22, seções rasas | 20+ | checar ADR-0004/0006 (interop/identity entre providers) | Revisão completa + Tarefa 0 |
| DataHunter | ⚠️ 22/22, item 11 sem handoff humano | 0 (só template) | checar ADR-0012 (reuso de memória/curadoria, se integra com NEXUS) | Revisão completa + formalizar ADRs + Tarefa 0 |
| Hydra | ❌ sem `docs/`, sem CONOPS | 0 (sem `docs/`) | **dono de ADR-0005/0009** — CONOPS deve nascer já alinhado | Criar estrutura do zero + Tarefa 0 |
| Forge | ❌ sem `docs/`, sem CONOPS | 0 (sem `docs/`) | **dono de ADR-0008** — CONOPS deve nascer já alinhado | Criar estrutura do zero + Tarefa 0 |

## Checklist padrão (5 tarefas, aplicada a cada projeto)

### Tarefa 0 — Conformidade com a arquitetura transversal do ACO
- [ ] Componente usa o **ACO Interop Envelope** (ADR-0004) ao trocar mensagens com outros componentes, ou declara explicitamente por que não se aplica ainda
- [ ] Componente propaga identidade via **ACO Identity Context** (ADR-0006) quando age em nome de outro ator, ou declara escopo local sem propagação
- [ ] Se o componente classifica tarefas/agentes, usa a taxonomia de autoevolução do ADR-0002/ADR-0015 (não inventa taxonomia própria)
- [ ] Se o componente tem políticas críticas (ex.: policy engine, validation policy), confirma que elas não são autoalteráveis pelo agente que governam (ADR-0013)
- [ ] Se o componente faz autoevolução/atualização de comportamento, usa rollout progressivo + regressão contínua (ADR-0010)
- [ ] Se o componente exporta evidência/observabilidade, usa o contrato mínimo do Hydra (ADR-0005), sem obrigação de expor dados brutos
- [ ] Nenhuma decisão local contradiz um ADR transversal Aceito — se contradiz, aplicar o critério de escopo do ADR-0003 (aco) para decidir se precisa de RFC/ADR cross-component

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

**Achado confirmado (2026-07-12): "PKGL" = nome antigo do NEXUS.** O template-fonte (`2-AI-System/ait-ai-system-project-template`) documentava um ecossistema anterior de 5 projetos sob a org extinta `1-AI-DECISION-LAB` (`open-webui-custom`, `DIR`, `OR`, `PKGL`, `DataHunter`). PKGL tinha exatamente os mesmos verbos operacionais do NEXUS ("Catalogar · Preparar · Distribuir") — confirmado comparando o clone local órfão `~/GitHub/PKGL-personal-knowledge-governance-layer` (remote aponta pro `1-AI-DECISION-LAB` extinto, mas o conteúdo do README já é literalmente o NEXUS). PKGL foi renomeado/evoluído para NEXUS; o CONOPS do DataHunter nunca foi atualizado após essa transição.

Gap (revisado): item 11 ("Integração com PKGL — Sinais de Confronto") não é uma lacuna de handoff humano isolada — é uma **referência a um componente que não existe mais com esse nome**. Toda a arquitetura de integração downstream do DataHunter (§1.2, §2.1, §3.2-3.4, §6, §9.3, §11 inteiro, §12-13, §17.5, §19.1, §21.1-Q03) é modelada em torno do PKGL. Decisão necessária: renomear as referências para NEXUS mantendo o conceito de "Sinais de Confronto", ou tratar como integração genuinamente distinta (se o time decidiu que DataHunter fala com um sucessor específico do PKGL diferente do NEXUS atual). Tratar como ADR — é uma decisão arquitetural, não um ajuste de texto.

Também "AIT Standard" (linha 6, 65, 100, 219, roadmap Fase 0/Histórico de Versões) e 3 variantes do nome antigo da org ("1-AI-DECISION-LAB", "AI-DECISION-LAB", "AI Decision Lab") aparecem no README — herdados do mesmo template. O template-fonte já foi corrigido (`ECOSSISTEMA.md` reduzido a ponteiro, termo renomeado para "ACO Component Layer Model") — falta propagar a correção para o README/CONOPS do DataHunter.

Ação: (1) corrigir nomenclatura da org e "AIT Standard" no README; (2) decidir e documentar via ADR o destino da integração PKGL→NEXUS; (3) formalizar ADRs retroativas para as demais decisões já implementadas no código.

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

## Horizon — pendências concretas (fonte: `RECONCILIACAO-HORIZON.md`)

CONOPS considerado ok; a pendência de "revisar os ADRs" **não é genérica** — já existe um documento pronto (`aco-cognitive-architecture/docs/03-arquitetura/decisoes/RECONCILIACAO-HORIZON.md`, rascunhado em 2026-07-11, ainda não aplicado no repo do Horizon) com o texto exato de cada nota de reconciliação. Nenhuma decisão já Aceita do Horizon é invalidada — são pontes declaradas, sem retrabalho.

- [ ] **ADR-0003** (Protocolo Interno de Agentes / Gateway MCP) — colar nota: o HIP permanece intacto; ao comunicar com outro componente ACO, a mensagem trafega dentro do ACO Interop Envelope (`core_payload` do HIP ocupa `payload.body`)
- [ ] **ADR-0004** (Persistência de Logs de Observabilidade e Soberania) — colar nota: arquitetura dual (OTel + tabelas relacionais) continua fonte de verdade local; habilitar opcionalmente o contrato de exportação mínimo do Hydra (sinais agregados `evolution`/`cost`/`quality`, nunca dados brutos) para cumprir a promessa do CONOPS §3 sobre o Hydra
- [ ] **ADR-0006** (Medição de Redução de Repetição / FinOps) — colar nota: `tokens_avoided`/`cost_estimate` já calculados mapeiam direto para o campo `cost` do contrato de exportação do Hydra, sem recálculo
- [ ] **ADR-0012** (Gestão de Identidade, SSO e Cofre Local — ainda **Status Proposta**, seção de Decisão vazia) — **intervenção preventiva**: ao preencher a decisão, declarar como o IdP escolhido traduz identidade local para o `aco_identity_context` (actor_type, actor_id, tenant_id, roles, provenance, delegation_chain) e como trata `delegation_chain` para agentes agindo em nome de usuários (cenário já previsto no CONOPS §8)
- [ ] **ADR-0014** (Stack de Observabilidade Técnica e Tracing — ainda **Status Proposta**, seção de Decisão vazia) — ao preencher a decisão, declarar se/como os traces técnicos alimentam o Hydra como sinal `quality` do contrato de exportação

Responsabilidade de aplicação: equipe do Horizon (Marco). Este plano não altera o repositório do Horizon.

## Fora de escopo deste plano

- **NEXUS** — considerado baseline, sem revisão necessária (mas é dono de ADR-0011/ADR-0012 da arquitetura transversal — vale checar se já refletidos localmente)

---

*Gerado a partir de análise comparativa dos 8 repositórios da org em 2026-07-09. Atualizado em 2026-07-11 com a camada de conformidade transversal do `aco-cognitive-architecture`.*
