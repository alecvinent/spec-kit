---
description: Performs a Self-Reflective Inquiry (SRI) audit and gap analysis on the specification or technical plan.
globs: .specify/**/*.md
---

# Command: /speckit-sri (Self-Reflective Inquiry & Audit)

## Objective
Analyze the current specification (`spec.md`), the simulation results (`dream_report.md`), the technical plan (`plan.md`), or tasks (`tasks.md`) using the **Self-Reflective Inquiry (SRI)** framework. 

This command enforces **Principle VII: Self-Reflective Inquiry (SRI Protocol) & Anti-Vibe-Coding** of the Spec Kit Constitution. It **does NOT generate code**. Its sole purpose is to constructively critique current design artifacts, surface hidden assumptions, detect missing information (gaps), and verify strict alignment with the project constitution.

## Execution Steps

The AI agent must perform the audit in 3 sequential stages:

### Stage 1: Destructive Self-Critique
Critique the proposed specification or plan by answering:
- *What implicit assumptions am I making that are not explicitly stated in the spec?*
- *Is there over-engineering, unnecessary complexity, or violation of Principle V (Minimal Dependencies)?*
- *Are the mitigations proposed in `dream_report.md` properly addressed, or are they being ignored?*

### Stage 2: Gap & Ambiguity Identification
- List every missing detail, underspecified boundary, or missing data contract.
- Formulate targeted questions or explicit recommendations to resolve each gap. Remember **Rule A**: Never invent silent fallbacks for missing specifications.

### Stage 3: Constitutional Compliance Check
Verify whether the proposed changes strictly adhere to all core principles defined in `.specify/memory/constitution.md`, specifically checking for offline-first performance (Principle IV) and test-backed changes (Principle II).

## Output Structure

Generate the simulation results and save them strictly to **`.specify/sri_audit.md`** using the following Markdown structure:

```markdown
# 🔍 SRI Audit Report

## 1. Self-Critique Matrix
| Aspect Evaluated | Identified Gap / Risk | Uncertainty Level | Recommended Action / Clarification |
| :--- | :--- | :--- | :--- |
| **Architecture** | [e.g., Unclear token expiration behavior] | High | Define default TTL and refresh logic |
| **Data Modeling** | [e.g., Missing DB index for search query] | Medium | Add index on target field |
| **Edge Cases** | [e.g., No handling for third-party rate limits] | High | Define exponential backoff policy |

## 2. Fundamental Gaps
1. **[GAP-01]:** [Clear description of missing requirement or detail]
2. **[GAP-02]:** [Clear description of missing requirement or detail]

## 3. Constitutional Compliance Checklist
- [ ] **Principle II (Tests):** Are test requirements clearly defined for these changes?
- [ ] **Principle VI (Dreaming):** Was the dream simulation executed and reviewed?
- [ ] **Principle VII (SRI):** Have all implicit assumptions been exposed?

## 4. Verdict & Next Steps
- [ ] **Approved with Observations:** Proceed to `/speckit-plan` or `/speckit-tasks` after applying patches.
- [ ] **Alignment Required:** Open blocking questions ([GAP-XX]) must be resolved by the developer before proceeding.
