# Go 开发规范（中文）

## 代码规范

- `gofmt` 自动格式化，tab 缩进（工具强制，社区统一）
- 错误必须显式处理，绝不用 `_` 忽略
- Context 作为第一个参数传递
- 禁止 `package main` 混用；业务逻辑放 `internal/`
- 依赖通过 `go mod tidy` 管理

## 测试策略

- 框架：`testing` 标准库 + `testify/require`
- Table-Driven Tests：所有场景用 `t.Run(name, func(t *testing.T))`
- 性能基准：`Benchmark`，用 `go test -bench=. -benchmem`
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
# 依赖
go mod tidy
go mod download

# 编译
go build ./...                          # 所有包
go build -o bin/app cmd/main.go         # 二进制

# 测试
go test -v -race -cover ./...
go test -bench=. -benchmem

# Lint
golangci-lint run ./...
```
