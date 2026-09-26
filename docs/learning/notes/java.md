## Questions to help me undertand Java
1. What is the difference between JVM, JRE and JDK?

JVM = engine that execute bytecode

JRE = environment needed to run a Java aplication
      (includes JVM + runtime libraries)

JDK = ambiente para desenvolver Java
      (includes developer tools + runtime)

When we write file_name.java, we have our SOURCE code. The "javac" that is available in the JDK compile it to bytecode: file_name.class

```text
                 JDK
                  │
        ┌─────────┴─────────┐
        │                   │
    javac                  JRE* 
        │                   │
        ▼                   ▼
     .class                JVM
                            │
                            ▼
                     executa bytecode
```
* We don't need to focus on the differences between JRE and JDK

2. Why does our project needs a JDK instead of only a JVM?

Because we're going to develop a Java application, so we need the java development kit.

3. Why can a Java application compiled on macOS run on Linux without recompiling the Java code, under normal conditions?

Because with the bytecode format and it can be executed in any platform that has a JVM compatible.

```text
                    .class
                      │
             ┌────────┼────────┐
             ▼        ▼        ▼
           JVM      JVM       JVM
          macOS     Linux    Windows
```

In sum:
```text
                 DEVELOPMENT
                      │
                 ┌────▼────┐
                 │   JDK   │
                 └────┬────┘
                      │
                    javac
                      │
                      ▼
                Java bytecode
                   (.class)
                      │
                      ▼
                    JVM
                      │
               ┌──────┴──────┐
               │             │
             macOS          Linux
               │             │
               ▼             ▼
           execution      execution
```