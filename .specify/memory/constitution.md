# Project Constitution

## Core Principles

### 1. Spec-Driven Development (SDD) First
All work MUST originate from an explicit requirement in `.specify/spec.md`. Code changes without a preceding specification or task in `.specify/tasks.md` are strictly prohibited.

### 2. Mandatory Pre-Plan Simulation (Dreaming Phase)
Before creating any technical architecture, plan, or set of tasks (`/speckit-plan` or `/speckit-tasks`), the agent MUST execute a **Dreaming Simulation Phase**.
- **Scenario Stress-Testing:** The agent must simulate potential edge cases, system bottlenecks, failure modes, race conditions, and non-obvious user journeys based on `spec.md`.
- **Exposing Hypotheses:** Generative assumptions or ambiguous specifications must be explicitly exposed as hypothetical scenarios in `.specify/dream_report.md` before finalizing architectural decisions.

### 3. Self-Reflective Inquiry (SRI Protocol)
Before writing or revising any artifact (`spec.md`, `plan.md`, or executable code via `/speckit-implement`), the agent MUST critique its own work and resolve gaps using the following checklist:
1. **Self-Critique & Gap Identification:** Expose implicit assumptions, missing boundaries, and technical failure risks.
2. **Inquiry Resolution:** Document gaps and resolve ambiguities in `.specify/sri_audit.md` before proceeding to task generation.

### 4. Anti-Vibe-Coding & Minimal Diffs
- No code shall be generated or altered without an explicit prior SRI trace recorded in the workflow or task description.
- Implementations must directly solve the task defined in `tasks.md` without adding unrequested "fluff" or secondary refactors outside the scope.

### 5. Artifact Traceability & Convergence
- All specifications, plans, tasks, and audits must persist in `.specify/` and be committed to the repository.
- Changes to logic must flow sequentially: `spec.md` → `dream_report.md` → `sri_audit.md` → `plan.md` → `tasks.md` → Code.
- Every development cycle must conclude with `/speckit-converge` to guarantee that code diffs perfectly match the specifications.

---

## SRI & Workflow Execution Matrix

When operating across Spec Kit skills, the agent must adhere to the following workflow extensions:

| Spec Kit Skill | Required Dream / SRI Action | Target Output Artifact |
| :--- | :--- | :--- |
| `/speckit-specify` | Run initial **Dream Simulation** to discover edge cases, security risks, and missing business logic. | `.specify/spec.md` |
| `/speckit-dream` | Perform deep simulation of load, network failures, data anomalies, and UX edge cases. | `.specify/dream_report.md` |
| `/speckit-sri` | Execute **SRI Critique** on `spec.md` and `dream_report.md`. Uncover hidden gaps and evaluate constitutional alignment. | `.specify/sri_audit.md` |
| `/speckit-plan` | Incorporate mitigations from `sri_audit.md` into technical architecture. Evaluate trade-offs before declaring design. | `.specify/plan.md` |
| `/speckit-tasks` | Validate that every task addresses at least one potential point of failure identified during the Dreaming/SRI phases. | `.specify/tasks.md` |
| `/speckit-implement` | Perform a rapid **Self-Reflective Review** prior to applying diffs. Ensure zero unreflected assumptions. | Source Code |
| `/speckit-converge` | Audit code against requirements to resolve drift and ensure full convergence. | Convergence Report |

---

## Quality Rules & Acceptance Criteria

- **Rule A (Explicit Gaps):** Never invent silent fallbacks for missing specifications. Expose the gap first in `sri_audit.md`, reflect on options, and document the chosen path.
- **Rule B (Traceable Rationale):** Architectural choices must include a "Failure Scenario Analysis" derived from the Dreaming report.
- **Rule C (Strict Alignment):** Any pull request or commit that violates these principles will be rejected during `/speckit-converge`.
