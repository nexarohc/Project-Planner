# Communication & Personal Information Operating System (CPIOS)

The unified layer for email, messages, calls, contacts, notifications, attachments — and the personal-information vault they draw on. Written as the `NLB-CPIOS-*` series per `NLB-00` Article VII, occupying Volume 30.

Cross-cutting; anchors to **LD-01 Personal Life** (`NLB-03`).

| Part | Title | Document |
| --- | --- | --- |
| 1 | Unified Communications, Inbox Intelligence & Personal Information Flow | [NLB-CPIOS-001](./NLB-CPIOS-001-unified-communications-inbox-intelligence-and-information-flow.md) |
| 2 | Communication Agents, Automation Safety, Personal Data Vault & Digital Identity | [NLB-CPIOS-002](./NLB-CPIOS-002-communication-agents-personal-data-vault-and-identity.md) |

## Boundary against RSOS

`NLB-RSOS-002` owns communication **in service of relationships** — drafting to a friend, remembering what was discussed with a person, tracking commitments made to someone.

CPIOS owns communication **as a system** — the inbox as a queue to triage, rules that process it, safety checks before anything leaves, multi-account handling, and the personal-data vault. The split is *who it's about* (RSOS) versus *how the volume is managed* (CPIOS). Where they meet on a reply draft, RSOS supplies relationship context and CPIOS supplies send safety.

## Three load-bearing safety properties

1. **The pre-send check** — attachment, recipient, account, sensitive data, amounts/dates. Warnings the user can override; the value is the moment of attention.
2. **Rule simulation before execution** — a rule that quietly archives the wrong 200 messages is discovered too late by definition. Simulation moves that discovery earlier.
3. **Minimum necessary context, with visible exclusions** — context preview shows what is *not* being used, which is what makes the guarantee checkable.
