---
name: "dev-workflow"
description: "Orchestrates the full software development lifecycle across 4 stages (Product/UIDesign/Code/Test) with 13 sub-skills. Invoke when user wants to start a software project, build a feature, or follow a structured dev process."
---

# 软件开发流程编排器

本 skill 编排完整的软件开发生命周期，按 **产品 → UI设计 → 开发 → 测试** 四大环节调度 13 个子 skill，管理阶段转换、上下文传递、迭代循环和决策点。

## 何时触发

- 用户要启动新的软件项目或功能
- 用户要求按流程开发
- 用户提到 "开发流程"、"软件开发"、"项目流程"、"从需求到上线"

## 四大环节总览

```
═══════════════════════════════════════════════════════════════
  产品 (Product)       UI设计 (UI)       开发 (Code)        测试 (Test)
═══════════════════════════════════════════════════════════════
  01 需求分析 ─────┐   01 UI设计 ───┐   01 技术架构设计 ─┐  01 测试用例编写
  02 原型设计      │                  │   02 代码编写 ─────┤  02 系统测试
  03 PRD编写 ──────┤                  │   03 代码审查 ─────┤  03 Bug修复 ──┐
  04 价值编写 ─────┘                  │                     │              │
  05 操作说明手册 ←───────────────────────────────────────────── (测试通过后) │
  06 上线发布 ←────────────────────────────────────────────────── (手册完成后)│
═══════════════════════════════════════════════════════════════
```

## 详细流程图

```
[产品环节]
  dev-product-01-requirements (需求分析)
        ↓
  brainstorming (头脑风暴) [内置 skill]
        ↓
  dev-product-02-prototype (原型设计)
        ↓
  dev-product-03-prd (PRD编写)
        ↓
  dev-product-04-value (价值编写)
        ↓
[UI设计环节]
  dev-ui-01-design (UI设计)
        ↓
[开发环节]
  dev-code-01-architecture (技术架构设计)  ←─────────────────┐
        ↓                                                   │
  dev-code-02-coding (代码编写)  ←────────────────────┐     │
        ↓                                              │     │
  dev-code-03-review (代码审查)                         │     │
        │                                              │     │
        ├── 通过 ──────────────────────────┐           │     │
        └── 不通过 → 返回代码编写 ─────────┤           │     │
                                           │           │     │
[测试环节]                                  │           │     │
  dev-test-01-testcases (测试用例编写) ─────┤           │     │
        ↓                                  │           │     │
  dev-test-02-testing (系统测试) ←──────────┘           │     │
        │                                              │     │
        ├── 通过 → [产品环节收尾]                       │     │
        │     dev-product-05-manual (操作说明手册)       │     │
        │           ↓                                   │     │
        │     dev-product-06-release (上线发布)          │     │
        │           ↓                                   │     │
        │        🎉 项目完成                             │     │
        │                                              │     │
        └── 未通过 → dev-test-03-bugfix (Bug修复) ──────┘     │
                        │                                     │
                        └→ 返回 dev-code-02-coding ───────────┘
```

## 环节定义

### 一、产品环节 (Product)

| 序号 | Skill | 中文 | 必选 |
|------|-------|------|------|
| P-01 | `dev-product-01-requirements` | 需求分析 | 是 |
| - | `brainstorming` | 头脑风暴 | 否 |
| P-02 | `dev-product-02-prototype` | 原型设计 | 否 |
| P-03 | `dev-product-03-prd` | PRD编写 | 是 |
| P-04 | `dev-product-04-value` | 价值编写 | 否 |
| P-05 | `dev-product-05-manual` | 操作说明手册 | 否 |
| P-06 | `dev-product-06-release` | 上线发布 | 是 |

### 二、UI设计环节 (UIDesign)

| 序号 | Skill | 中文 | 必选 |
|------|-------|------|------|
| U-01 | `dev-ui-01-design` | UI设计 | 否 |

### 三、开发环节 (Code)

| 序号 | Skill | 中文 | 必选 |
|------|-------|------|------|
| C-01 | `dev-code-01-architecture` | 技术架构设计 | 是 |
| C-02 | `dev-code-02-coding` | 代码编写 | 是 |
| C-03 | `dev-code-03-review` | 代码审查 | 否 |

### 四、测试环节 (Test)

| 序号 | Skill | 中文 | 必选 |
|------|-------|------|------|
| T-01 | `dev-test-01-testcases` | 测试用例编写 | 是 |
| T-02 | `dev-test-02-testing` | 系统测试 | 是 |
| T-03 | `dev-test-03-bugfix` | Bug修复 | 否 |

## 执行规则

### 1. 阶段调度
使用 Skill 工具调用对应子 skill，传入之前所有阶段的累积上下文。

### 2. 上下文传递
维护 ProjectContext 对象，每个阶段的输出自动追加。

### 3. 迭代循环
- **Bug 循环**：T-03 → C-02 → C-03 → T-02（最多 3 次）
- **审查拒绝循环**：C-03 → C-02（最多 2 次）
- **需求变更**：任何阶段可触发回退到 P-01

### 4. 并行执行
- U-01 和 T-01 可并行（在 P-04 完成后）
- C-01 完成后，C-02 和 T-01 可并行

### 5. 跳过决策
每个阶段前评估跳过条件，**必须与用户确认后才能跳过**。

### 6. 进度追踪
每次会话开始时展示当前进度。

### 7. 错误处理
- 子 skill 失败 → 报告错误，提供选项：重试 / 跳过 / 手动处理
- 子 skill 不存在 → 通知用户，提供选项：创建 / 手动进行 / 使用内置替代
