# Ace Club — Backend Learning Plan

## Purpose

This document defines the backend engineering competency map for
Ace Club.

It is NOT a fixed chronological curriculum.

Codex should dynamically select learning tasks based on:

- current Ace Club functionality;
- demonstrated mastery;
- prerequisite dependencies;
- recent learning history;
- natural engineering problems created by the project.

The project should drive learning whenever possible.

---

# 1. Learning Strategy

Prefer:

project problem
→ required concept
→ reasoning
→ implementation
→ testing
→ review
→ understanding

over:

technology list
→ tutorial
→ artificial exercise

Use Ace Club features as the primary source of realistic learning
problems.

---

# 2. Target

The long-term goal is to reach approximately Level 4
(independent application) in the core backend competencies.

Level 5 is expected only for selected topics after substantial
experience.

See `SKILLS.md` for current demonstrated mastery.

---

# 3. Competency Areas

## A. Go Fundamentals

### Foundations

- variables and types
- functions
- structs
- methods
- pointers
- zero values
- packages
- visibility

### Collections and memory behavior

- arrays
- slices
- slice length/capacity
- backing arrays
- maps
- allocation basics

### Abstraction

- interfaces
- interface satisfaction
- typed nil
- composition
- dependency boundaries

### Error handling

- error values
- wrapping
- `errors.Is`
- `errors.As`
- sentinel errors
- typed errors
- error ownership

### Resource management

- `defer`
- cleanup
- lifecycle management

Target: Level 4

---

## B. Go Application Development

- project/package organization
- dependency direction
- configuration
- application startup
- dependency construction
- graceful shutdown
- context propagation

Target: Level 4

Prerequisites:

Go Fundamentals

---

## C. HTTP and API Engineering

### Foundations

- request/response lifecycle
- methods
- headers
- status codes
- JSON encoding/decoding
- routing
- path/query parameters

### API behavior

- validation
- resource identity
- error responses
- pagination
- filtering
- idempotency
- API contracts

### Later

- authentication
- authorization
- middleware
- timeouts
- cancellation

Target: Level 4

Prerequisites:

Go Fundamentals

---

## D. SQL and Relational Modeling

### SQL foundations

- SELECT
- INSERT
- UPDATE
- DELETE
- WHERE
- ORDER BY
- JOIN
- aggregation

### Relational modeling

- tables
- primary keys
- foreign keys
- nullability
- relationships
- normalization basics

### Integrity

- NOT NULL
- UNIQUE
- CHECK
- foreign-key constraints

Target: Level 4

---

## E. PostgreSQL Application Integration

- database connections
- connection pools
- query execution
- parameterized SQL
- scanning results
- no-row semantics
- database errors
- context-aware queries
- migrations

Target: Level 4

Prerequisites:

- Go Fundamentals
- SQL Foundations

---

## F. Transactions and Database Concurrency

Learning progression:

basic SQL
→ persistent invariants
→ transactions
→ concurrent transactions
→ locking
→ MVCC
→ isolation levels
→ advanced consistency strategies

Topics:

- atomicity
- transaction boundaries
- commit/rollback
- check-then-write races
- row locking
- MVCC
- isolation levels
- serialization failures
- deadlocks
- optimistic vs pessimistic approaches
- database constraints under concurrency

Target: Level 4

Prerequisites:

- SQL and Relational Modeling
- PostgreSQL Integration

Ace Club should naturally introduce these topics through:

- court reservations;
- training capacity;
- equipment availability.

---

## G. Go Concurrency

Learning progression:

goroutines
→ shared state
→ data races
→ synchronization
→ channels
→ cancellation
→ bounded concurrency
→ backpressure

Topics:

- goroutines
- race conditions
- Go memory model basics
- happens-before
- mutexes
- channels
- ownership
- worker patterns
- bounded concurrency
- goroutine leaks
- cancellation

Target: Level 4

Prerequisites:

Go Fundamentals

Do not introduce concurrency merely because Go supports it.

Prefer real project motivation.

---

## H. Testing

### Foundations

- Go testing package
- table-driven tests
- test cases and boundaries

### Backend testing

- HTTP tests
- integration tests
- PostgreSQL tests
- test database lifecycle
- deterministic tests

### Advanced

- concurrency tests
- race detector
- benchmarks
- failure-path testing

Target: Level 4

Testing should evolve alongside implementation rather than being
postponed to a separate learning phase.

---

## I. Backend Architecture

Learning progression:

responsibility
→ coupling
→ boundaries
→ dependency direction
→ application operations
→ transaction ownership
→ modularity

Topics:

- separation of concerns
- dependency direction
- domain modeling
- application boundaries
- infrastructure boundaries
- interface placement
- transaction ownership
- modular monolith design
- avoiding premature abstraction

Target: Level 4

Architecture should emerge from real code.

Do not teach architecture primarily through pattern memorization.

---

## J. Security

Introduce progressively when relevant.

Topics:

- password hashing
- authentication
- authorization
- session/token concepts
- input handling
- SQL injection
- secrets
- least privilege
- common web security concerns

Target: Level 3–4

Prerequisites:

- HTTP
- database integration

---

## K. Operations

Introduce after a useful backend exists.

Topics:

- environment configuration
- Linux process fundamentals
- signals
- graceful shutdown
- Docker
- health checks
- structured logging
- deployment fundamentals

Target: Level 3–4

---

## L. Observability and Performance

Topics:

- logging
- metrics
- tracing
- latency
- throughput
- benchmarking
- profiling
- PostgreSQL EXPLAIN
- indexes
- query performance
- connection pool behavior

Target: Level 3–4

Prerequisites:

A functioning backend with enough behavior to observe.

---

## M. Distributed Systems

Introduce only after strong foundations and a concrete project
motivation.

Topics:

- caching
- queues
- retries
- idempotency
- eventual consistency
- delivery semantics
- backpressure
- distributed failures
- service boundaries

Target: Level 2–3 initially.

Do not introduce these merely for technology exposure.

---

# 4. Important Dependency Paths

## Request Processing

Go fundamentals
→ HTTP
→ error handling
→ context propagation
→ database integration
→ complete vertical slices

## Persistent Correctness

SQL
→ constraints
→ transactions
→ concurrent transactions
→ locking/MVCC
→ isolation
→ reservation correctness

## Concurrency

Go fundamentals
→ goroutines
→ shared state
→ races
→ synchronization
→ cancellation
→ bounded concurrency

## Architecture

working vertical slices
→ repeated responsibilities
→ observed coupling
→ useful boundaries
→ modular architecture

## Production Readiness

working application
→ configuration
→ graceful shutdown
→ logging
→ Docker
→ metrics
→ tracing
→ profiling

---

# 5. Suggested Ace Club Progression

This is a direction, not a fixed backlog.

## Phase 1 — Foundation

Use Court Registry to learn:

- Go project basics;
- HTTP;
- PostgreSQL integration;
- errors;
- migrations;
- basic testing.

## Phase 2 — First Real Domain Invariants

Use Court Reservations to learn:

- time modeling;
- validation;
- relational modeling;
- constraints;
- transactions;
- database concurrency.

## Phase 3 — Richer Domain

Use Training and Enrollment to reinforce:

- relationships;
- capacity;
- transactions;
- concurrency;
- authorization.

## Phase 4 — Resources

Use Equipment to explore:

- inventory modeling;
- availability;
- transaction consistency.

## Phase 5 — Operational Backend

Introduce:

- configuration;
- graceful shutdown;
- Docker;
- logging;
- metrics;
- deployment.

## Phase 6 — Performance and Reliability

Introduce only against measurable behavior:

- indexes;
- profiling;
- connection pools;
- caching where justified;
- background processing where justified.

---

# 6. Selection Principle

The next learning topic should usually be:

> the smallest missing concept required to correctly implement the
> next useful Ace Club behavior.

Do not rush toward advanced topics.

Do not artificially delay project development just to follow a
technology curriculum.

Let product problems and prerequisite readiness meet in the middle.