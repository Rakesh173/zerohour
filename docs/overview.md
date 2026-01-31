# Overview

ZeroHour is a **decision-layer CLI** for codebases.

It answers:
> What breaks the business first if this code fails?

---

## Problem

Static analysis tools:
- Produce too many findings
- Lack business or failure context
- Do not help with prioritization

Teams know what is wrong.
They do not know what to fix first.

---

## Approach

ZeroHour:
- Uses static, deterministic analysis
- Focuses on failure impact
- Forces prioritization (Top 5 only)

---

## Target Users

- Developers
- Security learners
- Code reviewers
- Hackathon judges (non-technical)

---

## Typical Use Case

1. Run ZeroHour on a codebase
2. See top failure-prone areas
3. Decide where to focus
4. Run SAST tools next

