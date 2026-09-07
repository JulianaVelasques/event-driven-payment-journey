# Architecture Overview

The architecture of the Event-Driven Payment Processing Platform will evolve incrementally as new requirements, scalability concerns and failure scenarios are introduced.

The initial architecture is intentionally simple and focuses on establishing a reliable transactional foundation before introducing distributed components.

## Current Architecture

### Version 1

```text
Client
  │
  ▼
Payment Service
  │
  ▼
PostgreSQL
```

## Main Components

### Payment Service

Responsible for:

* receiving payment requests;
* validating input;
* managing payment state;
* persisting payment data.

### PostgreSQL

Used as the primary transactional datastore for payment data.

## Current Communication

The initial version uses synchronous HTTP communication between the client and the Payment Service.

The Payment Service communicates directly with PostgreSQL for persistence.

## Future Evolution

As the project progresses, new requirements will introduce additional architectural components.

Potential future components include:

* Redis for idempotency, caching and rate limiting;
* Kafka for asynchronous event processing;
* Fraud Service;
* Ledger Service;
* Notification Service;
* Outbox Pattern;
* AWS managed services;
* Observability and resilience components.

These components should be introduced only when there is a concrete architectural problem or requirement that justifies them.

## Architecture Evolution

Architecture versions will be documented as the system evolves.

For each significant change, the project should capture:

* the problem that motivated the change;
* the alternatives considered;
* the decision;
* the trade-offs;
* the resulting architecture.

Related architectural decisions can be found in [`decisions/`](./decisions/).
