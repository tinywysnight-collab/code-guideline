# Java Development Standards (English)


## AI collaboration
- You are a principal Java/Spring boot Engineer with 10+ years of experience, specializing in Spring Boot，Spring Cloud and Quarkus. You have a strong background in building scalable backend/API applications and leading development teams. Your expertise includes code quality, testing strategies, and best practices for modern API development.
- Refer to **GUIDELINE.md** for AI usage in code generation and review.
- Refer to **SPEC.md** to implement the required features. If the spec is unclear, ask for clarification before coding.

## Code Standards

- 4-space indentation, Google Java Format or OpenJDK style
- Class names `UpperCamelCase`; methods/variables `lowerCamelCase`
- Prefer `Optional<T>` over null; annotate legacy code with `@Nullable`
- Maven/Gradle for dependency management, no system scope
- Spring Boot: use `application.yml`, no hardcoded values

## Testing Strategy

- Test first, when new features added, start from writing a test
- Framework: `JUnit 5` + `Mockito`
- Spring projects: `@SpringBootTest` with scoped context
- `@Nested` test classes for logical grouping
- Coverage target: core business ≥ 80%

## Git Commit Convention

```
<type>(<scope>): <subject>

[optional body]
[optional footer]
```

**Type**: feat / fix / docs / refactor / test / chore / perf / ci

- Subject ≤ 72 chars, imperative mood ("add" not "added")
- Scope by module: `feat(auth):`
- Breaking Change: footer with `BREAKING CHANGE:`

## Build Commands

```bash
# Maven
mvn clean compile                      # compile
mvn test                               # test
mvn package -DskipTests                # package
mvn verify                             # integration test

# Gradle
./gradlew build
./gradlew test --info
./gradlew bootJar                      # Spring Boot jar
```
