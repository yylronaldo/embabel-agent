# 中文翻译设计文档

## 概述

本设计文档定义了将Embabel Agent Framework英文文档翻译为中文的详细方案，包括翻译策略、术语规范、文件结构和质量保证措施。

## 架构

### 翻译策略架构

```
英文源文档 → 术语标准化 → 语言本地化 → 格式调整 → 质量检查 → 中文目标文档
```

### 文件映射关系

- `README.md` → `README-zh.md`
- `.kiro/steering/product.md` → `.kiro/steering/product-zh.md`
- `.kiro/steering/tech.md` → `.kiro/steering/tech-zh.md`
- `.kiro/steering/structure.md` → `.kiro/steering/structure-zh.md`

## 组件和接口

### 术语翻译组件

**核心概念术语表：**

| 英文 | 中文翻译 | 说明 |
|------|----------|------|
| Agent | 智能体 | AI领域标准翻译 |
| Action | 动作 | 保持简洁 |
| Goal | 目标 | 直译 |
| Condition | 条件 | 直译 |
| Planning | 规划 | AI规划领域标准翻译 |
| Domain Model | 领域模型 | 软件工程标准翻译 |
| Framework | 框架 | 标准翻译 |
| Spring Boot | Spring Boot | 保留英文 |
| Maven | Maven | 保留英文 |
| Kotlin | Kotlin | 保留英文 |

**技术术语表：**

| 英文 | 中文翻译 | 说明 |
|------|----------|------|
| Goal Oriented Action Planning (GOAP) | 目标导向动作规划 (GOAP) | 保留英文缩写 |
| Model Context Protocol (MCP) | 模型上下文协议 (MCP) | 保留英文缩写 |
| Agent-to-Agent (A2A) | 智能体间通信 (A2A) | 保留英文缩写 |
| Large Language Model (LLM) | 大语言模型 (LLM) | 标准翻译 |
| Dependency Injection | 依赖注入 | 标准翻译 |
| Auto-configuration | 自动配置 | 标准翻译 |

### 格式处理组件

**Markdown格式保持：**
- 标题层级保持不变
- 代码块保持原样
- 链接保持功能性
- 徽章和图片保持原样

**中文排版规范：**
- 中英文之间添加空格
- 使用中文标点符号
- 数字与中文之间添加空格
- 专有名词首次出现时提供英文对照

## 数据模型

### 翻译单元模型

```
TranslationUnit {
  sourceText: String
  targetText: String
  context: String
  terminology: List<Term>
  reviewStatus: ReviewStatus
}
```

### 术语模型

```
Term {
  english: String
  chinese: String
  category: TermCategory
  usage: String
  consistency: Boolean
}
```

## 错误处理

### 翻译质量控制

1. **术语一致性检查**
   - 扫描文档中的关键术语
   - 验证翻译一致性
   - 标记不一致的翻译

2. **格式完整性检查**
   - 验证Markdown格式
   - 检查链接有效性
   - 确保代码块完整

3. **语言质量检查**
   - 检查中文语法
   - 验证标点符号使用
   - 确保表达自然流畅

## 测试策略

### 翻译质量测试

1. **术语一致性测试**
   - 创建术语检查清单
   - 验证关键概念翻译统一
   - 检查专有名词处理

2. **可读性测试**
   - 中文母语者审阅
   - 技术准确性验证
   - 表达自然度评估

3. **格式完整性测试**
   - Markdown渲染测试
   - 链接功能测试
   - 代码示例验证

### 测试用例

1. **README翻译测试**
   - 验证项目介绍翻译准确性
   - 检查安装说明的可操作性
   - 确保代码示例保持原样

2. **Steering文件翻译测试**
   - 验证技术栈描述准确性
   - 检查项目结构说明清晰度
   - 确保产品概述完整性

## 实施计划

### 阶段1：术语标准化
- 建立完整术语表
- 定义翻译规范
- 创建质量检查清单

### 阶段2：核心文档翻译
- 翻译README.md主要部分
- 处理技术概念和代码示例
- 保持格式和链接完整性

### 阶段3：Steering文件翻译
- 翻译产品概述文档
- 翻译技术栈文档
- 翻译项目结构文档

### 阶段4：质量保证
- 术语一致性检查
- 语言质量审核
- 格式完整性验证