---
description: Simulates system behavior in production under extreme scenarios, edge cases, and failure modes (Dreaming Phase).
globs: .specify/**/*.md
---

# Command: /speckit-dream (System Simulation & Edge-Case Discovery)

## Objective
Execute an **analytical simulation (Dreaming Phase)** based on the current requirements (`spec.md`) or technical design (`plan.md`). 
This fulfills **Principle VI: Mandatory Pre-Plan Simulation** of the Spec Kit Constitution. The goal is to stress-test the system virtually prior to writing code, surfacing inconsistencies, architectural risks, and edge cases.

## Execution Steps

The AI agent must mentally simulate and evaluate the system across four main dimensions:

1. **Load & Concurrency Simulation:** Identify race conditions, deadlocks, and DB persistence bottlenecks under heavy simultaneous usage.
2. **Network & Dependency Failures:** Handle timeouts, 500 errors, corrupt payloads, retry/fallback policies, and ensure offline-first degradation is respected (Principle IV).
3. **Extreme & Anomalous Data:** Process oversized payloads, empty strings, null values, and malicious injection vectors safely.
4. **UX & State Failures:** Handle abrupt user disconnections, incomplete state processing, and unhandled UI error states.

## Output Structure

Generate the simulation results and save them strictly to **`.specify/dream_report.md`** using the following Markdown structure:

```markdown
# 🌙 Dream Simulation Report

## 1. Simulated Scenarios

### 🧪 Scenario 1: [Name of Scenario - e.g., Concurrency & Data Contention]
- **Simulated Context:** [Describe the setup and trigger]
- **Expected vs. Simulated Behavior:** [Analysis of what fails]
- **Risk Level:** [Low / Medium / High / Critical]
- **Suggested Mitigation:** [Actionable change required for spec.md or plan.md]

### 🧪 Scenario 2: [Name of Scenario - e.g., Integration Failure]
- **Simulated Context:** [Describe the setup and trigger]
- **Expected vs. Simulated Behavior:** [Analysis of what fails]
- **Risk Level:** [Low / Medium / High / Critical]
- **Suggested Mitigation:** [Actionable change required for spec.md or plan.md]

## 2. Impact Coverage Matrix

| Dimension | Simulated State | Identified Risk | Mitigation Strategy |
| :--- | :--- | :--- | :--- |
| **Performance** | [Stable / Degraded] | [Brief summary] | [e.g., Add timeout, caching, rate limiting] |
| **Security** | [Secure / Vulnerable] | [Brief summary] | [e.g., Add validation, RBAC rules] |
| **Resilience** | [Robust / Fragile] | [Brief summary] | [e.g., Define fallback or circuit breaker] |

## 3. Recommended Spec Updates

List explicit rules, constraints, or acceptance criteria that MUST be appended to `spec.md` to resolve these vulnerabilities:
1. **[NEW RULE]:** ...
2. **[NEW ACCEPTANCE CRITERIA]:** ...
