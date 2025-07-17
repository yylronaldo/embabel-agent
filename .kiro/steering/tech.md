# Technology Stack

## Build System
- **Maven**: Primary build tool with multi-module structure
- **Java 21**: LTS version, minimum JDK 17+ required for Spring Boot 3.x
- **Kotlin**: Primary language with Java interoperability
- **Spring Boot 3.x**: Application framework with auto-configuration

## Core Dependencies
- **Spring Framework**: Dependency injection, AOP, transaction management
- **Spring AI**: LLM integration and AI capabilities
- **Spring Shell**: Interactive command-line interface
- **Jackson**: JSON serialization with Kotlin module
- **Kotlin Coroutines**: Asynchronous programming

## AI & LLM Integration
- **OpenAI API**: GPT models integration
- **Anthropic API**: Claude models integration  
- **Ollama**: Local model support
- **AWS Bedrock**: Cloud AI services (optional)
- **MCP (Model Context Protocol)**: Tool integration standard

## Testing
- **JUnit 5**: Unit testing framework
- **Spring Boot Test**: Integration testing
- **Testcontainers**: Container-based testing
- **MockK**: Kotlin mocking library
- **JaCoCo**: Code coverage

## Development Environment
- **Nix Flakes**: Reproducible development environment
- **Docker**: Containerization and local services
- **IntelliJ IDEA**: Recommended IDE

## Common Commands

```bash
# Build entire project
mvn clean install

# Run tests
mvn test

# Run application with shell interface
mvn spring-boot:run -Dspring.profiles.active=shell

# Run with Docker services
docker-compose up

# Build documentation
mvn clean install -Pembabel-agent-docs

# Skip tests during build
mvn clean package -DskipTests
```

## Environment Variables
- `OPENAI_API_KEY`: Required for OpenAI integration
- `ANTHROPIC_API_KEY`: Optional for Anthropic integration
- `GOOGLE_STUDIO_API_KEY`: Required for A2A protocol with Gemini

## Spring Profiles
- `shell`: Interactive shell mode
- `ollama`: Local Ollama model support
- `docker-desktop`: Docker MCP tools integration
- `a2a`: Agent-to-Agent protocol support