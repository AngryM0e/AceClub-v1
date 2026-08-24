# ADR-0001: Start the New Implementation as a Modular Monolith

## Status

Accepted

## Context

Ace Club is being implemented again from scratch.

A previous attempt existed, but the new repository should not inherit its architecture by default.

The product is expected to contain several related domain areas:

- courts;
- reservations;
- equipment;
- training;
- users.

At the current stage:

- domain boundaries are still being discovered;
- expected load does not justify distributed architecture;
- independent deployment is not required;
- backend fundamentals are the primary learning focus.

Distributed architecture would introduce:

- network failure;
- deployment coordination;
- distributed tracing;
- cross-service consistency;
- message delivery;
- eventual consistency.

## Decision Drivers

The initial architecture should optimize for:

1. simplicity;
2. correctness;
3. rapid feedback;
4. clear domain modeling;
5. testability;
6. learning value;
7. ability to evolve.

## Considered Options

### Option A — Microservices

Advantages:

- independent deployment;
- potential independent scaling;
- explicit network boundaries.

Disadvantages:

- greater operational complexity;
- distributed failure modes;
- harder consistency;
- premature commitment to guessed boundaries.

### Option B — Modular Monolith

One deployable Go backend with internal boundaries introduced only when justified.

Advantages:

- simpler deployment;
- straightforward transactions;
- easier debugging;
- lower operational complexity;
- boundaries can emerge from real requirements.

Disadvantages:

- internal boundaries require discipline;
- poor package design can create coupling;
- future extraction may require restructuring.

## Decision

The fresh Ace Club implementation will begin as a modular monolith backed by PostgreSQL.

This decision does **not** prescribe a package structure.

Internal boundaries will be discovered through implementation.

## Rationale

A modular monolith avoids solving distributed-systems problems that Ace Club does not currently have.

It also creates a clean learning environment in which domain boundaries and architectural abstractions must be justified by actual code rather than inherited from the previous attempt.

## Consequences

### Positive

- low initial complexity;
- easier local development;
- easier end-to-end testing;
- simpler consistency;
- architecture can evolve from evidence.

### Negative

- discipline is required to preserve useful internal boundaries;
- later extraction may require deliberate work.

### Risks / Assumptions

This assumes Ace Club does not initially require independently deployable subsystems.

If evidence later contradicts that assumption, reconsider the decision.

## Verification

Periodically ask whether concrete operational or organizational problems exist that the monolithic deployment prevents us from solving reasonably.
