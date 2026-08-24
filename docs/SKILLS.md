# Ace Club — Backend Skills

## Purpose

This document tracks **demonstrated** backend engineering mastery.

It is not a self-esteem score and not a list of technologies used in
the repository.

A concept appearing in working code is not sufficient evidence of
mastery.

Codex should use this document when selecting learning tasks and
determining L0-L3 assistance levels.

---

# Mastery Scale

## 0 — Unknown

The developer does not yet have a usable model of the concept.

## 1 — Recognition

The developer recognizes the concept and basic terminology but cannot
reliably explain the mechanism.

## 2 — Explanation

The developer can explain the basic mechanism and reason through simple
examples.

## 3 — Guided Application

The developer can solve realistic problems with meaningful guidance.

## 4 — Independent Application

The developer can independently recognize when the concept applies,
design a reasonable solution, implement it, and debug it.

## 5 — Trade-off Reasoning

The developer can reason about unfamiliar cases, failure modes,
alternative approaches, and engineering trade-offs.

## Unassessed

There is not enough evidence yet.

Do not interpret `Unassessed` as zero knowledge.

---

# Mastery Update Rules

Do not increase mastery merely because:

- Codex generated working code;
- the developer copied an example;
- tests pass;
- the concept appears in the repository;
- the developer says they understand it.

Look for evidence.

### 0 → 1

The developer can recognize and roughly describe the concept.

### 1 → 2

The developer can explain the underlying mechanism using a new example.

### 2 → 3

The developer successfully applies the concept to a realistic task with
guidance.

### 3 → 4

The developer independently recognizes and solves a new realistic
problem involving the concept.

### 4 → 5

The developer can analyze unfamiliar variants, failure modes,
alternatives, and trade-offs.

Mastery may be lowered when repeated evidence shows that the current
rating is too high.

---

# Current Skills

## Go

| Skill | Level | Evidence |
|---|---|---|
| Basic syntax and types | Unassessed | |
| Structs and methods | Unassessed | |
| Pointers | Unassessed | |
| Slices and maps | Unassessed | |
| Interfaces | Unassessed | |
| Error handling | Unassessed | |
| Packages and visibility | Unassessed | |
| `context.Context` | Unassessed | |
| Resource lifecycle / `defer` | Unassessed | |

---

## HTTP

| Skill | Level | Evidence |
|---|---|---|
| Request/response lifecycle | Unassessed | |
| HTTP methods | Unassessed | |
| Status semantics | Unassessed | |
| JSON request/response handling | Unassessed | |
| Routing and parameters | Unassessed | |
| Validation | Unassessed | |
| API error semantics | Unassessed | |
| Idempotency | Unassessed | |

---

## SQL / PostgreSQL

| Skill | Level | Evidence |
|---|---|---|
| Basic SQL | Unassessed | |
| Relational modeling | Unassessed | |
| Constraints | Unassessed | |
| Joins | Unassessed | |
| PostgreSQL integration from Go | Unassessed | |
| Connection pools | Unassessed | |
| Migrations | Unassessed | |
| Transactions | Unassessed | |
| Locking | Unassessed | |
| MVCC | Unassessed | |
| Isolation levels | Unassessed | |
| Indexes/query planning | Unassessed | |

---

## Concurrency

| Skill | Level | Evidence |
|---|---|---|
| Goroutines | Unassessed | |
| Data races | Unassessed | |
| Mutexes | Unassessed | |
| Channels | Unassessed | |
| Go memory model basics | Unassessed | |
| Cancellation | Unassessed | |
| Bounded concurrency | Unassessed | |
| Database concurrency | Unassessed | |

---

## Testing

| Skill | Level | Evidence |
|---|---|---|
| Go unit tests | Unassessed | |
| Table-driven tests | Unassessed | |
| HTTP tests | Unassessed | |
| PostgreSQL integration tests | Unassessed | |
| Failure-path testing | Unassessed | |
| Concurrency testing | Unassessed | |

---

## Architecture

| Skill | Level | Evidence |
|---|---|---|
| Separation of responsibilities | Unassessed | |
| Dependency direction | Unassessed | |
| Domain modeling | Unassessed | |
| Application boundaries | Unassessed | |
| Interface placement | Unassessed | |
| Transaction boundaries | Unassessed | |
| Modular monolith reasoning | Unassessed | |

---

## Operations

| Skill | Level | Evidence |
|---|---|---|
| Linux/process fundamentals | Unassessed | |
| Configuration | Unassessed | |
| Graceful shutdown | Unassessed | |
| Docker | Unassessed | |
| Logging | Unassessed | |
| Metrics | Unassessed | |
| Tracing | Unassessed | |
| Profiling | Unassessed | |

---

## Security

| Skill | Level | Evidence |
|---|---|---|
| Authentication concepts | Unassessed | |
| Authorization | Unassessed | |
| Password handling | Unassessed | |
| SQL injection prevention | Unassessed | |
| Secrets/configuration | Unassessed | |

---

# Evidence Format

Evidence should be concise and point to actual demonstrated behavior.

Good:

> 2026-XX-XX — independently modeled 404 vs infrastructure failure in
> Court lookup; explained why `sql.ErrNoRows` should not leak into HTTP.

Good:

> PR #12 — independently identified check-then-write race in training
> enrollment and proposed a transaction strategy.

Weak:

> Used transactions.

Weak:

> Read about context.

---

# Calibration

During early development many skills will remain `Unassessed`.

Codex should gradually assess them through normal project work rather
than conducting one giant examination.

When an important prerequisite is uncertain, Codex may ask a small
number of diagnostic questions or propose a micro-experiment.

Prefer evidence gathered through real development.