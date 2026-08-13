# Autonomous Execution & Action Orchestration System (AEAOS)

The execution runtime — what happens between "approved" and "done", and how the system knows an action actually succeeded. Written as the `NLB-AEAOS-*` series per `NLB-00` Article VII, occupying Volume 32.

Cross-cutting; the runtime beneath every planner's actions.

| Part | Title | Document |
| --- | --- | --- |
| 1 | Execution Core, Task Orchestration & Action Integrity | [NLB-AEAOS-001](./NLB-AEAOS-001-execution-core-task-orchestration-and-action-integrity.md) |
| 2 | Multi-Agent Runtime, Delegation Limits & Agent Security | [NLB-AEAOS-002](./NLB-AEAOS-002-multi-agent-runtime-delegation-limits-and-agent-security.md) |
| 3 | Connectors, Web Automation, Device Control & Transaction Safety | [NLB-AEAOS-003](./NLB-AEAOS-003-connectors-web-automation-device-control-and-transaction-safety.md) |
| 4 | Event-Driven Execution, Proactive Operations & Automation Restraint | [NLB-AEAOS-004](./NLB-AEAOS-004-event-driven-execution-and-proactive-operations.md) |
| 5 | Authorization Binding, Uncertain State & Substitution Control | [NLB-AEAOS-005](./NLB-AEAOS-005-authorization-binding-uncertain-state-and-substitution-control.md) |
| 6 | Scheduling Execution, File Operations & Interface Targeting | [NLB-AEAOS-006](./NLB-AEAOS-006-scheduling-execution-file-operations-and-interface-targeting.md) |

## Boundary against NLB-NIC-002

`NLB-NIC-002` (the Nexa Action Engine) owns the **action model**: the lifecycle, action types, approval checkpoints, the Autonomy Ladder, and the Representation Boundary. AEAOS owns the **runtime beneath it** — idempotency, verification, partial state, limits, and the multi-agent population. The split is *what Nexa is permitted to do* (NIC-002) versus *how it is actually carried out and confirmed* (AEAOS).

Workflow mechanics remain with `NLB-09`, simulation and rollback with `NLB-CPIOS-002`, agent definition with `NLB-NXOS-004`, tool routing with `NLB-NIC-004`, and connectors with `NLB-12`.

## Three load-bearing properties

1. **Idempotency** — retry is the standard response to failure and network calls fail ambiguously by nature, so without it every recovery mechanism becomes a duplication mechanism.
2. **Verified completion** — "done" requires evidence. A false success is discovered when someone arrives at a hotel with no booking; a clean failure is recoverable in the moment.
3. **Approval is bound to specifics** — an approval that outlives its parameters has become a standing permission nobody granted.
4. **Delegation moves work, never permission** — an agent that could acquire authority by asking another agent has no authority boundary, only an unenforced convention.

> Only verified execution qualifies as completion.
