# Product Overview

Embabel Agent Framework is a JVM-based framework for building AI agent applications that seamlessly mix LLM interactions with code and domain models. 

## Key Features

- **Sophisticated Planning**: Uses Goal Oriented Action Planning (GOAP) algorithm for dynamic decision-making
- **Strong Typing**: Full type safety with domain models, actions, goals, and conditions
- **Spring Integration**: Built on Spring Boot with dependency injection and enterprise features
- **Multi-LLM Support**: Works with OpenAI, Anthropic, Ollama, and other providers
- **MCP Integration**: Supports Model Context Protocol for tool integration
- **A2A Protocol**: Integrates with Agent-to-Agent communication protocol

## Programming Models

- **Annotation-based**: Spring-style with `@Agent`, `@Goal`, `@Action`, `@Condition` annotations
- **Kotlin DSL**: Idiomatic Kotlin with `agent {}` and `action {}` blocks

## Execution Modes

- **Focused**: Direct agent invocation for specific tasks
- **Closed**: Dynamic agent selection from available agents
- **Open**: Goal-based execution using all available resources

The framework enables building testable, composable, and extensible AI applications on the JVM.