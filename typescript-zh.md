# TypeScript 开发规范（中文）

## 代码规范

- 2 空格缩进，strict mode 强制开启
- 接口用 `interface`，类型用 `type`；优先 `unknown` 而非 `any`
- 异步统一返回 `Promise<T>`，禁止裸 Promise
- 路径别名 `@/*` 在 tsconfig 中配置，禁止相对路径跳层（`../../`）
- React 组件用 `.tsx`，工具函数用 `.ts`

## 测试策略

- 框架：`Jest` 或 `Vitest`
- Mock：`vi.mock()` / `jest.mock()`，MSW 模拟 HTTP
- 快照测试用于组件：`expect(component).toMatchSnapshot()`
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
npm install && npm ci                  # lockfile 保证一致

# 检查
tsc --noEmit                           # strict mode
eslint src/ --ext .ts,.tsx
prettier --check src/

# 测试
vitest run                             # 或 jest

# 构建
vite build                             # 前端
tsc && esbuild dist/index.js --bundle  # 库
```
