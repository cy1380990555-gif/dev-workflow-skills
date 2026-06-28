---
name: "dev-ui-01-design"
description: "Creates high-fidelity UI designs based on Ant Design spec with mock data. Invoke when user needs UI mockups, visual design, design specs, or mentions 'UI设计', '界面设计', '视觉设计', 'UI design'."
---

# UI设计-01: UI设计

基于原型和 PRD，严格按照 Ant Design 设计规范创建高保真 UI 设计稿，使用 Mock 数据实现可交互的演示 Demo。

## 设计规范要求

**必须严格遵循 Ant Design 设计规范**：
- 组件：直接选用 Ant Design 组件库（Button、Table、Form、Modal 等）
- 主题：白色背景 + 蓝色主色（#1677ff）
- 字体：默认 Ant Design 字体规范
- 间距：遵循 Ant Design 间距体系
- 交互：遵循 Ant Design 交互规范

**Demo 质量要求**：
- 所有页面交互必须正常工作，点击按钮有响应
- 使用 Mock 数据填充，数据要真实合理
- 不允许出现点击无反应、报错、空白页面等现象
- 表单提交、弹窗打开关闭、页面跳转等交互必须完整可用

## 触发条件

- 原型和 PRD 已确认，需要输出视觉设计
- 用户提到 "UI设计"、"界面设计"、"视觉设计"、"出设计稿"
- 前端开发需要设计规范和切图

## 执行步骤

### Step 1: Ant Design 主题配置

基于 Ant Design 默认主题，确认项目主题配置：

```markdown
## 主题配置

### 色彩体系（基于 Ant Design 默认主题）
| 类别 | 色值 | 用途 |
|------|------|------|
| 主色 | #1677ff | 主要按钮、链接、重点元素 |
| 成功色 | #52c41a | 成功状态 |
| 警告色 | #faad14 | 警告提示 |
| 错误色 | #ff4d4f | 错误状态、危险操作 |
| 文字主色 | rgba(0,0,0,0.88) | 正文标题 |
| 背景色 | #ffffff | 页面背景 |
| 布局背景 | #f5f5f5 | 布局区域背景 |
```

### Step 2: Ant Design 组件选型确认

确认每个页面区域使用的 Ant Design 组件。

### Step 3: 核心页面设计

为每个核心页面输出设计说明，包含布局结构、组件明细、Mock 数据、页面状态。

### Step 4: Demo 验证

**必须逐页验证**：
- [ ] 每个按钮点击后有正确响应
- [ ] 表单可以正常填写和提交
- [ ] Modal/Drawer 可以正常打开和关闭
- [ ] Table 数据正常显示，分页可切换
- [ ] 搜索和筛选功能正常
- [ ] 页面跳转正常
- [ ] Mock 数据真实合理

### Step 5: 设计走查

与前端开发确认组件使用、主题配置、交互实现。

## 输出物

- Ant Design 主题配置
- 组件选型方案
- 核心页面设计稿（含各状态）
- Mock 数据集
- 动效说明
- 可交互 Demo

## 质量检查清单

- [ ] 严格使用 Ant Design 组件，白色背景蓝色主色(#1677ff)
- [ ] 所有 P0 功能页面有设计稿
- [ ] 每个页面有空/加载/错误状态
- [ ] 所有按钮点击有响应，无报错无空白
- [ ] 表单可填写可提交，校验正常
- [ ] Mock 数据真实合理
- [ ] 移动端适配已考虑
- [ ] 前端开发已确认可实现

## 交接条件

→ 下一阶段：**技术架构设计** (dev-code-01-architecture)
