<h1 align="center"> 💳 Event-Driven Payment Journey <h1>
<h4 align="center">
  🚀 Learning by implementing an Event-Driven Payment Processing Platform
</h4>

<p align="center">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/JulianaVelasques/event-driven-payment-journey">

  <a href="https://github.com/JulianaVelasques/event-driven-payment-journey/commits/main">
    <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/JulianaVelasques/event-driven-payment-journey">
  </a>

  <a href="https://github.com/JulianaVelasques/event-driven-payment-journey/issues">
    <img alt="GitHub issues" src="https://img.shields.io/github/issues/JulianaVelasques/event-driven-payment-journey">
  </a>

  <img alt="License" src="https://img.shields.io/badge/license-MIT-brightgreen">

</p>

<p align="center">
  <a href="#page_with_curl-about">About</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#construction-current-status">Current Status</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#building_construction-architecture">Architecture</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#wrench-built-with">Built With</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#books-learning-journey">Learning Journey</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#rocket-getting-started">Getting Started</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#grin-notes">Notes</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#woman_technologist-author">Author</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#memo-license">License</a>
</p>

## :page_with_curl: About

This is a personal learning and portfolio project focused on building an **Event-Driven Payment Processing Platform** from scratch.

The main goal is to explore the technologies and architectural patterns commonly used to build scalable and reliable backend systems, while understanding not only **how** to use them, but also **why and when** to use them.

The project will progressively explore:

* Java and Spring Boot
* PostgreSQL
* Redis
* Apache Kafka
* Event-Driven Architecture
* Distributed Systems
* Reliability and resilience patterns
* AWS
* Terraform
* Docker
* Kubernetes
* Observability and monitoring

Rather than building everything at once, the architecture will evolve as new requirements and problems are introduced.

### :bulb: Why this project?

I have professional experience working with backend systems, APIs, integrations, cloud infrastructure, Kubernetes, Terraform, Redis and messaging infrastructure.

However, several of these technologies were already available as part of existing systems and infrastructure.

This project is an opportunity to go one step further:

> **From using technologies that already exist to understanding and implementing the systems behind them.**

The goal is to develop stronger backend and System Design skills, especially around distributed systems, asynchronous communication, reliability, scalability and architectural trade-offs.

It is also part of my preparation for Software Engineering opportunities in Europe.

---

## :construction: Current Status

The project is being developed incrementally through different phases.

### Phase 0 — Setup

**Current phase:** 🚧 In progress

The current focus is on establishing the development environment and project foundations:

* Java
* Spring Boot
* Maven
* Docker
* PostgreSQL
* Testing
* CI/CD
* Development conventions
* AI-assisted development workflow

The project will gradually evolve from a simple Payment API into a distributed, event-driven system.

### Roadmap

| Phase | Focus                             |
| ----- | --------------------------------- |
| 0     | Setup                             |
| 1     | Java + Spring + PostgreSQL        |
| 2     | Redis                             |
| 3     | Kafka + Event-Driven Architecture |
| 4     | Reliability & Distributed Systems |
| 5     | AWS + Infrastructure as Code      |
| 6     | Production Engineering            |

For the complete roadmap, see [`docs/project/roadmap.md`](docs/project/roadmap.md).

---

## :building_construction: Architecture

The architecture will evolve throughout the project.

The initial version is intentionally simple:

```text
Client
  │
  ▼
Payment Service
  │
  ▼
PostgreSQL
```

As the project evolves, asynchronous processing and additional services will be introduced:

```text
                         ┌───────────────┐
                         │    Client     │
                         └───────┬───────┘
                                 │
                                 ▼
                       ┌──────────────────┐
                       │  Payment Service  │
                       └────────┬─────────┘
                                │
                         PaymentCreated
                                │
                                ▼
                         ┌─────────────┐
                         │    Kafka    │
                         └──────┬──────┘
                                │
              ┌─────────────────┼─────────────────┐
              ▼                 ▼                 ▼
       ┌────────────┐    ┌────────────┐    ┌──────────────┐
       │   Fraud    │    │   Ledger   │    │ Notification │
       │   Service  │    │   Service  │    │   Service    │
       └────────────┘    └────────────┘    └──────────────┘
```

Redis, AWS services and additional infrastructure will be introduced as the system's requirements and failure scenarios become more complex.

Architecture documentation and diagrams can be found in [`docs/architecture`](docs/architecture).

---

## :wrench: Built With

The technology stack will evolve throughout the project.

### Backend

* [Java](https://www.oracle.com/java/)
* [Spring Boot](https://spring.io/projects/spring-boot)
* [Maven](https://maven.apache.org/)

### Data & Messaging

* [PostgreSQL](https://www.postgresql.org/)
* [Redis](https://redis.io/)
* [Apache Kafka](https://kafka.apache.org/)

### Infrastructure

* [Docker](https://www.docker.com/)
* [Kubernetes](https://kubernetes.io/)
* [Terraform](https://www.terraform.io/)
* [AWS](https://aws.amazon.com/)

### Testing & CI

* [JUnit](https://junit.org/)
* [Testcontainers](https://testcontainers.com/)
* [GitHub Actions](https://github.com/features/actions)

### Observability

* OpenTelemetry
* Metrics
* Structured logging
* Distributed tracing

Not all of these technologies are part of the current implementation yet. They will be introduced gradually as part of the learning journey.

---

## :books: Learning Journey

This repository is not only about the final implementation.

I am also documenting the problems, experiments and architectural decisions made throughout the project.

### What I want to explore

* REST APIs and backend architecture
* Database transactions and consistency
* Redis and caching strategies
* Idempotency
* Event-Driven Architecture
* Kafka producers and consumers
* Partitions and consumer groups
* Message ordering
* At-least-once delivery
* Retries and dead-letter queues
* Eventual consistency
* Outbox Pattern
* Distributed systems failure scenarios
* Scalability and performance
* AWS architecture
* Infrastructure as Code
* Observability and resilience

### Documentation

```text
docs/
├── project/
│   ├── context.md
│   ├── goals.md
│   └── roadmap.md
│
├── architecture/
│   ├── overview.md
│   ├── decisions/
│   └── diagrams/
│
├── learning/
│   ├── concepts/
│   ├── experiments/
│   └── notes/
│
└── development/
    ├── workflow.md
    ├── conventions.md
    └── current-state.md
```

The idea is to document not only **what was implemented**, but also the reasoning behind the decisions.

---

## 🤖 AI-Assisted Development

AI is part of the development workflow of this project.

I want to explore how AI can improve engineering productivity without replacing the learning process.

The workflow I am using is:

```text
Learn
  ↓
Design
  ↓
Implement
  ↓
Test
  ↓
Break
  ↓
Review
  ↓
Document
```

AI may be used as:

* Teacher
* Pair programmer
* Design reviewer
* Code reviewer
* Debugging partner
* Adversarial tester
* System Design interviewer
* Documentation assistant

The goal is to use AI to accelerate development while still understanding the concepts, trade-offs and implementation decisions behind the system.

More details about the development workflow can be found in [`AGENTS.md`](AGENTS.md) and [`docs/development/workflow.md`](docs/development/workflow.md).

---

## :rocket: Getting Started

### Prerequisites

The project will evolve over time, but the initial development environment requires:

* Java 21+
* Maven
* Docker
* Git

### Clone the project

```bash
git clone git@github.com:JulianaVelasques/event-driven-payment-journey.git

cd event-driven-payment-journey
```

### Run the project

The local development setup will be documented as the project progresses.

```bash
docker compose up --build
```

---

## :mag: Project Goals

By the end of the project, I want to be able to confidently explain:

* What problem each technology solves.
* Why a particular technology was chosen.
* What alternatives were considered.
* What trade-offs each decision introduces.
* How the system behaves when components fail.
* How the system can scale.
* How asynchronous processing affects consistency.
* How the system can be tested and observed.
* How the architecture could evolve as requirements change.

The final goal is not simply to have a project using Java, Kafka, Redis and AWS.

It is to build a system that I understand deeply enough to explain, debug, evolve and defend from a System Design perspective.

---

## :grin: Notes

* The architecture is intentionally being developed incrementally.
* Technologies are introduced when they solve a concrete problem in the system.
* Experiments and failure scenarios are part of the learning process.
* Architectural decisions will be documented as ADRs under [`docs/architecture/decisions`](docs/architecture/decisions).
* The project is primarily a learning and portfolio project, so some components may intentionally be simplified compared to a production payment platform.
* The implementation will prioritize understanding and engineering trade-offs over unnecessary complexity.

---

## :woman_technologist: Author

* LinkedIn - [Juliana Velasques Balta](https://www.linkedin.com/in/julianavelasquesbalta/)
* GitHub - [Juliana Velasques](https://github.com/JulianaVelasques)

---

## :memo: License

This project is under the MIT license. See the [LICENSE](LICENSE.md) file for more details.

---

Made with ♥ by [Juliana Velasques](https://github.com/JulianaVelasques)
