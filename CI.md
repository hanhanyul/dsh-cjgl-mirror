# CI 与协作配置

这个仓库是 `hanqi007/dsh-cjgl` 的镜像，配置了以下 GitHub 能力：

## 1. 持续集成（.github/workflows/ci.yml）

- 触发：推送到 `main` / `dev`，以及针对 `main` 的拉取请求
- 环境：Ubuntu + Node 20
- 步骤：
  1. `node --check lib/index.js` —— 语法检查
  2. `node test/smoke-host.mjs` —— 冒烟测试（95 项断言）

## 2. 自动分配问题（.github/workflows/auto-assign.yml）

- 触发：新 issue 创建
- 行为：自动把 issue 分配给 `hanqi007`，没有标签时补一个 `triage`

## 3. 分支保护

`main` 分支启用规则集：

- 合并前必须通过 CI（状态检查 `test`）
- 必须经拉取请求，至少 1 个批准
- 禁止强制推送与删除分支

## 4. 拉取请求

所有改动走 PR 流程，标题用 `feat:` / `fix:` / `chore:` 前缀。
