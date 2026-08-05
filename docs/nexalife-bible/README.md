# 📖 The NexaLife Bible

The authoritative specification for NexaLife — an AI-powered Life Operating System. Every volume follows the standards defined in `NLB-00` (document ID, version, status, revision history).

## Volumes

| Volume | Title | Document | Status |
| --- | --- | --- | --- |
| 00 | Master Constitution | [NLB-00](./NLB-00-master-constitution.md) | Master Draft (v1.1) |
| 01 | Product Vision & Strategy | [NLB-01](./NLB-01-product-vision-and-strategy.md) | Draft (v1.0) |
| 02 | Market Research & Competitor Analysis | [NLB-02](./NLB-02-market-research-and-competitor-analysis.md) | Master Draft (v1.0) |
| 03 | Universal Life Domain Architecture (ULDA) | [NLB-03](./NLB-03-universal-life-domain-architecture.md) | Master Draft (v1.1) |
| 04 | The Complete Domain & Planner Universe | [NLB-04](./NLB-04-domain-and-planner-universe.md) | Master Draft (v1.1) |
| 05 | Universal Planner Engine (UPE) | [NLB-05](./NLB-05-universal-planner-engine.md) | Master Draft (v1.0) |
| 06 | Universal AI Engine (UAE) | [NLB-06](./NLB-06-universal-ai-engine.md) | Master Draft (v1.0) |
| 07 | Universal Data Platform (UDP) | [NLB-07](./NLB-07-universal-data-platform.md) | Master Draft (v1.0) |
| 08 | Universal Experience Framework (UXF) | [NLB-08](./NLB-08-universal-experience-framework.md) | Master Draft (v1.0) |
| 09 | Automation & Workflow Engine (AWE) | [NLB-09](./NLB-09-automation-and-workflow-engine.md) | Master Draft (v1.0) |
| 10 | Identity, Organizations & Security Framework (IOSF) | [NLB-10](./NLB-10-identity-organizations-and-security-framework.md) | Master Draft (v1.0) |
| 11 | Nexa AI Operating System (NAOS) | [NLB-11](./NLB-11-nexa-ai-operating-system.md) | Master Draft (v1.0) |
| 12 | Integration & Connected Services Platform (ICSP) | [NLB-12](./NLB-12-integration-and-connected-services-platform.md) | Master Draft (v1.0) |
| 13 | Marketplace & Extensibility Platform (MEP) | [NLB-13](./NLB-13-marketplace-and-extensibility-platform.md) | Master Draft (v1.0) |
| 14 | Community, Competitions & Achievement Platform (CCAP) | [NLB-14](./NLB-14-community-competitions-and-achievement-platform.md) | Master Draft (v1.0) |
| 15 | Master Planner Specification Standard (MPSS) | [NLB-15](./NLB-15-master-planner-specification-standard.md) | Master Draft (v1.1) |
| 16 | Study Planner Bible (multi-part, series `NLB-SP-001`–`NLB-SP-008`) | [planners/study-planner/](./planners/study-planner/) | **Complete** (8 of 8 parts) |
| 17–20 | *(retired — see NLB-00 v1.5 note; not reassigned)* | — | Retired |
| 21 | Life Orchestrator & Universal Planning Engine (LOUPE) | [NLB-21](./NLB-21-life-orchestrator-and-universal-planning-engine.md) | Master Draft (v1.0) |
| 22 | Nexa Intelligence Core (NIC) (multi-part, series `NLB-NIC-001`+) | [nexa-intelligence-core/](./nexa-intelligence-core/) | In Progress (4 of ~5 parts) |
| 23 | NXOS — Nexa Operating Layer (multi-part, series `NLB-NXOS-001`+) | [nxos/](./nxos/) | In Progress (6 of ~6 parts) |
| 24 | User Personas | — | Planned |
| 25 | Product Requirements (PRD) | — | Planned |
| 26 | Analytics & Insight Layer | — | Planned |
| 27 | Platform Architecture & Infrastructure | — | Planned |

See `NLB-00` Article VIII for the full roadmap and the rationale behind the current ordering, and Article VII for documentation standards (ID scheme, versioning, status lifecycle, amendment process — including the `NLB-<XX>-NNN` scheme multi-part series use for their own parts).

### Multi-part series

Some volumes are big enough to need their own numbered series rather than a single document. Each still holds just one slot in the roadmap above; their parts are numbered independently under the `NLB-<XX>-NNN` scheme (NLB-00 Article VII).

| Series | Covers | Directory | Parts written |
| --- | --- | --- | --- |
| `NLB-SP-*` | The Study Planner — first planner spec'd under the MPSS (NLB-15) | [planners/study-planner/](./planners/study-planner/) | 001–008 (complete) |
| `NLB-NIC-*` | Nexa Intelligence Core — Nexa's model-agnostic identity, memory, orchestration, action-taking, cross-device presence, and developer platform | [nexa-intelligence-core/](./nexa-intelligence-core/) | 001 Identity/Memory/Orchestration, 002 Action Engine, 003 Nexa Everywhere, 004 Developer Platform & AI Ecosystem |
| `NLB-NXOS-*` | NXOS — the 20-year coordination-layer vision, and its four fabrics (Cognitive/Goal, Memory, Agent, Knowledge, Workflow) formalized in depth | [nxos/](./nxos/) | 001 Coordination Layer, 002 Cognitive Architecture, 003 Memory System, 004 AI Agent Ecosystem, 005 Knowledge Graph, 006 Hyper Automation |

Future planner bibles (Finance, Health, Business, and so on) will follow the same pattern under `docs/nexalife-bible/planners/<planner-name>/`, each with its own two-or-three-letter series code.

## Reading order

1. **Governance** — `NLB-00` (rules for the whole Bible)
2. **Strategy** — `NLB-01`, `NLB-02` (why NexaLife, and against what market)
3. **Structure** — `NLB-03`, `NLB-04` (the 17 Life Domains and the 503-entry planner catalogue)
4. **Shared engines** — `NLB-05` through `NLB-09` (the five platform layers every planner is built from: Planner, AI, Data, Experience, Automation)
5. **Trust & connectivity** — `NLB-10` (identity, organizations, security), `NLB-11` (Nexa's own behavior), `NLB-12` (external integrations)
6. **Growth & community** — `NLB-13` (Marketplace), `NLB-14` (Community, Competitions & Achievement)
7. **The authoring standard** — `NLB-15` (MPSS): the template every individual planner spec, starting with the Study Planner Bible at 16–23, must follow
8. **Everything after** — personas, requirements, analytics, and infrastructure, per the Volume 24–27 roadmap above

## Amending a volume

Follow `NLB-00` Article VII: bump the version (MAJOR for changes other volumes depend on, MINOR for additive/non-breaking changes), record the change in that volume's Revision History table, and update this index if the volume's status or title changes.
