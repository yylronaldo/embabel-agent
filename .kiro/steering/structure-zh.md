# 项目结构

## 多模块 Maven 项目

Embabel 智能体框架遵循模块化架构，具有清晰的关注点分离：

## 核心模块

- **embabel-agent-api**：核心框架 API、DSL 和主要功能
- **embabel-agent-autoconfigure**：Spring Boot 自动配置
- **embabel-agent-dependencies**：依赖管理 BOM
- **embabel-agent-starters**：用于轻松集成的 Spring Boot 启动器

## 专用模块

- **embabel-agent-shell**：使用 Spring Shell 的交互式命令行界面
- **embabel-agent-ux**：用户体验和界面组件
- **embabel-agent-rag**：检索增强生成 (RAG) 功能
- **embabel-agent-mcpserver**：模型上下文协议 (MCP) 服务器实现
- **embabel-agent-a2a**：智能体间通信 (A2A) 协议集成
- **embabel-agent-eval**：智能体评估和测试工具
- **embabel-agent-test**：测试工具和框架

## 文档和构建

- **embabel-agent-docs**：项目文档（使用 `-Pembabel-agent-docs` 激活）

## 关键目录

```
├── .github/                    # GitHub 工作流和模板
├── .kiro/                      # Kiro IDE 配置和指导
├── embabel-agent-api/          # 主要 API 模块
│   ├── src/main/kotlin/        # Kotlin 源代码
│   ├── src/main/java/          # Java 源代码  
│   ├── src/test/               # 测试代码
│   └── docker-compose.yml      # 本地服务
├── embabel-agent-shell/        # CLI 模块
├── embabel-agent-starters/     # Spring Boot 启动器
│   ├── embabel-agent-starter/
│   ├── embabel-agent-starter-platform/
│   └── embabel-agent-starter-bedrock/
└── pom.xml                     # 父 POM
```

## 命名约定

- **模块**：`embabel-agent-{用途}` 格式
- **包**：遵循 `com.embabel.agent.{模块}` 结构
- **类**：使用描述性名称和适当的后缀（Agent、Action、Goal、Condition）
- **配置**：不同环境和功能的 Spring 配置文件

## 依赖流

- 所有模块继承自 `embabel-agent-parent`
- 通用依赖在 `embabel-agent-dependencies` BOM 中管理
- 模块依赖 `embabel-agent-api` 获取核心功能
- 启动器为应用程序提供简单的集成点

## 源代码组织

- **Kotlin**：主要语言，位于 `src/main/kotlin`
- **Java**：互操作支持，位于 `src/main/java`
- **资源**：配置文件位于 `src/main/resources`
- **测试**：在 `src/test/` 中镜像源结构

## 构建产物

- 每个模块产生一个 JAR 产物
- `embabel-agent-shell` 可以作为可执行 JAR 运行
- 启动器为 Spring Boot 应用程序提供自动配置