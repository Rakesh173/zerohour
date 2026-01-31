# ZeroHour – Execution Plan

This document defines **what to build, in what order, and why**.

Scope is intentionally constrained to ship a **working decision-layer CLI**.

---

## Goal (Non-Negotiable)

Ship a CLI that:

1. Analyzes a codebase statically
2. Identifies **failure-prone areas**
3. Outputs **only the top 3 issues**
4. Explains **business impact**, not vulnerabilities

Anything outside this is out of scope.

---

## Core Assumptions

- Static analysis only
- Deterministic logic
- Terminal-native output

---

## Phase 1 — Foundation (Must Work First)

### 1. CLI Skeleton
- `zerohour analyze` command
- Argument parsing (`-C`, `--no-box`)
- Exit codes
- Error handling

Deliverable:
- CLI runs reliably on a sample repo

---

### 2. File Scanner
- Traverse directory
- Filter analyzable files
- Ignore noise (node_modules, build output, etc.)

Deliverable:
- Consistent file list for analysis

---

## Phase 2 — Signal Extraction

### 3. Structural Signal Collection
Extract **structural signals only**:
- Entry points
- High fan-in logic
- Central orchestration files
- Dependency concentration

No semantic understanding.
No execution flow.

Deliverable:
- Raw signals per file/module

---

## Phase 3 — Failure Analysis

### 4. Failure Impact Heuristics
Apply deterministic rules to estimate:
- Failure propagation
- Blast radius
- Isolation vs coupling

Deliverable:
- Ranked internal list of risky areas

---

### 5. Forced Prioritization
- Sort by failure impact
- Drop everything except **Top 3**

This rule is strict.

Deliverable:
- Exactly 3 findings or fewer

---

## Phase 4 — Reporting

### 6. Explainable Output
For each finding:
- What can fail
- Why it matters
- What breaks
- Where to look in code

Formats:
- Boxed terminal output
- Plain text (`--no-box`)

Deliverable:
- Human-readable, decision-ready output

---

## Phase 5 — Validation

### 7. Sanity Testing
- Run against small sample projects
- Ensure output is:
  - Stable
  - Repeatable
  - Understandable without code knowledge

Deliverable:
- Confidence that results are explainable

---

## Explicitly Out of Scope

These will **not** be implemented in this phase:

- CVE detection
- Dependency vulnerability scanning
- Risk scores
- Severity numbers
- Dashboards
- Config files
- Language-specific deep parsing
- Runtime analysis

---

## Success Criteria

ZeroHour is considered successful if:

- It always outputs ≤ 5 issues
- Results are deterministic
- A non-technical reader understands *why* something matters
- A technical user knows *where* to look next

---

## Failure Conditions

The project fails if:
- It behaves like a SAST tool
- It outputs too many findings
- It requires explanation outside the tool
- It prioritizes quantity over decision clarity

---

## Notes

This plan optimizes for:
- Speed of development
- Clarity of purpose
- Honest scope

Anything that dilutes the **decision-layer** goal is rejected.

