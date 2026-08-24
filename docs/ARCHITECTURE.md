# Ace Club — Architecture

## Purpose

This document describes architecture that **actually exists**.

It is descriptive, not aspirational.

The new Ace Club implementation starts from scratch. Previous architecture must not be copied into this document unless the new code independently arrives at the same structure.

---

# 1. Current System

Current implementation architecture:

```text
No application architecture has been committed yet.
```

Intended deployment direction:

```text
Browser
   │
   ▼
Vue Application
   │
   │ HTTP
   ▼
Go Backend
   │
   │ SQL
   ▼
PostgreSQL
```

The internal backend structure is intentionally undecided.

---

# 2. Fresh-Architecture Rule

Do not begin by recreating the previous implementation.

Do not assume the project needs:

- handlers/services/repositories;
- clean architecture layers;
- domain/application/infrastructure packages;
- interfaces for every dependency;
- generic base abstractions.

Any such boundary must be justified by current code and responsibilities.

If the new implementation independently converges on a familiar pattern, document why that pattern is useful here.

---

# 3. Architectural Principles

## 3.1 Vertical slices before generalized structure

Prefer completing a small end-to-end behavior before building a broad framework.

Use actual implementation pressure to discover useful abstractions.

## 3.2 Prefer explicit dependencies

Dependencies should be visible and understandable.

Avoid hidden global state and unnecessary implicit behavior.

## 3.3 Boundaries need responsibilities

For every proposed layer or abstraction, ask:

1. What responsibility does it own?
2. What responsibility does it prevent another component from owning?
3. What current problem does it solve?
4. What complexity does it add?

## 3.4 Preserve context propagation

Request-scoped work should propagate `context.Context` through blocking operations.

Conceptually:

```text
HTTP request context
        │
        ▼
application operation
        │
        ▼
database operation
```

## 3.5 Persistent invariants require concurrency reasoning

An application check before a database write does not automatically protect a persistent invariant.

Consider:

- concurrent transactions;
- database constraints;
- transaction boundaries;
- isolation;
- locking;
- retries.

---

# 4. Current Backend Structure

Not yet defined.

The first vertical slice should provide evidence for the initial structure.

Once actual structure exists, document:

- package responsibilities;
- dependency direction;
- important interfaces;
- transaction ownership;
- error propagation.

---

# 5. Data Architecture

Primary persistent storage:

**PostgreSQL**

Schema changes should use versioned migrations.

Important invariants should be represented with database capabilities when appropriate, including:

- `NOT NULL`;
- `UNIQUE`;
- foreign keys;
- `CHECK`;
- exclusion constraints;
- transactions.

---

# 6. HTTP Architecture

The backend will expose an HTTP API consumed by the Vue frontend.

Detailed API conventions should emerge from real endpoints.

When designing endpoints, consider:

- HTTP method semantics;
- resource identity;
- validation;
- expected vs unexpected failures;
- status codes;
- idempotency where relevant.

---

# 7. Error Model

Not yet finalized.

The first vertical slices should explicitly distinguish among concepts such as:

```text
malformed request
        ≠
invalid application operation
        ≠
resource not found
        ≠
conflict
        ≠
infrastructure failure
```

Do not expose raw database errors as API semantics.

---

# 8. Transactions

No transaction architecture has been established yet.

Transaction boundaries should be introduced only when a real consistency requirement requires them.

---

# 9. Testing Strategy

The testing strategy should evolve incrementally.

Likely categories:

### Unit Tests

For deterministic logic that is meaningful without infrastructure.

### Integration Tests

For behavior dependent on PostgreSQL.

### HTTP-Level Tests

For transport semantics and end-to-end vertical slices.

Avoid mocks merely to satisfy an architectural style.

Choose boundaries based on the behavior that needs confidence.

---

# 10. Deployment Architecture

Not yet designed.

Do not add deployment complexity before the application has useful behavior.

---

# 11. Architecture Evolution

When a concrete problem suggests a new component or abstraction, record:

1. the observed problem;
2. evidence that it exists;
3. candidate solutions;
4. trade-offs;
5. why the selected option is justified.

Create an ADR for significant durable decisions.
