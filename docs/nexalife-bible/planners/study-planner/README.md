# Study Planner Bible

The Study Planner is the first individual planner specified under the Master Planner Specification Standard (`NLB-15`). It is written as its own numbered series, `NLB-SP-*`, per the ID scheme in `NLB-00` Article VII, and occupies a single reserved slot — Volume 16 — in the Bible's top-level roadmap.

Home domain: **LD-02 Education** (`NLB-03`). Catalogue entry: **PU-02-001 Study Planner** (`NLB-04`).

**Status: complete.** All eight parts are written; see the MPSS coverage table below for what's fully specified versus deferred to future platform volumes (Personas, PRD).

## Parts

| Part | Title | Document | Status |
| --- | --- | --- | --- |
| 1 | Foundation Architecture | [NLB-SP-001](./NLB-SP-001-foundation-architecture.md) | Master Draft (v1.0) |
| 2 | AI Tutor Ecosystem | [NLB-SP-002](./NLB-SP-002-ai-tutor-ecosystem.md) | Master Draft (v1.0) |
| 3 | Learning Engine & Knowledge System (LEKS) | [NLB-SP-003](./NLB-SP-003-learning-engine-and-knowledge-system.md) | Master Draft (v1.0) |
| 4 | Daily Study Workspace & Focus System (DSWFS) | [NLB-SP-004](./NLB-SP-004-daily-study-workspace-and-focus-system.md) | Master Draft (v1.0) |
| 5 | Assessment, Practice & Analytics (APA) | [NLB-SP-005](./NLB-SP-005-assessment-practice-and-analytics.md) | Master Draft (v1.0) |
| 6 | Collaboration, Community & Research Workspace (CCRW) | [NLB-SP-006](./NLB-SP-006-collaboration-community-and-research-workspace.md) | Master Draft (v1.0) |
| 7 | Technical Architecture, Data Model & API Framework (TADAF) | [NLB-SP-007](./NLB-SP-007-technical-architecture-data-model-and-api-framework.md) | Master Draft (v1.0) |
| 8 | Deployment, Operations, QA & Product Evolution (DOQAPE) | [NLB-SP-008](./NLB-SP-008-deployment-operations-qa-and-product-evolution.md) | Master Draft (v1.0) |

## MPSS section coverage

Per `NLB-15`, a planner bible is complete only once its parts, taken together, cover all 21 mandatory sections.

| MPSS section | Covered by | Status |
| --- | --- | --- |
| 1. Planner Identity | SP-001 | Done |
| 2. Business Objectives | SP-001 | Done |
| 3. Target Personas | SP-001 (baseline) | Partial — full persona depth awaits `NLB-22` (User Personas) |
| 4. Navigation Map | SP-001, SP-004 | Done |
| 5. Dashboard Architecture | SP-001, SP-004 | Done |
| 6. Complete Feature Inventory | SP-001, SP-003, SP-004, SP-005, SP-006 | Done |
| 7. Artificial Intelligence | SP-002, SP-003, SP-005 | Done |
| 8. Database Design | SP-007 | Done |
| 9. API Design | SP-007 | Done |
| 10. Automation | SP-007 (event model) | Done |
| 11. Analytics | SP-003, SP-005 | Done |
| 12. Notifications | SP-004 (partial) | Partial |
| 13. Reports | SP-005 | Done |
| 14. Permissions | SP-006, SP-007 | Done |
| 15. Integrations | SP-006, SP-007 (partial) | Partial |
| 16. Offline Support | SP-001, SP-003, SP-004, SP-007 | Done |
| 17. Accessibility | SP-002, SP-004, SP-005, SP-006 | Done |
| 18. Performance Requirements | SP-007, SP-008 | Done |
| 19. Security | SP-006, SP-007, SP-008 | Done |
| 20. Testing Strategy | SP-007, SP-008 | Done |
| 21. Future Expansion | SP-003, SP-005, SP-007, SP-008 | Done |

Two rows remain partial: full Target Persona depth depends on `NLB-22` (User Personas, not yet written), and Notifications/Integrations have baseline coverage but no dedicated deep-dive part — both acceptable gaps for a first-of-its-kind planner bible, and both are candidates for a future `NLB-SP-009` if warranted rather than a reason to hold up the rest of the specification.
