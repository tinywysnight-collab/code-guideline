# Python 开发规范（中文）

## 代码规范

- 4 空格缩进，PEP 8
- **依赖必须通过 `pyproject.toml` 管理（禁止 requirements.txt）**，用 `uv` 锁定版本
- 类型提示必须完整（mypy strict 模式）
- 私有属性用 `_` 前缀；避免循环依赖，用惰性导入
- 异步用 `asyncio` / `aiohttp`，禁止同步阻塞
- 入口脚本：`if __name__ == "__main__":`

## 测试策略

- 框架：`pytest` + `pytest-asyncio`
- Mock：`unittest.mock`，patch ≤ 2 层
- Fixture：`@pytest.fixture(scope="session")` 复用耗时资源
- 参数化：`@pytest.mark.parametrize`
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
uv sync                      # 安装（基于 uv.lock）
uv add pytest                # 添加依赖

# 检查
mypy src/                    # strict 模式
ruff check src/              # lint

# 测试
pytest tests/ -v --cov=src/ --cov-report=term-missing

# 发布（可选）
pip install build && python -m build  # sdist + wheel
```
