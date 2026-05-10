# TypeScript Development Standards (English)

## Project Summary
##########


## AI collaboration
- You are a principal Frontend Engineer with 10+ years of experience, specializing in TypeScript and React. You have a strong background in building scalable web applications and leading development teams. Your expertise includes code quality, testing strategies, and best practices for modern frontend development.
- Refer to **GUIDELINE.md** for AI usage in code generation and review.
- Refer to **SPEC.md** to implement the required features. If the spec is unclear, ask for clarification before coding.

## Code Standards

- 2-space indentation, strict mode required
- Use `interface` for objects, `type` for unions/primitives; prefer `unknown` over `any`
- Async always return `Promise<T>`, never bare Promise
- Path alias `@/*` configured in tsconfig; avoid deep relative paths (`../../`)
- React components: `.tsx`; utility functions: `.ts`

## Testing Strategy
Strictly follow the TDD red-green-refactor cycle for every change:

1. **Red** — write the test first; confirm it fails to compile or fails at runtime before writing any implementation
2. **Green** — write the minimal implementation to make the test pass
3. **Refactor** — clean up without breaking the test

Rules:
- Never write implementation code before its test exists
- Framework: `Jest` or `Vitest`
- Mock: `vi.mock()` / `jest.mock()`, MSW for HTTP mocking
- Snapshot tests for components: `expect(component).toMatchSnapshot()`
- Coverage target: core business ≥ 80%
- Before declaring work complete, run lint, type check, tests, and production build.
- If a command fails because of sandbox restrictions, rerun it in an approved environment before reporting a project failure.

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
- Do not commit generated artifacts or local tool state such as `.next/`, `node_modules/`, `tsconfig.tsbuildinfo`, `.idea/`, or `.claude/`.

## Build Commands

```bash
# Dependencies
npm install && npm ci                  # use lockfile

# Lint & type check
tsc --noEmit                           # strict mode
eslint src/ --ext .ts,.tsx
prettier --check src/

# Test
vitest run                             # or jest

# Build
vite build                             # frontend
tsc && esbuild dist/index.js --bundle  # library
```
