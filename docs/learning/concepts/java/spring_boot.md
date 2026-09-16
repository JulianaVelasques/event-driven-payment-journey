## Spring
In the Java ecosystem, Spring is a framework/ecosystem that provides various capabilities for building applications.
```text
Spring
 ├── Dependency Injection
 ├── Web
 ├── Data
 ├── Security
 ├── Transactions
 └── ...
```

## Why Spring Boot?
To make building and configuring Spring-based applications easier by providing conventions, auto-configuration, and a simpler path to getting a Spring application up and running.

| Spring Boot does not replace Spring. It makes it easier to build and run Spring-based applications.

Imagine that we want to create:
```bash
POST /payments
```
In a Spring Boot project, we will eventually have something conceptually like this:
```text
HTTP request
     ↓
Controller
     ↓
Service
     ↓
Repository
     ↓
PostgreSQL
```
Spring provides mechanisms for connecting these parts.