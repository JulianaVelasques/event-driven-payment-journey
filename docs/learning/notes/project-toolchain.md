# Project Toolchain

This document defines the main tools and versions used in the project.

## Java

* **Version:** Java 25
* **Release type:** Long-Term Support (LTS)
* **JDK required:** Yes

Java 25 was selected because it is the latest LTS release and provides a modern Java baseline for the project.

The project requires a JDK rather than only a runtime because Java development requires tools such as `javac` for compilation.

## Maven

* **Version:** 3.9.x
* **Purpose:** Dependency management and build automation

Maven will manage project dependencies and the application build lifecycle.

For Java 25, the `maven-compiler-plugin` should be version **3.14.1 or higher** to support the Java version used by the project.

> Note: `maven-compiler-plugin` is a Maven build plugin and is separate from the Maven version itself.

## Spring Boot

* **Version:** TBD

Spring Boot will be used as the backend application framework.

The final version should be selected based on compatibility with Java 25 and the project's other dependencies.

## Docker

* **Version:** Current stable version installed locally
* **Purpose:** Containerized and reproducible environments

Docker will be used in later phases to run the application and supporting infrastructure in containers.

Containerization is intentionally outside the scope of Task 0.

## Git

* **Version:** Current stable version installed locally
* **Purpose:** Source control and versioning

Git will be used to track the project's source code and changes.

## Environment Variables

Environment-specific configuration and sensitive values should be provided through environment variables rather than hardcoded into the source code.

Examples include:

* database connection information
* credentials
* service endpoints
* environment-specific configuration
