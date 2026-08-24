# Ace Club — Project Context

## 1. Product Overview

Ace Club is a web application for managing the activities and resources of a tennis club.

The system is intended to support:

- tennis courts;
- court reservations;
- tennis equipment;
- equipment reservations;
- coaches;
- training sessions;
- player enrollment in training sessions.

This repository is a **fresh implementation started from scratch**.

A previous attempt existed, but it is intentionally not treated as a foundation, reference architecture, compatibility target, or source of implementation decisions.

The new version should be designed from first principles.

---

## 2. Fresh-Start Principle

The current implementation must not preserve previous code, structure, abstractions, naming, database schema, or architectural choices merely because they existed before.

The previous attempt may be discussed only as retrospective learning material when that is useful.

Do not use the previous implementation as an answer key.

For every important decision in the new project, reason from:

1. current product requirements;
2. domain invariants;
3. technical constraints;
4. observed implementation pressure;
5. learning goals.

The new codebase should earn its architecture through current reasoning.

---

## 3. Users

The initial domain contains three primary user types.

### Club Administrator

Potential responsibilities:

- manage courts;
- manage equipment;
- manage coaches;
- manage training sessions;
- inspect reservations.

### Coach

Potential capabilities:

- view assigned training sessions;
- inspect participants;
- manage training-related information.

### Player

Potential capabilities:

- reserve courts;
- reserve equipment;
- enroll in training sessions;
- view reservations and training schedules.

These roles are hypotheses about the product domain and may evolve.

---

## 4. Core Domain Areas

### Courts

Physical tennis courts belonging to a club.

### Court Reservations

Time intervals during which a court is reserved.

Important future invariant:

> Two reservations for the same court must not overlap.

### Equipment

Tennis equipment available through the club.

The exact distinction between equipment types, stock quantities, and individually tracked equipment units has not yet been decided.

### Equipment Reservations

Reservations of equipment by players.

### Training

Training sessions conducted by coaches.

Potential concepts include:

- training programs;
- individual training sessions;
- capacity;
- enrollment;
- cancellation.

The exact model should be discovered during implementation.

### Users and Authorization

Authentication and authorization will be introduced when product behavior requires them.

They should not dominate the first development phase.

---

## 5. Technology

### Backend

- Go

Prefer the standard library where it is sufficient.

Third-party dependencies should solve a concrete current problem.

### Database

- PostgreSQL

PostgreSQL is part of the application architecture, not just storage.

Use database constraints, transactions, indexes, locking, and PostgreSQL-specific features when they provide clear correctness or performance benefits.

### Frontend

- Vue

Backend engineering is the primary learning focus, but the system is intended to become a complete web application.

---

## 6. Architecture Direction

Ace Club starts as a **modular monolith**.

This is a direction, not a predesigned internal package structure.

The backend begins as one deployable Go application backed by PostgreSQL.

Internal boundaries should emerge from actual vertical slices and domain responsibilities.

Do not introduce distributed architecture without a concrete reason.

Initial non-goals include:

- microservices;
- Kubernetes;
- Kafka/NATS/RabbitMQ;
- Redis;
- Elasticsearch;
- event sourcing;
- CQRS;
- service mesh;
- distributed databases.

These technologies may be studied later when Ace Club develops a problem that makes them relevant.

---

## 7. Engineering Philosophy

### Start from behavior

Prefer implementing small vertical slices of real behavior over building generic infrastructure first.

### Prefer simple designs

Use the simplest design that:

- preserves correctness;
- expresses the domain clearly;
- can be tested;
- supports reasonable future change.

### Architecture must have reasons

Every meaningful abstraction should answer:

> What concrete current problem does this solve?

### Correctness before convenience

Important invariants must remain valid under:

- concurrent requests;
- failures;
- retries;
- invalid input;
- partial operations where relevant.

### Database integrity matters

Application-level validation is not assumed sufficient when concurrent database transactions can violate persistent invariants.

---

## 8. Primary Learning Goal

Ace Club is both a product and a learning environment.

The primary educational goal is to develop strong backend engineering skills with Go and PostgreSQL.

Important topics include:

- idiomatic Go;
- HTTP semantics;
- API design;
- SQL and relational modeling;
- PostgreSQL constraints;
- transactions;
- concurrency;
- testing;
- architecture;
- observability;
- deployment;
- performance;
- distributed systems fundamentals.

---

## 9. Learning Principle

Project completion speed is secondary to developer understanding.

The preferred loop is:

Problem → Independent reasoning → Design → Implementation → Testing/Failure → Review → Correction → Explanation

rather than:

Problem → AI-generated solution → Integration

---

## 10. First Development Phase

The project begins from an empty implementation.

The first milestone should establish the smallest useful end-to-end backend behavior without prematurely designing later features.

The initial candidate vertical slice is:

### Court Registry

An administrator can:

- create a court;
- list courts;
- retrieve a court.

This slice should establish the path:

HTTP → application behavior → PostgreSQL → HTTP response

The exact internal architecture should emerge while implementing it.

---

## 11. Non-Goals

Ace Club is not intended to maximize the number of technologies used.

Do not introduce technology primarily for:

- portfolio keyword coverage;
- architectural fashion;
- imitation of large-scale systems;
- hypothetical scale;
- preservation of choices from the previous attempt.

Complexity must be earned by a current problem.
