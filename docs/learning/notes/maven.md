## Questions to help me understand Maven

Maven itself is the CLI (`mvn`). The compiler plugin is **not** Maven: it is a plugin that Maven calls to run `javac`. Their versions are independent.

---

### 1. What is Maven actually doing?

Maven is **not** the JVM and **not** `javac`. It orchestrates the build:

- reads `pom.xml`
- downloads dependencies into the local cache (`~/.m2`)
- runs plugins bound to lifecycle phases
- for compile, it asks `maven-compiler-plugin` to call `javac`

```text
  you:  mvn compile | test | package
                 │
                 ▼
              Maven
                 │
     ┌───────────┼───────────┐
     ▼           ▼           ▼
  compiler    surefire      jar
  plugin      plugin        plugin
     │           │           │
     ▼           ▼           ▼
  javac       JUnit      .jar in target/
```

`java -cp target/classes com.velasques.app.App` does **not** use Maven. It only runs bytecode that Maven (or another compile) already produced.

---



### 2. What is the role of `pom.xml`?

It is the **project contract**: identity, Java version, dependencies, and plugin versions.

In this repo it lives at `event-driven-payment-journey/pom.xml`. Run `mvn` from that directory.


| Piece                                | Role here                                                                                   |
| ------------------------------------ | ------------------------------------------------------------------------------------------- |
| `groupId` / `artifactId` / `version` | Coordinates of the artifact (`com.velasques.app:event-driven-payment-journey:1.0-SNAPSHOT`) |
| `maven.compiler.release`             | Compile for Java 25                                                                         |
| `dependencies`                       | JUnit Jupiter (test scope only)                                                             |
| `pluginManagement`                   | Pins plugin versions, including compiler 3.14.1                                             |


Without the POM, Maven would not know what to compile, which tests to run, or which libraries to put on the classpath.

---



### 3. What happens during compile, test and package?

Phases are a **ladder**. Asking for a phase runs that phase **and every earlier one**.

```text
validate → … → compile → … → test → … → package
```

`mvn compile`

- copies `src/main/resources` into `target/classes` (skipped if that folder does not exist)
- compiles `src/main/java` → `target/classes`
- does **not** compile or run tests
- does **not** run `App.main`

`mvn test`

- everything in `compile`
- compiles `src/test/java` → `target/test-classes`
- Surefire runs JUnit (`AppTest`)
- reports land in `target/surefire-reports/`
- failed tests fail the build

`mvn package`

- everything in `test`
- `maven-jar-plugin` builds a JAR from production classes (not test classes)

Useful extra: `mvn clean` deletes `target/` so the next command recreates it from source.

---



### 4. Where does the generated artifact go?

Always under `target/` (gitignored). Source stays in `src/`.


| Path                                                   | Created by            | Contents                                 |
| ------------------------------------------------------ | --------------------- | ---------------------------------------- |
| `target/classes/`                                      | `compile`             | Production `.class` (and main resources) |
| `target/test-classes/`                                 | `test` (test-compile) | Test `.class`                            |
| `target/surefire-reports/`                             | `test`                | Test reports                             |
| `target/event-driven-payment-journey-1.0-SNAPSHOT.jar` | `package`             | The **artifact**: packaged app           |


The JAR name is `{artifactId}-{version}.jar`.

`mvn compile` creates `target/` if it is missing. It does **not** create `test-classes` or the JAR. Incremental compile may skip `javac` if nothing changed; the folder still remains.

```text
src/main/java/.../App.java
        │  mvn compile
        ▼
target/classes/.../App.class
        │  mvn package
        ▼
target/event-driven-payment-journey-1.0-SNAPSHOT.jar
```

