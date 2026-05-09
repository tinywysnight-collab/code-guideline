# Java 开发规范（中文）

## 代码规范

- 4 空格缩进，Google Java Format 或 OpenJDK 规范
- 类名 `UpperCamelCase`，方法/变量 `lowerCamelCase`
- 检查异常用 `Optional<T>` 而非 null；老代码用 `@Nullable` 标注
- Maven/Gradle 统一管理，禁止 system scope
- Spring Boot：配置用 `application.yml`，禁止硬编码

## 测试策略

- 框架：`JUnit 5` + `Mockito`
- Spring 项目用 `@SpringBootTest` 加载真实上下文，限制范围
- `@Nested` 嵌套测试类组织逻辑组
- 覆盖率目标：核心业务 ≥ 80%

## Git 提交规范

```
<type>(<scope>): <subject>

[optional body]
[optional footer]
```

**Type**：feat / fix / docs / refactor / test / chore / perf / ci

- Subject ≤ 72 字，祈使语气（"add" 而非 "added"）
- Scope 用模块名：`feat(auth):`
- Breaking Change：footer 写 `BREAKING CHANGE:`

## 构建命令

```bash
# Maven
mvn clean compile                      # 编译
mvn test                               # 测试
mvn package -DskipTests                # 打包
mvn verify                             # 集成测试

# Gradle
./gradlew build
./gradlew test --info
./gradlew bootJar                      # Spring Boot jar
```
