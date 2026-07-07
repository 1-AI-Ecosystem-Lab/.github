<div align="center">
  <img src="https://raw.githubusercontent.com/1-AI-Ecosystem-Lab/.github/main/profile/assets/aco-hero-banner.svg" alt="Arquitetura Cognitiva Operacional — Inferência, decisão, conhecimento, governança e operação como um sistema integrado" width="100%" />
</div>

<br/>

## Resumo executivo

A **1-AI-Ecosystem-Lab** desenvolve a **Arquitetura Cognitiva Operacional (ACO)**: uma infraestrutura que trata IA generativa como uma **operação governada e observável**, não como uma coleção de chamadas a modelos.

À medida que empresas migram de chats isolados para agentes e sistemas multiagentes, os problemas deixam de ser "qual modelo usar" e passam a ser **custo de inferência descontrolado, decisões não rastreáveis, conhecimento perdido entre sessões e ausência de governança sobre dados, privacidade e risco**.

A isso se soma um problema pouco discutido: **cada plataforma expõe suas próprias tools e protocolos** — function calling, MCP, plugins proprietários — criando uma integração fragmentada em vez de uma camada única de execução. E o mais crítico de todos: **o conhecimento gerado em cada conversa com um LLM se perde ao final da sessão**, em vez de virar um ativo que a organização acumula e reutiliza.

A ACO endereça isso com um conjunto de componentes modulares e independentes — hoje já em operação real, não apenas em design — que cobrem inferência, decisão, memória, execução multiagente e observabilidade de ponta a ponta. Cada componente pode ser adotado isoladamente e se acopla às principais stacks e vendors de IA do mercado: não é um pacote fechado que exige adoção completa, nem prende a organização a um único fornecedor.

Este README é a porta de entrada da arquitetura: o que já está rodando, como as peças se conectam, e por que o modelo de governança-como-infraestrutura é a próxima fronteira além de "só criar mais um agente".

<br/>

## A lacuna nas arquiteturas de raciocínio atuais

A ACO responde a sete limitações estruturais identificadas em arquiteturas de raciocínio atuais — cada componente do ecossistema, à exceção do Horizon (camada de experiência), existe para resolver exatamente uma delas.

| Limitação identificada | Como a ACO responde |
|---|---|
| **Agentes autônomos sem supervisão estruturada** — sistemas multiagentes executam sem trilha auditável de decisão nem mecanismo formal de intervenção humana | **ARGO** oferece HITL configurável, rastreabilidade e avaliação contínua por projeto e versão — agentes podem operar independentes em runtime, mas nunca perdem o vínculo de monitoramento e manutenção |
| **Capacidades fragmentadas e não reaproveitáveis** — cada equipe recria ferramentas e integrações do zero, sem um catálogo central | **Forge** publica, descobre, governa e compõe qualquer elemento executável da arquitetura, tornando capacidades reutilizáveis entre projetos e times |
| **Entrada não governada e seleção de modelo estática** — prompts ambíguos chegam sem refino a um modelo fixo, independente da tarefa | **DIR** refina prompts ambíguos sem custo antes do envio a um provedor oneroso, e seleciona o modelo mais adequado por conteúdo, criticidade, domínio e tipo de tarefa |
| **Excesso de uso e falta de controle sobre inferência** — cada decisão dispara nova chamada ao modelo, mesmo quando o custo poderia ser evitado | **OR-OmniRouter** controla consumo de tokens com fallback automático entre modelos (evitando interrupções por limite de uso) e otimiza o prompt de entrada por roteamento entre técnicas de redução |
| **Conhecimento externo não curado** — dados e evidências técnicas usados por agentes vêm de fontes não verificadas, sem proveniência | **DataHunter** descobre e cura dados técnicos com scoring de autoridade e proveniência antes de entrarem no ecossistema |
| **Aprendizado finito e sistema passivo** — o conhecimento gerado numa interação se perde ao final dela, e o sistema não evolui nem melhora decisões com o próprio uso | **NEXUS** trata conhecimento como objeto com lifecycle e proveniência, consolidando memória episódica em semântica, procedural e organizacional — e vai além do armazenamento: cria e publica novos artefatos para consumo ativo por agentes e humanos futuros |
| **Falta de governança e visibilidade sobre a abordagem neural dentro do raciocínio** — não é só "quem usou o quê", é como componentes neurais influenciam a decisão internamente | **Hydra** cobre observabilidade cognitiva, LLMOps, AgentOps, FinOps, auditoria, drift e qualidade — tornando essa influência rastreável e auditável, em vez de uma caixa-preta |
| **Acesso fragmentado e inteligência acoplada à interface** — a interação humana fica ilhada em chats locais, dificultando a omnicanalidade e a governança de contexto | O **Horizon** atua como Hub de Experiência centralizado (Thin Client), desacoplando a interface da orquestração e garantindo que humanos, sistemas e bots acessem as capacidades cognitivas sob regras unificadas |


### De IHM para IHIAM

O modelo clássico de **IHM — Interface Homem-Máquina** — pressupõe um humano operando uma máquina determinística: o comando é executado exatamente como dado, e nada do que acontece numa interação fica disponível para a próxima.

Em sistemas cognitivos, a IA deixa de ser apenas interface e passa a atuar como agente dentro do próprio processo de decisão. A ACO é desenhada para o paradigma **IHIAM — Interface Homem-IA-Máquina**: a IA participa ativamente da evolução do conhecimento e da tomada de decisão, não apenas media o comando do humano para a máquina.

<div align="center">
  <img src="https://raw.githubusercontent.com/1-AI-Ecosystem-Lab/.github/main/profile/assets/aco-ihm-ihiam.svg" alt="Comparação entre o modelo clássico IHM (Interface Homem-Máquina), com fluxo único e sem aprendizado, e o paradigma IHIAM da ACO, com a IA participando ativamente em um loop bidirecional de decisão e aprendizado" width="100%" />
</div>

**Mesma tarefa, dois paradigmas** — pedido: *"me manda o relatório de vendas"*

| | IHM | IHIAM (ACO) |
|---|---|---|
| 1 | Comando é enviado exatamente como escrito, ambíguo | DIR identifica a ambiguidade (falta período, região, formato) e refina o pedido — sem custo, antes de qualquer chamada ao provedor |
| 2 | Máquina executa o que entendeu, sem verificar | ARGO executa com o agente e modelo certos para a tarefa |
| 3 | Erro ou resultado incompleto só aparece no final | Resultado é observado, e a decisão fica registrada com contexto |
| 4 | Nada é reaproveitado — a próxima pessoa começa do zero | NEXUS consolida o padrão aprendido; o próximo pedido parecido é resolvido mais rápido e com mais precisão |

<br/>

## Onde cada componente está hoje

| Componente | Camada | Papel em uma frase | Status |
|---|---|---|---|
| **Horizon** | Experience | Interface única para chats, marketplace de agentes, workflows e observabilidade | ![estável](https://img.shields.io/badge/estável-1E9E64?style=flat-square) |
| **ARGO** | Agent Platform | Plataforma low-code para criar, publicar e operar agentes autônomos — independentes em runtime, mas monitorados e mantidos pelo ARGO | ![ativo](https://img.shields.io/badge/ativo-0E9AAE?style=flat-square) |
| **NEXUS** | Cognitive Continuity | Memória viva: consolida e publica conhecimento para agentes e humanos | ![ativo](https://img.shields.io/badge/ativo-0E9AAE?style=flat-square) |
| **OR-OmniRouter** | Inference Control | Inferência contínua com fallback entre tiers local / free / paid | ![beta](https://img.shields.io/badge/beta-C98A1D?style=flat-square) |
| **DataHunter** | Data Discovery | Descoberta e curadoria agêntica de dados técnicos | ![beta](https://img.shields.io/badge/beta-C98A1D?style=flat-square) |
| **Forge** | Capability OS | Publica, descobre e compõe qualquer elemento executável da ACO | ![em desenvolvimento](https://img.shields.io/badge/em%20desenvolvimento-5C6885?style=flat-square) |
| **DIR** | Cognitive Decision | Refina prompts e roteia para o modelo certo por custo, qualidade e risco | ![em desenvolvimento](https://img.shields.io/badge/em%20desenvolvimento-5C6885?style=flat-square) |
| **Hydra** | Operational Intelligence | Observabilidade, LLMOps, AgentOps, FinOps e auditoria | ![em desenvolvimento](https://img.shields.io/badge/em%20desenvolvimento-5C6885?style=flat-square) |

<br/>

## Conceitos fundamentais

O vocabulário abaixo é a base sobre a qual o **DIR** toma decisões de roteamento — cada tarefa é classificada por esses critérios antes de ser direcionada ao modelo e à política corretos.

| Conceito | Papel |
|---|---|
| **Modelo** | Capacidade técnica: coding, reasoning, long-context, vision, tool calling, baixa latência, baixo custo ou privacidade local. |
| **Política** | Critério operacional: local-first, cost-first, quality-first, privacy-first, premium-only, dual-pass, audit-required ou low-latency. |
| **Agente / MAS** | Execução de um ou mais papéis cognitivos: planner, coder, reviewer, researcher, support ou orchestrator. |
| **Estado Cognitivo** | Condição atual da tarefa: simple, complex, sensitive, critical, uncertain, long-context, tool-use ou exploratory. |

Esses critérios operam sobre uma cadeia maior, que atravessa toda a arquitetura — de fato bruto a decisão governada:

| Camada | Papel | Componente responsável |
|---|---|---|
| Dados | fatos | **DataHunter** |
| Informação | contexto | **Horizon** |
| Conhecimento | padrões | **NEXUS** |
| Cognição | decisão | **DIR** |
| Governança Cognitiva | lifecycle + soberania | **Hydra** |

<br/>

## Mapa do ecossistema

<div align="center">
  <img src="https://raw.githubusercontent.com/1-AI-Ecosystem-Lab/.github/main/profile/assets/aco-architecture-map.svg" alt="Mapa da arquitetura cognitiva operacional: da camada de experiência até a inferência, com NEXUS e DataHunter como camadas satélite e Hydra observando todos os componentes" width="100%" />
</div>

| Camada | Projeto | Papel | Status |
|---|---|---|---|
| Experience Layer | Horizon | Hub de experiência cognitiva para chats, marketplace de agentes, workflows, conhecimento e observabilidade | estável |
| Agent Platform Layer | ARGO | Plataforma low-code para criar, publicar e operar agentes autônomos com supervisão humana — independentes em runtime, mas monitorados e mantidos pelo ARGO | ativo |
| Capability OS Layer | Forge | OS de capacidades — publica, descobre, governa e compõe qualquer elemento executável da ACO | em desenvolvimento |
| Cognitive Decision Layer | DIR | Refina prompts ambíguos sem custo e roteia dinamicamente para o modelo certo por custo, qualidade e risco | em desenvolvimento |
| Inference Control Layer | OR-OmniRouter | Camada de inferência contínua com fallback entre tiers local, free cloud e paid | beta |
| Data Discovery Layer | DataHunter | Agente de descoberta e curadoria de dados técnicos com scoring de autoridade e proveniência | beta |
| Cognitive Continuity Layer | NEXUS | Memória viva: cria e publica conhecimento (semântico, procedural e organizacional) com lifecycle e proveniência, para consumo de agentes e humanos | ativo |
| Operational Intelligence Layer | Hydra | Observabilidade cognitiva, LLMOps, AgentOps, FinOps, auditoria, drift e qualidade | em desenvolvimento |

### Componentes independentes, adoção incremental

Cada componente da ACO opera de forma autônoma e agnóstica a stack — não exige a arquitetura completa para entregar valor, nem trava a organização a um único fornecedor de IA. **ARGO** e **Horizon** são os pontos de entrada mais comuns: um agente publicado no ARGO pode atuar de forma isolada, gerenciado exclusivamente pela plataforma; o Horizon pode ser adotado como interface de chat sozinho, sem nenhum outro componente por trás.

Quando conectados, os componentes se acoplam entre si e às principais stacks e vendors de IA do mercado: agentes do ARGO produzem Cognitive Objects que fluem ao NEXUS, o OR-OmniRouter fornece inferência resiliente entre múltiplos provedores, o Forge expõe capacidades a sistemas externos, e o Hydra coleta métricas e auditoria de ponta a ponta.

Na prática, a adoção pode começar pequena — um agente no ARGO, uma interface no Horizon — e crescer para a arquitetura completa sem reescrever nada.

### Por onde começar

| Objetivo | Projeto |
|---|---|
| Consumir LLMs com resiliência e fallback automático | OR-OmniRouter |
| Criar, publicar e operar agentes com supervisão humana | ARGO |
| Descobrir datasets e evidências técnicas | DataHunter |
| Ter uma interface para conversar com qualquer LLM | Horizon |
| Preservar conhecimento entre sessões, agentes e humanos | NEXUS |

<br/>

## Ciclo cognitivo operacional

Esse ciclo conecta uso, decisão, ação, observação e aprendizado contínuo — cada interação alimenta o próximo ciclo. Metade do loop é sustentada pelo **DIR** (decisão), a outra metade pelo **NEXUS** (aprendizado).

<div align="center">
  <img src="https://raw.githubusercontent.com/1-AI-Ecosystem-Lab/.github/main/profile/assets/aco-cognitive-cycle.svg" alt="Ciclo cognitivo operacional: interação, inferência, decisão, ação, observação, aprendizado, consolidação e redistribuição em loop contínuo" width="100%" />
</div>

<br/>

## Como conversas viram conhecimento

O pipeline abaixo é o mecanismo interno do **NEXUS** para transformar uma conversa em conhecimento reutilizável — da memória episódica de uma sessão até a memória semântica de toda a organização.

<div align="center">
  <img src="https://raw.githubusercontent.com/1-AI-Ecosystem-Lab/.github/main/profile/assets/aco-knowledge-pipeline.svg" alt="Pipeline de conhecimento: da conversa até a distribuição entre agentes, passando por captura, validação e consolidação" width="100%" />
</div>

<br/>

## Governança cognitiva transversal

A governança não é uma camada posterior. Ela atravessa todo o ecossistema — cada domínio abaixo é aplicado por um ou mais componentes específicos, não por uma camada única de compliance.

| Domínio | Exemplos | Componente |
|---|---|---|
| Segurança | RBAC, segredos, menor privilégio, isolamento | ARGO, Forge |
| Dados | LGPD, sensibilidade, retenção, soberania | DataHunter, NEXUS |
| Modelos | provedores autorizados, tiers, fallback permitido | OR-OmniRouter |
| Agentes | escopo, ferramentas, autonomia, HITL obrigatório | ARGO |
| Conhecimento | proveniência, validade, conflito, decay | NEXUS |
| Custos | budget, quota, FinOps, paid fallback | OR-OmniRouter, Hydra |
| Qualidade | evals, validação, grounding, regressão | Hydra |
| Auditoria | ledger, rastreabilidade, logs, decisões | Hydra |
| Operação | SLO, incidentes, runbooks, monitoramento | Hydra |

> ⚠️ As linhas **Segurança** e **Dados** ainda não foram confirmadas por você — os componentes listados são inferência minha com base no que já validamos em outras seções. Confirme ou ajuste antes de considerar essa tabela final (posso remover este aviso assim que confirmar).

<br/>

## Evolução da IA

```
LLMs → APIs → copilots → agents → multi-agent systems → cognitive infrastructure
```

A ACO se posiciona no último estágio dessa curva: não mais um agente isolado, mas a infraestrutura que os governa.

<br/>

## Direção estratégica

A 1-AI-Ecosystem-Lab constrói uma arquitetura para:

- otimizar o uso de inferência;
- reduzir custo real de entrega;
- governar agentes e sistemas multiagentes;
- preservar conhecimento entre ferramentas e sessões;
- aplicar políticas de soberania, privacidade e qualidade;
- observar operações cognitivas ponta a ponta;
- criar sistemas progressivamente mais adaptativos.

> O futuro da IA não será definido apenas pelos modelos. Será definido pela capacidade de **operar cognição governada em escala**.
>
> **Arquitetura Cognitiva Operacional = Inferência + Decisão + Conhecimento + Governança + Operação**

<br/>

## Fale com a gente

Interessado em conhecer a arquitetura em mais detalhes, uma demonstração ou uma conversa técnica?

📧 `[seu e-mail aqui]` · 💼 `[link do LinkedIn aqui]`
