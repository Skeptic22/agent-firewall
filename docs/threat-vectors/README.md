# Sprint 1 Threat Vectors

Five attack scenarios the AI Agent Firewall should stop. Author: Temitope (The Breaker).

| ID | Title | Rules tested | Gap type |
|---|---|---|---|
| [THREAT-001](THREAT-001-read-then-exfiltrate.md) | Read a secret, then send it out | `RULE-ENV-002`, then `SINK-NET-001` | None expected for the basic case. Later tests may find session-state or coverage gaps. |
| [THREAT-002](THREAT-002-poisoned-readme.md) | Poisoned README | `RULE-ENV-002`, `SINK-NET-001`, `RULE-NET-005` | Coverage and design: which exact tool call does the hidden text trigger? |
| [THREAT-003](THREAT-003-poisoned-commit-or-issue.md) | Poisoned commit message or issue | `RULE-IPI-003`, `SINK-NET-001` | Coverage: the protected-file list may be too short. |
| [THREAT-004](THREAT-004-path-and-tool-name-tricks.md) | Path and tool-name tricks | `RULE-ENV-002`, `RULE-CRYPTO-001` | Tool-name, text-form and meaning gaps. All are potential gaps until Sprint 3. |
| [THREAT-005](THREAT-005-other-egress-and-url-tricks.md) | Other ways out, and URL tricks | `SINK-NET-001`, `SINK-EXEC-002`, `RULE-NET-005` | Coverage and text-form. |

## Honesty rule

These are paper tests. The repo loads and checks the policy but does not yet intercept tool calls, so nothing here is a confirmed bypass. Findings are written as "potential gap" or "the rule would not match". A bypass is only confirmed after it is reproduced against the real firewall in Sprint 3.

All examples use fake data (`API_KEY=fake-secret-123`) and `.example` domains.
