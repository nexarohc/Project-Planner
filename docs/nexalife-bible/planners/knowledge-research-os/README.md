# Knowledge, Research & Personal Intelligence Operating System (KROS)

The layer that lets NexaLife research a question, judge the evidence, and remember the conclusion along with the reasoning that produced it. Written as the `NLB-KROS-*` series per `NLB-00` Article VII, occupying Volume 31.

Home domains: **LD-02 Education** and **LD-16 Science & Research** (`NLB-03`). Catalogue anchors PU-02-023–031 and PU-16-001–013 (`NLB-04`).

| Part | Title | Document |
| --- | --- | --- |
| 1 | Personal Knowledge Base, Research Engine, Verification & Decision Memory | [NLB-KROS-001](./NLB-KROS-001-personal-knowledge-research-engine-and-decision-memory.md) |
| 2 | Research Agents, Knowledge Synthesis, Professional Learning & Intelligence Safety | [NLB-KROS-002](./NLB-KROS-002-research-agents-synthesis-and-intelligence-safety.md) |
| 3 | Knowledge Workspace, Personal Encyclopedia, Research Studio & Knowledge-to-Execution | [NLB-KROS-003](./NLB-KROS-003-knowledge-workspace-research-studio-and-knowledge-to-execution.md) |
| 4 | Knowledge Automation, Agentic Research Pipelines, Organizational Intelligence & Knowledge Security | [NLB-KROS-004](./NLB-KROS-004-knowledge-automation-agentic-pipelines-organizational-intelligence-and-security.md) |
| 5 | Cognitive Workspace, Reasoning Tools, Knowledge Governance & The Research Command Center | [NLB-KROS-005](./NLB-KROS-005-cognitive-workspace-reasoning-tools-governance-and-research-command-center.md) |
| 6 | Temporal Knowledge, Context Assembly, Answer Modes & Multi-Model Verification | [NLB-KROS-006](./NLB-KROS-006-temporal-knowledge-context-assembly-and-multi-model-verification.md) |
| 7 | Personal Intelligence, Predictive Analysis, Decision Quality & Belief Tracking | [NLB-KROS-007](./NLB-KROS-007-personal-intelligence-predictive-analysis-decision-quality-and-belief-tracking.md) |
| 8 | Multimodal Understanding, Knowledge Lineage & Personalization Boundaries | [NLB-KROS-008](./NLB-KROS-008-multimodal-understanding-knowledge-lineage-and-personalization-boundaries.md) |
| 9 | Context Hierarchy, Scoped Instructions, Context Snapshots & The Personal Context API | [NLB-KROS-009](./NLB-KROS-009-context-hierarchy-snapshots-and-the-personal-context-api.md) |
| 10 | Project, Goal, Decision & Risk Intelligence | [NLB-KROS-010](./NLB-KROS-010-project-goal-decision-and-risk-intelligence.md) |

## What this series owns — and what it doesn't

KROS's contribution is **research methodology**: how sources are ranked, how conflicts are surfaced, how a claim is verified, when to stop researching, and how a conclusion is remembered.

| Deferred to | Which owns |
| --- | --- |
| `NLB-NXOS-005` | The Universal Knowledge Graph. KROS contributes Research and Decision nodes; it does not build a second graph. |
| `NLB-NXOS-003` | The memory system — kinds, ranking, compression, forgetting. KROS adds research-specific decay rules only. |
| `NLB-NXOS-002` | Confidence scoring and evidence tracking as platform mechanisms. KROS applies them to external sources. |
| `NLB-SP-002`/`003`/`005` | Learning mechanics for students — spaced repetition, active recall, mastery models, prerequisite graphs, diagnostics, adaptive difficulty, learning paths. Part 2 covers only what adult and professional learning adds on top. |
| `NLB-CPIOS-001` · `NLB-08` | Communication search and Global Search. KROS federates both rather than duplicating either. |
| `NLB-NIC-002` · `NLB-NIC-003` | The action lifecycle and the Autonomy Ladder; cross-device continuity and ambient assistance. Part 7 applies the ladder to knowledge work rather than defining a second one. |
| `NLB-21` | Goal decomposition, cross-planner priority and daily planning. Part 7 contributes the attention budget as an input. |

## Three load-bearing properties

1. **Epistemic status is explicit** — Fact, Interpretation, Assumption, User opinion, Unknown, Unverified, Conflicting, Outdated. Most systems collapse these into "information"; keeping them distinct is what lets a user act on a conclusion without inheriting hidden assumptions.
2. **Source deduplication before corroboration** — fifteen sites reprinting one press release are one source, not fifteen confirmations. Treating repetition as agreement is the most common way automated research manufactures false confidence.
3. **The agent output contract, with a non-empty Uncertainties field** — an agent that reports only findings hides its own limits. Every final report carries a "what we don't know" section for the same reason.

> **NexaLife should never confuse confidence with truth.**
