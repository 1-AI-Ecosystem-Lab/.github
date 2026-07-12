# Plano de Revisão dos CONOPS — 1-AI-Ecosystem-Lab

> Escopo: revisão de consistência, profundidade e conformidade dos CONOPS de todos os projetos da org, tendo o **NEXUS** como baseline estrutural, o **README da org** como fonte da visão executiva e o repositório **`aco-cognitive-architecture`** como fonte normativa das decisões transversais.

## Raiz do problema de nomenclatura (fonte corrigida em 2026-07-12)

Boa parte do drift de nomenclatura encontrado nos projetos (org antiga, "AIT Standard", integrações com "PKGL") **não é independente por projeto — vem de uma fonte comum**: o template `2-AI-System/ait-ai-system-project-template`, usado para gerar a estrutura `docs/` dos projetos, documentava um ecossistema anterior sob a org extinta `1-AI-DECISION-LAB`.

**PKGL foi renomeado/evoluído para NEXUS.** O template já foi corrigido: `ECOSSISTEMA.md` foi reduzido a um ponteiro para este plano e para `aco-cognitive-architecture`, e "AIT Standard" foi renomeado para **ACO Component Layer Model**. Falta propagar a correção para os projetos que herdaram a nomenclatura antiga.

## Nomenclatura canônica dos componentes

| Nome canônico | Repositório | Camada | Status na org |
|---|---|---|---|
| Horizon | `open-webui-custom` *(rename pendente para `horizon`)* | Experience | estável |
| ARGO | `argo-agent-platform` | Agent Platform | ativo |
| NEXUS | `Nexus-congnitive-continuity-infraestructure` | Cognitive Continuity | ativo |
| OR-OmniRouter | `or-omni-router` | Inference Control | beta |
| DataHunter | `DataHunter` | Data Discovery | beta |
| Forge | `forge` | Capability OS | em desenvolvimento |
| DIR | `dir-dynamic-inference-routing` | Cognitive Decision | em desenvolvimento |
| Hydra | `hydra` | Operational Intelligence | em desenvolvimento |

## Identificação canônica das ADRs

Para evitar ambiguidade entre ADRs com a mesma numeração em repositórios distintos, referências textuais devem usar o namespace do domínio:

```text
ACO-ADR-0004
HORIZON-ADR-0012
ARGO-ADR-0015
DIR-ADR-0002
OR-ADR-0006
NEXUS-ADR-0011
FORGE-ADR-0001
HYDRA-ADR-0001
DATAHUNTER-ADR-0001
```

Regras:

- [ ] usar o identificador canônico em READMEs, CONOPS, RFCs, issues, commits e referências cruzadas;
- [ ] não renomear arquivos existentes em massa nesta etapa, para não quebrar links;
- [ ] novos ADRs devem adotar `<NAMESPACE>-ADR-NNNN-<slug>.md` ou declarar o identificador canônico no cabeçalho;
- [ ] planejar migração controlada dos nomes físicos, com atualização integral de links e compatibilidade documental.

## Arquitetura transversal da ACO

O repositório [`aco-cognitive-architecture`](https://github.com/1-AI-Ecosystem-Lab/aco-cognitive-architecture), especialmente [`docs/03-arquitetura`](https://github.com/1-AI-Ecosystem-Lab/aco-cognitive-architecture/tree/main/docs/03-arquitetura), contém as decisões ratificadas com impacto transversal. Essas decisões são obrigatórias para os componentes vinculados, não apenas orientações.

| ADR canônico | Decisão | Vincula |
|---|---|---|
| ACO-ADR-0001 | Evolution Governance Record e governança de mutações | todos os produtores de artefatos governados |
| ACO-ADR-0002 | Taxonomia de autoevolução como ontologia obrigatória | ARGO, DIR e classificadores |
| ACO-ADR-0003 | Critério de escopo para RFC/ADR cross-component | todos |
| ACO-ADR-0004 | ACO Interop Envelope obrigatório entre componentes | todos que trocam mensagens |
| ACO-ADR-0005 | Contrato mínimo de exportação de evidências do Hydra | Hydra e emissores de evidência |
| ACO-ADR-0006 | ACO Identity Context obrigatório | todos que propagam identidade e delegação |
| ACO-ADR-0007 | Autoevolução como capacidade transversal | todos os aplicáveis |
| ACO-ADR-0008 | Forge como autoridade de publicação | Forge e publicadores de artefatos |
| ACO-ADR-0009 | Hydra como autoridade de evidência, avaliação e rollback | Hydra e componentes autoevolutivos |
| ACO-ADR-0010 | Rollout progressivo e regressão contínua | componentes com evolução produtiva |
| ACO-ADR-0011 | Separação entre memória episódica, reflexão, conhecimento e procedimento | NEXUS |
| ACO-ADR-0012 | NEXUS como autoridade de curadoria para reutilização de memória | NEXUS e consumidores de memória |
| ACO-ADR-0013 | Políticas críticas não autoalteráveis | ARGO e DIR |
| ACO-ADR-0014 | Agentic Workstream compartilhado, com Horizon como autoridade | Horizon e ARGO |
| ACO-ADR-0015 | Tipologia oficial de casos de uso autoevolutivos | todos |

## Estados de adoção de uma decisão

Um ADR aceito indica ratificação, mas não demonstra implementação ou conformidade. Cada decisão deve ser acompanhada em três dimensões:

| Estado | Significado |
|---|---|
| **Ratificado** | Decisão arquitetural aprovada e normativa. |
| **Implementado** | Código, configuração, schema ou processo correspondente existe. |
| **Conformidade verificada** | Teste, revisão ou auditoria comprova aderência. |

O registro inicial e o mapa ADR → componente → implementação estão no [README da arquitetura normativa](https://github.com/1-AI-Ecosystem-Lab/aco-cognitive-architecture/blob/main/docs/03-arquitetura/README.md).

## Status geral por projeto

| Projeto | CONOPS | ADRs locais | Conformidade ACO transversal | Ação |
|---|---|---|---|---|
| NEXUS | ✅ 22/22 — baseline | 19 | checar ACO-ADR-0011/0012 e vincular evidências | Revisão de conformidade |
| Horizon | ✅ 22/22 | 6 (+ 2 em Proposta) | reconciliação parcial mapeada | Concluir adoção e evidências |
| ARGO | ⚠️ 20/22, gaps estruturais | 20 | verificar ACO-ADR-0002/0013/0014 | Revisão completa |
| DIR | ✅ 22/22, alta profundidade | 3 (+ naming inconsistente) | reconciliar ACO-ADR-0002/0013/0015 | Revisão focada |
| OR-OmniRouter | ⚠️ 23/22, seções rasas | 20+ | incorporar ACO-ADR-0004/0006 | Revisão completa |
| DataHunter | ⚠️ 22/22, integração superestimada | 0 (só template) | experimental e desconectado | Reenquadrar e formalizar decisões |
| Hydra | ❌ sem CONOPS completo | 0 | dono de ACO-ADR-0005/0009 | Criar estrutura e CONOPS |
| Forge | ❌ sem CONOPS completo | 0 | dono de ACO-ADR-0008 | Criar estrutura e CONOPS |

## Checklist padrão — seis tarefas por projeto

### Tarefa 0 — Conformidade com a arquitetura transversal

- [ ] Usa o **ACO Interop Envelope** (ACO-ADR-0004) em comunicação cross-component ou declara por que ainda não se aplica.
- [ ] Propaga identidade via **ACO Identity Context** (ACO-ADR-0006), inclusive `delegation_chain` quando aplicável.
- [ ] Se classifica tarefas ou agentes, usa ACO-ADR-0002 e ACO-ADR-0015.
- [ ] Políticas críticas não são autoalteráveis pelo agente governado (ACO-ADR-0013).
- [ ] Autoevolução produtiva utiliza rollout progressivo e regressão contínua (ACO-ADR-0010).
- [ ] Exportação de evidência segue o contrato mínimo do Hydra (ACO-ADR-0005).
- [ ] Nenhuma decisão local contradiz ADR transversal ratificado sem aplicar ACO-ADR-0003.

### Tarefa 1 — Consistência do README

- [ ] Nome, sigla, camada e papel canônicos.
- [ ] Status atualizado.
- [ ] Link para a arquitetura normativa e ADRs aplicáveis.
- [ ] Identificadores de ADR com namespace.

### Tarefa 2 — Alinhamento CONOPS ↔ visão da organização

- [ ] Visão e motivação refletem a limitação resolvida pelo componente.
- [ ] Papel e fronteiras batem com a camada declarada.
- [ ] Vocabulário ACO consistente.
- [ ] Estado atual não é confundido com arquitetura-alvo.

### Tarefa 3 — Profundidade item a item

- [ ] Todos os 22 itens presentes ou ausência justificada.
- [ ] Profundidade proporcional ao baseline NEXUS.
- [ ] Subitens e cenários operacionais suficientes.

### Tarefa 4 — Leitura integral

- [ ] Estrutura lógica e sem contradições.
- [ ] Escopo e maturidade consistentes.
- [ ] Links para ADRs, SRS, SSDD e sprints válidos.
- [ ] Questões abertas citam ADR existente ou ADR a criar.

### Tarefa 5 — Evidência de implementação e conformidade

- [ ] Cada ADR aplicável possui estado: Ratificado, Implementado e Conformidade verificada.
- [ ] Implementação possui link para código, configuração, schema, release ou procedimento.
- [ ] Conformidade possui teste de contrato, revisão, auditoria ou evidência do Hydra.
- [ ] A matriz em `docs/03-arquitetura/README.md` foi atualizada.
- [ ] Declarações sem evidência usam `A verificar`, nunca `Conforme`.

## Tarefas específicas por projeto

### 1. ARGO (`argo-agent-platform`)

- [ ] completar as seções equivalentes a **Requisitos Operacionais por Camada** e **Handoff para Curadoria Humana e Revisão Operacional**;
- [ ] verificar se o policy engine cumpre ACO-ADR-0013;
- [ ] reconciliar a classificação local com ACO-ADR-0002 e ACO-ADR-0015;
- [ ] definir como o ARGO produz e atualiza o Agentic Workstream conforme ACO-ADR-0014;
- [ ] propagar ACO Identity Context e `delegation_chain` em ações de agentes;
- [ ] vincular testes ou evidências de conformidade.

### 2. DIR (`dir-dynamic-inference-routing`)

- [ ] adotar identificadores canônicos `DIR-ADR-NNNN` nas referências;
- [ ] migrar gradualmente arquivos `adr-00X-*` para o padrão definido, sem quebrar links;
- [ ] reconciliar scoring e classificação com ACO-ADR-0002/0015;
- [ ] confirmar que validation/fallback policies cumprem ACO-ADR-0013;
- [ ] documentar ACO Interop Envelope e ACO Identity Context na borda;
- [ ] manter separação explícita: DIR decide, OR executa a rota.

### 3. OR-OmniRouter (`or-omni-router`)

- [ ] substituir "Ecossistema AIT" por ACO;
- [ ] aprofundar a seção de handoff;
- [ ] incorporar ACO-ADR-0004 no gateway de entrada e saída;
- [ ] incorporar ACO-ADR-0006 para identidade, tenant e delegação;
- [ ] mapear telemetria de execução ao contrato de exportação do Hydra;
- [ ] registrar testes de compatibilidade de envelope, falha fechada e correlação por `trace_id`.

### 4. DataHunter

O código é experimental e atualmente desconectado da ACO. O CONOPS superestima a maturidade e descreve integração com o nome antigo PKGL como se fosse corrente.

- [ ] substituir PKGL por NEXUS apenas nas integrações futuras planejadas;
- [ ] reenquadrar o projeto como standalone/experimental no estado atual;
- [ ] mover integração NEXUS para roadmap;
- [ ] corrigir "AIT Standard" e nomes antigos da organização;
- [ ] formalizar ADRs retroativas quando houver decisão estável;
- [ ] não declarar conformidade cross-component antes de existir integração e teste.

### 5. Hydra

- [ ] criar estrutura `docs/` e CONOPS completo;
- [ ] usar ACO-ADR-0005 e ACO-ADR-0009 como requisitos fundadores;
- [ ] documentar pipeline Evento → Coleta → Correlação → Análise → Indicadores → Ação;
- [ ] definir ingestão, correlação, avaliação, rollback e retenção de evidências;
- [ ] implementar a própria capacidade de verificar conformidade dos demais componentes;
- [ ] publicar contratos, schemas e testes de exportação.

### 6. Forge

- [ ] criar estrutura `docs/` e CONOPS completo;
- [ ] usar ACO-ADR-0008 como requisito fundador;
- [ ] formalizar contrato de publicação e lifecycle de artefatos executáveis;
- [ ] incorporar envelope, identidade e rollout progressivo;
- [ ] vincular publicação, promoção, depreciação e rollback a evidências do Hydra;
- [ ] publicar schemas e testes de contrato.

## Ordem sugerida de execução

1. **Hydra e Forge** — criar documentação e contratos fundadores.
2. **ARGO** — policy engine, taxonomia, identidade e workstream.
3. **OR-OmniRouter** — envelope, identidade e telemetria.
4. **DIR** — políticas, taxonomia e nomenclatura.
5. **DataHunter** — reenquadramento experimental e roadmap NEXUS.
6. **NEXUS e Horizon** — consolidar evidências da adoção já parcialmente documentada.

## Horizon — pendências concretas

- [ ] **HORIZON-ADR-0003** — reconciliar HIP com ACO Interop Envelope.
- [ ] **HORIZON-ADR-0004** — habilitar exportação opcional de sinais agregados para Hydra.
- [ ] **HORIZON-ADR-0006** — mapear `tokens_avoided` e `cost_estimate` ao contrato Hydra.
- [ ] **HORIZON-ADR-0012** — preencher decisão de identidade e tradução para `aco_identity_context`.
- [ ] **HORIZON-ADR-0014** — definir alimentação do Hydra pelos traces técnicos.

## Fora de escopo imediato

- renomeação física em massa de todos os ADRs existentes;
- declaração de conformidade sem evidência técnica;
- integração produtiva do DataHunter antes do reenquadramento do CONOPS.

---

*Gerado a partir de análise comparativa dos oito repositórios. Atualizado em 2026-07-12 com namespaces canônicos, estados de adoção, matriz ADR → componente → implementação e backlog de conformidade.*