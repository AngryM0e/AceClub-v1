# Ace Club — Development Workflow

## 1. Purpose

This document defines how changes are made to the fresh Ace Club implementation.

The project is intentionally restarting from zero.

The workflow must prevent the previous implementation from silently becoming the design template for the new one.

---

# 2. Source of Truth

The current GitHub repository is the source of truth for:

- current code;
- migrations;
- tests;
- documentation;
- Issues;
- Pull Requests;
- ADRs.

The previous implementation is historical material only.

ChatGPT is a reasoning and learning environment around the current repository.

---

# 3. Fresh-Start Rule

For every new task:

1. read the current requirement;
2. reason about the domain;
3. identify invariants and failure modes;
4. design the smallest useful solution;
5. implement it in the new codebase.

Do not ask:

> How did the old project do this?

Ask:

> What does the current problem require?

The old implementation may be reviewed later only for retrospective comparison.

---

# 4. Development Unit

Prefer small vertical slices.

Example:

```text
HTTP request
    ↓
application behavior
    ↓
database interaction
    ↓
HTTP response
```

Avoid building entire architectural layers before useful behavior exists.

---

# 5. Issue Workflow

Significant work should begin with a GitHub Issue.

Issues should describe:

- the problem;
- desired behavior;
- acceptance criteria;
- important constraints;
- learning focus.

Avoid encoding an unproven architecture into the issue.

---

# 6. Design Before Implementation

Before implementing a non-trivial feature, identify:

1. affected domain concepts;
2. invariants;
3. expected failure modes;
4. persistence implications;
5. concurrency implications where relevant;
6. API implications;
7. testing strategy.

For the first implementation of a concept, the developer should produce the initial design before AI proposes one.

---

# 7. Implementation

Prefer the smallest correct implementation.

Do not implement:

- speculative flexibility;
- abstractions copied from the previous attempt;
- generalized frameworks for one use case;
- unnecessary interfaces;
- premature optimization.

If a previous pattern is reintroduced, it must be justified by the new codebase.

---

# 8. Testing

Before considering a task complete, consider:

### Happy path

Does expected behavior work?

### Boundary cases

What happens at important boundaries?

### Invalid input

Are invalid states rejected appropriately?

### Failure cases

What happens when dependencies fail?

### Concurrency

Can concurrent operations violate an invariant?

### Persistence

Does PostgreSQL enforce the properties we rely on?

---

# 9. Self-Review

Before requesting review, ask:

- What assumptions did I make?
- What can fail?
- Which invariant does this code depend on?
- Could concurrent execution change the result?
- Are errors classified correctly?
- Are transaction boundaries correct?
- Did I recreate an old abstraction without proving that I still need it?
- Can simpler code solve the same problem?

---

# 10. Pull Request

Meaningful changes should normally go through a Pull Request.

A PR should explain:

- what changed;
- why;
- important design decisions;
- risks;
- testing;
- uncertainties.

---

# 11. Review Priority

Review approximately in this order:

1. correctness;
2. data integrity;
3. concurrency;
4. security;
5. failure handling;
6. API semantics;
7. architecture;
8. testing;
9. performance;
10. idiomatic Go;
11. readability/style.

---

# 12. After Review

For substantive findings:

1. understand the problem;
2. explain why it occurs;
3. propose a correction;
4. implement the correction;
5. verify it.

Do not mechanically apply patches without understanding them.

---

# 13. Merge Criteria

A change is ready to merge when:

- acceptance criteria are satisfied;
- important tests pass;
- review findings are addressed or deliberately accepted;
- the developer can explain the design;
- relevant documentation is updated.

---

# 14. Documentation Update

After meaningful changes, consider updating:

- `CURRENT_STATE.md`;
- `ARCHITECTURE.md`;
- an ADR;
- `LEARNING_LOG.md`;
- `PROJECT_CONTEXT.md` only when stable context changes.

---

# 15. Retrospective Use of the Previous Attempt

The previous implementation may be compared with the new one only after the developer has formed and preferably implemented the new solution.

Useful retrospective questions:

- What did the old implementation optimize for?
- What did the new implementation optimize for?
- Which old decisions were actually good?
- Which were accidental complexity?
- What would I now explain differently?

The old code should be used as a learning artifact, not a scaffold.
