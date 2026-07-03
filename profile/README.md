<div align="center">
  <img src="./assets/aco-hero-banner.svg" alt="Arquitetura Operacional Cognitiva — Inferência, decisão, conhecimento, governança e operação como um sistema integrado" width="100%" />
</div>

<br/>

## Resumo executivo

A **1-AI-Ecosystem-Lab** desenvolve a **Arquitetura Operacional Cognitiva (ACO)**: uma infraestrutura que trata IA generativa como uma **operação governada e observável**, não como uma coleção de chamadas a modelos.

À medida que empresas migram de chats isolados para agentes e sistemas multiagentes, os problemas deixam de ser "qual modelo usar" e passam a ser **custo de inferência descontrolado, decisões não rastreáveis, conhecimento perdido entre sessões e ausência de governança sobre dados, privacidade e risco**. A ACO endereça isso com um conjunto de componentes modulares — hoje já em operação real, não apenas em design — que cobrem inferência, decisão, memória, execução multiagente e observabilidade de ponta a ponta.

Este README é a porta de entrada da arquitetura: o que já está rodando, como as peças se conectam, e por que o modelo de governança-como-infraestrutura é a próxima fronteira além de "só criar mais um agente".

<br/>

## Onde cada componente está hoje

| Componente | Camada | Papel em uma frase | Status |
|---|---|---|---|
| **Horizon** | Experience | Interface única para chats, agentes, workflows e observabilidade | ![estável](https://img.shields.io/badge/estável-33C481?style=flat-square) |
| **ARGO** | Agent Platform | Plataforma multiagente governada com HITL configurável | ![ativo](https://img.shields.io/badge/ativo-2FD9E8?style=flat-square) |
| **NEXUS** | Cognitive Continuity | Memória e conhecimento com lifecycle e proveniência | ![ativo](https://img.shields.io/badge/ativo-2FD9E8?style=flat-square) |
| **OR-OmniRouter** | Inference Control | Inferência contínua com fallback entre tiers local / free / paid | ![beta](https://img.shields.io/badge/beta-F5A623?style=flat-square) |
| **DataHunter** | Data Discovery | Descoberta e curadoria agêntica de dados técnicos | ![beta](https://img.shields.io/badge/beta-F5A623?style=flat-square) |
| **Forge** | Capability OS | Publica, descobre e compõe qualquer elemento executável da ACO | ![em desenvolvimento](https://img.shields.io/badge/em%20desenvolvimento-5C6885?style=flat-square) |
| **DIR** | Cognitive Decision | Roteamento cognitivo dinâmico por custo, qualidade e risco | ![em desenvolvimento](https://img.shields.io/badge/em%20desenvolvimento-5C6885?style=flat-square) |
| **Hydra** | Operational Intelligence | Observabilidade, LLMOps, AgentOps, FinOps e auditoria | ![em desenvolvimento](https://img.shields.io/badge/em%20desenvolvimento-5C6885?style=flat-square) |

<br/>

## Por que isso existe

Usar IA não é apenas selecionar um modelo.

À medida que empresas e equipes passam de chats isolados para copilots, agentes e sistemas multiagentes, surgem novos desafios:

- fragmentação entre ferramentas, modelos e agentes;
- aumento de custo por uso inadequado de inferência;
- baixa rastreabilidade das decisões;
- conhecimento preso em conversas e plataformas;
- dificuldade de governar privacidade, soberania, qualidade e risco;
- ausência de observabilidade cognitiva ponta a ponta.

A proposta da Arquitetura Operacional Cognitiva é tratar IA como uma **infraestrutura operacional governada**, e não apenas como uma coleção de APIs.

A arquitetura combina:

- inferência contínua;
- decisão cognitiva dinâmica;
- execução multiagente governada;
- memória e conhecimento com lifecycle;
- observabilidade, auditoria e FinOps;
- governança transversal.

> **Princípio central**
> `Uso da IA Generativa = inferência + decisão + conhecimento + governança + operação`

<br/>

## Conceitos fundamentais

| Conceito | Papel |
|---|---|
| **Modelo** | Capacidade técnica: coding, reasoning, long-context, vision, tool calling, baixa latência, baixo custo ou privacidade local. |
| **Política** | Critério operacional: local-first, cost-first, quality-first, privacy-first, premium-only, dual-pass, audit-required ou low-latency. |
| **Agente / MAS** | Execução de um ou mais papéis cognitivos: planner, coder, reviewer, researcher, support ou orchestrator. |
| **Estado Cognitivo** | Condição atual da tarefa: simple, complex, sensitive, critical, uncertain, long-context, tool-use ou exploratory. |

Sistemas de IA maduros não apenas processam dados — eles precisam **capturar, validar, consolidar e distribuir conhecimento com rastreabilidade**:

| Camada | Papel |
|---|---|
| Dados | fatos |
| Informação | contexto |
| Conhecimento | padrões |
| Cognição | decisão |
| Governança Cognitiva | lifecycle + soberania |

<br/>

## Mapa do ecossistema

<div align="center">
  <img src="./assets/aco-architecture-map.svg" alt="Mapa da arquitetura operacional cognitiva: da camada de experiência até a inferência, com NEXUS e DataHunter como camadas satélite e Hydra observando todos os componentes" width="100%" />
</div>

| Camada | Projeto | Papel | Status |
|---|---|---|---|
| Experience Layer | Horizon | Hub de experiência cognitiva para chats, agentes, workflows, conhecimento e observabilidade | estável |
| Agent Platform Layer | ARGO | Plataforma multiagente governada com HITL configurável, compilador declarativo e avaliação contínua por projeto | ativo |
| Capability OS Layer | Forge | OS de capacidades — publica, descobre, governa e compõe qualquer elemento executável da ACO | em desenvolvimento |
| Cognitive Decision Layer | DIR | Motor de roteamento cognitivo dinâmico com scoring multiobjetivo de custo, qualidade e risco | em desenvolvimento |
| Inference Control Layer | OR-OmniRouter | Camada de inferência contínua com fallback entre tiers local, free cloud e paid | beta |
| Data Discovery Layer | DataHunter | Agente de descoberta e curadoria de dados técnicos com scoring de autoridade e proveniência | beta |
| Cognitive Continuity Layer | NEXUS | Infraestrutura de continuidade cognitiva: Cognitive Objects, Fabrics, lifecycle, proveniência e distribuição cross-agent | ativo |
| Operational Intelligence Layer | Hydra | Observabilidade cognitiva, LLMOps, AgentOps, FinOps, auditoria, drift e qualidade | em desenvolvimento |

**Por onde começar**

| Objetivo | Projeto |
|---|---|
| Consumir LLMs com resiliência e fallback automático | OR-OmniRouter |
| Criar e operar agentes com supervisão humana | ARGO |
| Descobrir datasets e evidências técnicas | DataHunter |
| Ter uma interface para conversar com qualquer LLM | Horizon |
| Preservar conhecimento entre sessões e agentes | NEXUS |

<br/>

## Ciclo cognitivo operacional

Esse ciclo conecta uso, decisão, ação, observação e aprendizado contínuo — cada interação alimenta o próximo ciclo.

<div align="center">
  <img src="./assets/aco-cognitive-cycle.svg" alt="Ciclo cognitivo operacional: interação, inferência, decisão, ação, observação, aprendizado, consolidação e redistribuição em loop contínuo" width="100%" />
</div>

<br/>

## Como conversas viram conhecimento

<div align="center">
  <img src="./assets/aco-knowledge-pipeline.svg" alt="Pipeline de conhecimento: da conversa até a distribuição entre agentes, passando por captura, validação e consolidação" width="100%" />
</div>

<br/>

## Governança cognitiva transversal

A governança não é uma camada posterior. Ela atravessa todo o ecossistema.

| Domínio | Exemplos |
|---|---|
| Segurança | RBAC, segredos, menor privilégio, isolamento |
| Dados | LGPD, sensibilidade, retenção, soberania |
| Modelos | provedores autorizados, tiers, fallback permitido |
| Agentes | escopo, ferramentas, autonomia, HITL obrigatório |
| Conhecimento | proveniência, validade, conflito, decay |
| Custos | budget, quota, FinOps, paid fallback |
| Qualidade | evals, validação, grounding, regressão |
| Auditoria | ledger, rastreabilidade, logs, decisões |
| Operação | SLO, incidentes, runbooks, monitoramento |

<br/>

## Evolução da IA

```
LLMs → APIs → copilots → agents → multi-agent systems → cognitive infrastructure
```

A próxima fronteira não é apenas criar agentes. É operar **sistemas cognitivos governados, observáveis e economicamente sustentáveis**.

<br/>

## Direção estratégica

A 1-AI-Ecosystem-Lab explora a construção de uma arquitetura para:

- otimizar o uso de inferência;
- reduzir custo real de entrega;
- governar agentes e sistemas multiagentes;
- preservar conhecimento entre ferramentas e sessões;
- aplicar políticas de soberania, privacidade e qualidade;
- observar operações cognitivas ponta a ponta;
- criar sistemas progressivamente mais adaptativos.

> O futuro da IA não será definido apenas pelos modelos. Será definido pela capacidade de **operar cognição governada em escala**.
>
> **Arquitetura Operacional Cognitiva = Inferência + Decisão + Conhecimento + Governança + Operação**

<br/>

## Fale com a gente

Interessado em conhecer a arquitetura em mais detalhes, uma demonstração ou uma conversa técnica?

📧 `[seu e-mail aqui]` · 💼 `[link do LinkedIn aqui]`

