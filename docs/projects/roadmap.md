# Roadmap

This roadmap describes the progressive development of the Event-Driven Payment Processing Platform.

The project follows a learning-by-building approach:

**Learn → Design → Implement → Test → Break → Review → Document**

The architecture should evolve incrementally. New technologies should be introduced when they solve a concrete problem rather than being added only for the sake of using them.

---

## Phase 0 — Setup

**Focus:** Development environment, project foundation and engineering workflow.

### Topics

* Java 21+
* Spring Boot
* Maven
* Git/GitHub
* Docker
* PostgreSQL
* JUnit
* Integration testing
* GitHub Actions
* Project documentation
* AI-assisted development workflow

### Goals

* Set up the Java/Spring development environment.
* Create the initial project structure.
* Configure local infrastructure with Docker.
* Establish testing and CI foundations.
* Define development conventions.
* Establish the workflow for collaborating with AI.

### Milestone

**Development environment ready and project foundation established.**

---

## Phase 1 — Java + Spring + PostgreSQL

**Focus:** Build the first version of the payment system as a simple synchronous application.

### Topics

#### Java

* Object-oriented programming
* Interfaces
* Collections
* Generics
* Streams
* Records
* Optional
* Exceptions
* Functional programming basics
* Concurrency fundamentals

#### Spring Boot

* Dependency Injection
* IoC
* REST APIs
* Controllers
* Services
* Repositories
* Configuration
* Validation
* Error handling
* Transactions

#### PostgreSQL

* Relational data modeling
* Constraints
* Indexes
* Transactions
* ACID
* Isolation levels
* Locking
* Query performance
* Database migrations

### Goals

* Build the Payment Service.
* Implement payment creation and retrieval.
* Persist payments in PostgreSQL.
* Establish transaction boundaries.
* Create unit and integration tests.
* Containerize the application.

### Milestone

**Working Payment API using Java, Spring Boot and PostgreSQL.**

---

## Phase 2 — Redis

**Focus:** Introduce Redis by solving concrete problems in the payment system.

### Topics

* Redis data structures
* Key/value model
* TTL and expiration
* Atomic operations
* Caching
* Cache-aside pattern
* Cache invalidation
* Idempotency
* Race conditions
* Distributed rate limiting

### Goals

* Implement payment idempotency.
* Understand how duplicate requests can occur.
* Use Redis for caching where appropriate.
* Implement API/merchant rate limiting.
* Explore Redis failure scenarios.
* Understand when Redis is appropriate and when it is not.

### Milestone

**Payment Service using Redis for idempotency, caching and rate limiting.**

---

## Phase 3 — Kafka + Event-Driven Architecture

**Focus:** Transform the system from a primarily synchronous application into an event-driven system.

### Topics

#### Kafka

* Producers
* Consumers
* Brokers
* Topics
* Partitions
* Offsets
* Consumer groups
* Replication
* Retention
* Ordering
* Consumer lag

#### Event-Driven Architecture

* Synchronous vs asynchronous communication
* Events vs commands
* Event producers and consumers
* Loose coupling
* Event contracts
* Eventual consistency
* Asynchronous workflows
* Publish/subscribe patterns

### Goals

* Introduce `PaymentCreated` events.
* Build Kafka producers and consumers.
* Understand partitions and consumer groups through experiments.
* Split the application into independently processing services.
* Introduce:

  * Payment Service
  * Fraud Service
  * Ledger Service
  * Notification Service
* Observe how failures and delays propagate through an event-driven system.

### Milestone

**Genuinely event-driven payment processing platform using Kafka.**

---

## Phase 4 — Reliability & Distributed Systems

**Focus:** Understand and handle the failure modes introduced by distributed systems.

### Topics

* At-most-once delivery
* At-least-once delivery
* Exactly-once processing concepts
* Idempotent consumers
* Duplicate events
* Retries
* Exponential backoff
* Timeouts
* Dead-letter topics/queues
* Poison messages
* Consumer failures
* Consumer lag
* Eventual consistency
* State machines
* Database/Kafka consistency
* Outbox Pattern
* Saga Pattern concepts
* Compensating actions

### Goals

* Introduce reliable retry strategies.
* Implement dead-letter handling.
* Make event consumers idempotent.
* Simulate consumer and infrastructure failures.
* Understand the database/Kafka dual-write problem.
* Implement the Outbox Pattern.
* Model payment state transitions.
* Document important reliability decisions.

### Milestone

**Reliable event-driven payment platform resilient to common distributed-system failures.**

---

## Phase 5 — AWS + Infrastructure as Code

**Focus:** Understand how to operate the system in a cloud environment.

### Topics

#### AWS

* IAM
* VPC fundamentals
* Networking
* Load Balancers
* Compute
* ECS/EKS concepts
* RDS
* ElastiCache
* MSK
* S3
* CloudWatch

#### Infrastructure as Code

* Terraform
* Providers
* Resources
* Variables
* State
* Modules
* Environments
* Infrastructure lifecycle

#### Architecture decisions

* Kafka vs SQS/SNS
* Managed vs self-managed services
* ECS vs EKS
* Database deployment options
* Cloud scalability and availability

### Goals

* Containerize services for cloud deployment.
* Deploy the application to AWS.
* Use managed services where appropriate.
* Provision infrastructure with Terraform.
* Understand networking and service-to-service communication.
* Evaluate cloud architecture trade-offs.

### Milestone

**Payment platform deployed to AWS with infrastructure managed through Terraform.**

---

## Phase 6 — Production Engineering

**Focus:** Make the system production-oriented and develop stronger System Design skills.

### Topics

#### Observability

* Structured logging
* Metrics
* Distributed tracing
* OpenTelemetry
* Latency
* Throughput
* Error rates
* Kafka consumer lag
* SLIs
* SLOs

#### Resilience

* Timeouts
* Retries
* Circuit breakers
* Bulkheads
* Backpressure
* Rate limiting
* Graceful degradation

#### Performance & Scalability

* Load testing
* Capacity planning
* Bottleneck identification
* Database performance
* Connection pools
* Kafka throughput
* Consumer scaling
* Horizontal scaling

#### System Design

* Scalability
* Availability
* Reliability
* Consistency
* Security
* Failure scenarios
* Capacity estimation
* Bottlenecks
* Trade-offs

### Goals

* Add meaningful observability to the system.
* Measure and analyze system behavior under load.
* Identify and address bottlenecks.
* Test resilience against infrastructure failures.
* Review the architecture as a complete distributed system.
* Document major architectural decisions and trade-offs.
* Prepare to explain the system as a System Design interview case.

### Milestone

**Production-oriented distributed payment platform with documented architecture, reliability strategies and scalability considerations.**

---

# Final Objective

By the end of the roadmap, the goal is not simply to have a project that uses Java, Kafka, Redis and AWS.

The goal is to be able to confidently explain:

* What problem each technology solves.
* Why it was chosen.
* What alternatives were considered.
* What trade-offs it introduces.
* How the system behaves under failure.
* How it scales.
* How it is tested and observed.
* How the architecture could evolve as requirements change.

The project should demonstrate both **hands-on engineering experience** and **System Design reasoning**.
