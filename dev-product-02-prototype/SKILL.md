---
name: "dev-product-02-prototype"
description: "Designs interactive prototypes based on Ant Design spec with mock data. Invoke when user needs wireframes, mockups, interaction design, or mentions '原型设计', '交互设计', 'wireframe', 'prototype'."
---

# 产品-02: 原型设计

基于需求和头脑风暴结果，严格按照 Ant Design 设计规范设计产品原型，使用 Mock 数据实现可交互的演示 Demo。

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

- 需求分析完成，需要可视化产品形态
- 用户提到 "原型设计"、"交互设计"、"画原型"、"wireframe"
- 需要向利益相关者展示产品概念

## 执行步骤

### Step 1: 信息架构设计

梳理产品的信息层级和导航结构。

### Step 2: Ant Design 组件选型

为每个页面区域选择对应的 Ant Design 组件。

### Step 3: 页面原型设计

为每个核心页面设计原型，使用 Ant Design 组件。

### Step 4: 交互流程定义

描述用户操作和系统响应。

### Step 5: 用户旅程地图

描述核心用户场景和情绪变化。

### Step 6: Demo 验证

**必须逐页验证**：
- [ ] 每个按钮点击后有正确响应（不报错、不空白）
- [ ] 表单可以正常填写和提交
- [ ] Modal/Drawer 可以正常打开和关闭
- [ ] Table 数据正常显示，分页可切换
- [ ] 搜索和筛选功能正常
- [ ] 页面跳转正常，面包屑正确
- [ ] 所有 Mock 数据真实合理

## 输出物

- 信息架构图
- Ant Design 组件选型方案
- 核心页面原型（至少覆盖 P0 功能）
- Mock 数据集
- 交互流程文档
- 可交互 Demo（所有交互正常工作）

## 质量检查清单

- [ ] 严格使用 Ant Design 组件，白色背景蓝色主色
- [ ] 所有 P0 功能的页面已有原型
- [ ] 每个页面有空状态/加载/错误状态
- [ ] 所有按钮点击有响应，无报错无空白
- [ ] 表单可填写可提交，校验正常
- [ ] Mock 数据真实合理
- [ ] 交互流程覆盖正常和异常路径
- [ ] 导航结构清晰，页面跳转正常
- [ ] 用户已确认原型方向

## 交接条件

→ 下一阶段：**PRD编写** (dev-product-03-prd)
