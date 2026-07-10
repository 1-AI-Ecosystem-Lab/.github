# RFC-0001 — Índice de referências acessíveis pela web

Este arquivo reúne as referências do documento `docs/rfc/RFC-0001-Governed-Self-Evolving-Agents.md` em formato operacional, com links públicos, tipo de fonte e observação de relevância para a Arquitetura Cognitiva Operacional (ACO).

> Objetivo: facilitar leitura, verificação, curadoria bibliográfica e futura manutenção da base de conhecimento arquitetural.

---

## 1. Artigos e preprints

### 1.1 ReAct

- **Referência curta:** YAO et al. (2023)
- **Título:** *ReAct: synergizing reasoning and acting in language models*
- **Tipo:** artigo / preprint
- **Link público:** https://arxiv.org/abs/2210.03629
- **Relevância para a ACO:** fundamenta a separação observável entre raciocínio, ação e observação no runtime de agentes. Influencia principalmente ARGO, DIR e Hydra.

### 1.2 Reflexion

- **Referência curta:** SHINN et al. (2023)
- **Título:** *Reflexion: language agents with verbal reinforcement learning*
- **Tipo:** artigo / preprint
- **Link público:** https://arxiv.org/abs/2303.11366
- **Relevância para a ACO:** fundamenta mecanismos de reflexão e aprendizagem verbal sem atualização de pesos. Influencia principalmente NEXUS, ARGO e Hydra.

### 1.3 Self-Refine

- **Referência curta:** MADAAN et al. (2023)
- **Título:** *Self-Refine: iterative refinement with self-feedback*
- **Tipo:** preprint
- **Link público:** https://arxiv.org/abs/2303.17651
- **Relevância para a ACO:** útil para ciclos locais de crítica e refinamento, especialmente em workflows cognitivos e decisões iterativas. Influencia ARGO e DIR.

### 1.4 Generative Agents

- **Referência curta:** PARK et al. (2023)
- **Título:** *Generative agents: interactive simulacra of human behavior*
- **Tipo:** artigo / conferência
- **Link público:** https://arxiv.org/abs/2304.03442
- **Relevância para a ACO:** importante para memória episódica, reflexão e planejamento de mais alto nível. Influencia especialmente NEXUS.

### 1.5 Voyager

- **Referência curta:** WANG et al. (2023)
- **Título:** *Voyager: an open-ended embodied agent with large language models*
- **Tipo:** preprint
- **Link público:** https://arxiv.org/abs/2305.16291
- **Relevância para a ACO:** central para o conceito de biblioteca de skills em crescimento, aprendizagem aberta e reutilização de capacidades. Influencia Forge, NEXUS, ARGO e Hydra.

### 1.6 Survey de agentes autoevolutivos

- **Referência curta:** GAO et al. (2025)
- **Título:** *A survey of self-evolving agents: on path to artificial super intelligence*
- **Tipo:** survey / preprint
- **Link público:** https://arxiv.org/abs/2507.21046
- **Relevância para a ACO:** fornece a moldura conceitual mais direta para a RFC-0001, especialmente na distinção entre o que evolui, quando evolui e como evolui.

---

## 2. Prioridade de leitura sugerida

### Prioridade alta

1. GAO et al. (2025) — survey de agentes autoevolutivos  
2. YAO et al. (2023) — ReAct  
3. SHINN et al. (2023) — Reflexion  
4. WANG et al. (2023) — Voyager

### Prioridade média

5. MADAAN et al. (2023) — Self-Refine  
6. PARK et al. (2023) — Generative Agents

---

## 3. Leitura por componente da ACO

| Componente | Referências mais úteis |
|---|---|
| **ARGO** | ReAct, Reflexion, Self-Refine, Voyager |
| **Forge** | Voyager, survey de agentes autoevolutivos |
| **NEXUS** | Reflexion, Generative Agents, Voyager |
| **DIR** | ReAct, Self-Refine, survey de agentes autoevolutivos |
| **Hydra** | ReAct, Reflexion, Voyager, survey de agentes autoevolutivos |
| **Horizon** | survey de agentes autoevolutivos |
| **DataHunter** | survey de agentes autoevolutivos |
| **OR-OmniRouter** | survey de agentes autoevolutivos |

---

## 4. Observações de curadoria

- Todos os links acima são públicos e acessíveis pela web.
- Neste momento, o repositório mantém **metadados bibliográficos e links**, não cópias locais dos PDFs.
- Caso a organização deseje, uma próxima etapa pode acrescentar:
  - arquivo BibTeX consolidado;
  - índice por tema;
  - classificação por evidência e maturidade;
  - DOI e venue final quando aplicável;
  - notas críticas por artigo.
