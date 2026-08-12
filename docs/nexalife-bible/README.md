# 📖 The NexaLife Bible

The authoritative specification for NexaLife — an AI-powered Life Operating System. Every volume follows the standards defined in `NLB-00` (document ID, version, status, revision history).

## Volumes

| Volume | Title | Document | Status |
| --- | --- | --- | --- |
| 00 | Master Constitution | [NLB-00](./NLB-00-master-constitution.md) | Master Draft (v1.14) |
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
| 24 | Health Operating System (HealthOS) | [planners/health-os/](./planners/health-os/) | **Complete** (6 parts) |
| 25 | Fitness & Performance OS (FPOS) | [planners/fitness-performance-os/](./planners/fitness-performance-os/) | **Complete** (3 parts) |
| 26 | BucketList & Experience OS (BLOS) | [planners/bucketlist-os/](./planners/bucketlist-os/) | **Complete** (2 parts) |
| 27 | Relationships & Social Life OS (RSOS) | [planners/relationships-social-os/](./planners/relationships-social-os/) | **Complete** (3 parts) |
| 28 | Finance, Wealth & Financial Freedom OS (FWOS) | [planners/finance-wealth-os/](./planners/finance-wealth-os/) | **Complete** (2 parts) |
| 29 | Career, Work & Professional Growth OS (CWOS) | [planners/career-work-os/](./planners/career-work-os/) | **Complete** (2 parts) |
| 30 | Communication & Personal Information OS (CPIOS) | [planners/communication-personal-info-os/](./planners/communication-personal-info-os/) | **Complete** (2 parts) |
| 31 | Knowledge, Research & Personal Intelligence OS (KROS) | [planners/knowledge-research-os/](./planners/knowledge-research-os/) | **Complete** (10 parts) |
| 32 | User Personas | — | Planned |
| 33 | Product Requirements (PRD) | — | Planned |
| 34 | Analytics & Insight Layer | — | Planned |
| 35 | Platform Architecture & Infrastructure | — | Planned |

See `NLB-00` Article VIII for the full roadmap and the rationale behind the current ordering, and Article VII for documentation standards (ID scheme, versioning, status lifecycle, amendment process — including the `NLB-<XX>-NNN` scheme multi-part series use for their own parts).

### Multi-part series

Some volumes are big enough to need their own numbered series rather than a single document. Each still holds just one slot in the roadmap above; their parts are numbered independently under the `NLB-<XX>-NNN` scheme (NLB-00 Article VII).

| Series | Covers | Directory | Parts written |
| --- | --- | --- | --- |
| `NLB-SP-*` | The Study Planner — first planner spec'd under the MPSS (NLB-15) | [planners/study-planner/](./planners/study-planner/) | 001–010 (complete) |
| `NLB-NIC-*` | Nexa Intelligence Core — Nexa's model-agnostic identity, memory, orchestration, action-taking, cross-device presence, and developer platform | [nexa-intelligence-core/](./nexa-intelligence-core/) | 001 Identity/Memory/Orchestration, 002 Action Engine, 003 Nexa Everywhere, 004 Developer Platform & AI Ecosystem |
| `NLB-NXOS-*` | NXOS — the 20-year coordination-layer vision, and its four fabrics (Cognitive/Goal, Memory, Agent, Knowledge, Workflow) formalized in depth | [nxos/](./nxos/) | 001 Coordination Layer, 002 Cognitive Architecture, 003 Memory System, 004 AI Agent Ecosystem, 005 Knowledge Graph, 006 Hyper Automation |
| `NLB-HOS-*` | HealthOS — whole-person health: medical organization, wellness, nutrition, sleep, mental wellbeing, healthcare ecosystem | [planners/health-os/](./planners/health-os/) | 001–006 (complete) |
| `NLB-FPOS-*` | Fitness & Performance OS — training, sport, and the IRL competition network | [planners/fitness-performance-os/](./planners/fitness-performance-os/) | 001–003 (complete) |
| `NLB-BLOS-*` | BucketList & Experience OS — dreams into planned, funded, booked, remembered experiences | [planners/bucketlist-os/](./planners/bucketlist-os/) | 001–002 (complete) |
| `NLB-RSOS-*` | Relationships & Social Life OS — People Graph, communication intelligence, communities, family coordination, life-memory | [planners/relationships-social-os/](./planners/relationships-social-os/) | 001–003 (complete) |
| `NLB-FWOS-*` | Finance, Wealth & Financial Freedom OS — cash flow, budgeting, debt, investing, business finance, wealth architecture | [planners/finance-wealth-os/](./planners/finance-wealth-os/) | 001–002 (complete) |
| `NLB-CWOS-*` | Career, Work & Professional Growth OS — career strategy, jobs, freelance, leadership, entrepreneurship | [planners/career-work-os/](./planners/career-work-os/) | 001–002 (complete) |
| `NLB-CPIOS-*` | Communication & Personal Information OS — unified inbox, agents, automation safety, personal data vault, digital identity | [planners/communication-personal-info-os/](./planners/communication-personal-info-os/) | 001–002 (complete) |
| `NLB-KROS-*` | Knowledge, Research & Personal Intelligence OS — research methodology, verification, knowledge workspace, agentic pipelines, security, reasoning tools | [planners/knowledge-research-os/](./planners/knowledge-research-os/) | 001–010 (complete) |

**Scope boundaries between planner bibles.** HealthOS owns whole-person wellbeing; FPOS owns training and competition (and is the sport-specific implementation of `NLB-14`'s competition framework, not a second one); BLOS is the full product specification of the Bucket List Platform capability `NLB-14` established; RSOS owns relationships and communication; FWOS owns money, and connects to BLOS so savings become experiences; CPIOS owns communication as a system where RSOS owns it as relationship context; KROS owns research methodology, deferring student learning mechanics to the Study Planner and the knowledge graph itself to NXOS. Each bible's README states its boundary explicitly.

Future planner bibles (Career, Business, Travel, and so on) will follow the same pattern under `docs/nexalife-bible/planners/<planner-name>/`, each with its own series code.

## Reading order

1. **Governance** — `NLB-00` (rules for the whole Bible)
2. **Strategy** — `NLB-01`, `NLB-02` (why NexaLife, and against what market)
3. **Structure** — `NLB-03`, `NLB-04` (the 17 Life Domains and the 503-entry planner catalogue)
4. **Shared engines** — `NLB-05` through `NLB-09` (the five platform layers every planner is built from: Planner, AI, Data, Experience, Automation)
5. **Trust & connectivity** — `NLB-10` (identity, organizations, security), `NLB-11` (Nexa's own behavior), `NLB-12` (external integrations)
6. **Growth & community** — `NLB-13` (Marketplace), `NLB-14` (Community, Competitions & Achievement)
7. **The authoring standard** — `NLB-15` (MPSS): the template every individual planner bible must follow
8. **Individual planner bibles** — Study Planner (16), HealthOS (24), FPOS (25), BLOS (26), RSOS (27), FWOS (28), each its own multi-part series
9. **Everything after** — personas, requirements, analytics, and infrastructure, per the Volume 32–35 roadmap above

## Amending a volume

Follow `NLB-00` Article VII: bump the version (MAJOR for changes other volumes depend on, MINOR for additive/non-breaking changes), record the change in that volume's Revision History table, and update this index if the volume's status or title changes.
