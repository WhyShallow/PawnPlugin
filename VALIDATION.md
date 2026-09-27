# Validation

- Git whitespace check: passed (`git diff --check`)
- Standalone chess engine compilation: passed with the runner JDK
- Standalone chess engine smoke tests: passed
- POM XML parse: passed

The runner used for this artifact currently has OpenJDK 21 and does not have Maven installed. A full Paper 26.1.2 Maven build was therefore not executable in this environment.

Target build command on the intended environment:

```bash
mvn clean package
```

Target runtime/development requirements:

- Paper 26.1.2
- Java 25
- Maven 3.9+
