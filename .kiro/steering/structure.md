# Project Structure

## Multi-Module Maven Project

The Embabel Agent Framework follows a modular architecture with clear separation of concerns:

## Core Modules

- **embabel-agent-api**: Core framework APIs, DSLs, and main functionality
- **embabel-agent-autoconfigure**: Spring Boot auto-configuration
- **embabel-agent-dependencies**: Dependency management BOM
- **embabel-agent-starters**: Spring Boot starters for easy integration

## Specialized Modules

- **embabel-agent-shell**: Interactive command-line interface using Spring Shell
- **embabel-agent-ux**: User experience and interface components
- **embabel-agent-rag**: Retrieval-Augmented Generation capabilities
- **embabel-agent-mcpserver**: Model Context Protocol server implementation
- **embabel-agent-a2a**: Agent-to-Agent protocol integration
- **embabel-agent-eval**: Agent evaluation and testing utilities
- **embabel-agent-test**: Testing utilities and frameworks

## Documentation & Build

- **embabel-agent-docs**: Project documentation (activated with `-Pembabel-agent-docs`)

## Key Directories

```
├── .github/                    # GitHub workflows and templates
├── .kiro/                      # Kiro IDE configuration and steering
├── embabel-agent-api/          # Main API module
│   ├── src/main/kotlin/        # Kotlin source code
│   ├── src/main/java/          # Java source code  
│   ├── src/test/               # Test code
│   └── docker-compose.yml      # Local services
├── embabel-agent-shell/        # CLI module
├── embabel-agent-starters/     # Spring Boot starters
│   ├── embabel-agent-starter/
│   ├── embabel-agent-starter-platform/
│   └── embabel-agent-starter-bedrock/
└── pom.xml                     # Parent POM
```

## Naming Conventions

- **Modules**: `embabel-agent-{purpose}` format
- **Packages**: Follow `com.embabel.agent.{module}` structure
- **Classes**: Use descriptive names with appropriate suffixes (Agent, Action, Goal, Condition)
- **Configuration**: Spring profiles for different environments and features

## Dependencies Flow

- All modules inherit from `embabel-agent-parent`
- Common dependencies managed in `embabel-agent-dependencies` BOM
- Modules depend on `embabel-agent-api` for core functionality
- Starters provide easy integration points for applications

## Source Organization

- **Kotlin**: Primary language, located in `src/main/kotlin`
- **Java**: Interop support, located in `src/main/java`
- **Resources**: Configuration files in `src/main/resources`
- **Tests**: Mirror source structure in `src/test/`

## Build Artifacts

- Each module produces a JAR artifact
- `embabel-agent-shell` can be run as executable JAR
- Starters provide auto-configuration for Spring Boot applications