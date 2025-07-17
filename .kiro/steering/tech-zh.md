# 技术栈

## 构建系统
- **Maven**：主要构建工具，多模块结构
- **Java 21**：LTS 版本，Spring Boot 3.x 最低需要 JDK 17+
- **Kotlin**：主要语言，与 Java 互操作
- **Spring Boot 3.x**：应用程序框架，具有自动配置

## 核心依赖
- **Spring Framework**：依赖注入、AOP、事务管理
- **Spring AI**：LLM 集成和 AI 功能
- **Spring Shell**：交互式命令行界面
- **Jackson**：JSON 序列化，包含 Kotlin 模块
- **Kotlin Coroutines**：异步编程

## AI 和 LLM 集成
- **OpenAI API**：GPT 模型集成
- **Anthropic API**：Claude 模型集成  
- **Ollama**：本地模型支持
- **AWS Bedrock**：云 AI 服务（可选）
- **MCP (模型上下文协议)**：工具集成标准

## 测试
- **JUnit 5**：单元测试框架
- **Spring Boot Test**：集成测试
- **Testcontainers**：基于容器的测试
- **MockK**：Kotlin 模拟库
- **JaCoCo**：代码覆盖率

## 开发环境
- **Nix Flakes**：可重现的开发环境
- **Docker**：容器化和本地服务
- **IntelliJ IDEA**：推荐的 IDE

## 常用命令

```bash
# 构建整个项目
mvn clean install

# 运行测试
mvn test

# 使用 shell 界面运行应用程序
mvn spring-boot:run -Dspring.profiles.active=shell

# 使用 Docker 服务运行
docker-compose up

# 构建文档
mvn clean install -Pembabel-agent-docs

# 构建时跳过测试
mvn clean package -DskipTests
```

## 环境变量
- `OPENAI_API_KEY`：OpenAI 集成必需
- `ANTHROPIC_API_KEY`：Anthropic 集成可选
- `GOOGLE_STUDIO_API_KEY`：A2A 协议与 Gemini 集成必需

## Spring 配置文件
- `shell`：交互式 shell 模式
- `ollama`：本地 Ollama 模型支持
- `docker-desktop`：Docker MCP 工具集成
- `a2a`：智能体间通信协议支持