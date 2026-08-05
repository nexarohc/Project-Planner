# Nexa Intelligence Core (NIC)

The model-agnostic architecture underneath Nexa: identity, memory, orchestration, and (in Part 2) action-taking. Where `NLB-06` (Universal AI Engine) defines the platform mechanism and `NLB-11` (Nexa AI Operating System) defines Nexa's user-facing behavior, NIC defines the internal architecture that keeps Nexa a single coherent companion regardless of which underlying AI models power any given task. It is written as its own numbered series, `NLB-NIC-*`, per `NLB-00` Article VII, and occupies a single reserved slot — Volume 22 — in the Bible's top-level roadmap.

## Parts

| Part | Title | Document | Status |
| --- | --- | --- | --- |
| 1 | Identity, Memory & Orchestration | [NLB-NIC-001](./NLB-NIC-001-identity-memory-and-orchestration.md) | Master Draft (v1.0) |
| 2 | Nexa Action Engine (NAE) — intelligent task execution & workflow automation | [NLB-NIC-002](./NLB-NIC-002-nexa-action-engine.md) | Master Draft (v1.0) |
| 3 | Nexa Everywhere (NE) — voice, desktop, mobile & ambient computing | [NLB-NIC-003](./NLB-NIC-003-nexa-everywhere.md) | Master Draft (v1.0) |
| 4 | Nexa Developer Platform & AI Ecosystem (NDPAE) — SDK, extensions, skills & developer platform | [NLB-NIC-004](./NLB-NIC-004-nexa-developer-platform-and-ai-ecosystem.md) | Master Draft (v1.0) |
| 5 | Nexa Operating System (NXOS) — the long-term AI operating layer coordinating every planner, agent, app, and device | — | Proposed, not yet drafted |

## How the parts relate to other volumes

Part 4 overlaps substantially with `NLB-13` (Marketplace & Extensibility Platform) by design — it is the AI-specific specialization of that volume's general asset/certification/publishing mechanics (AI Skills, the AI Tool Registry, multi-provider/MCP compatibility), not a competing definition. See Part 4's Purpose section for the exact division of responsibility. Parts 2 and 3 similarly specialize `NLB-09` (Automation), `NLB-12` (Integrations), and `NLB-21` (LOUPE) for, respectively, Nexa-initiated action-taking and cross-device presence.
