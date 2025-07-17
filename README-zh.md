# Embabel 智能体框架

![Build](https://github.com/embabel/embabel-agent/actions/workflows/maven.yml/badge.svg)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=embabel_embabel-agent&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=embabel_embabel-agent)
[![Discord](https://img.shields.io/discord/1277751399261798401?logo=discord)](https://discord.gg/t6bjkyj93q)

[//]: # ([![Quality Gate Status]&#40;https://sonarcloud.io/api/project_badges/measure?project=embabel_embabel-agent&metric=alert_status&token=d275d89d09961c114b8317a4796f84faf509691c&#41;]&#40;https://sonarcloud.io/summary/new_code?id=embabel_embabel-agent&#41;)

[//]: # ([![Bugs]&#40;https://sonarcloud.io/api/project_badges/measure?project=embabel_embabel-agent&metric=bugs&#41;]&#40;https://sonarcloud.io/summary/new_code?id=embabel_embabel-agent&#41;)
![Kotlin](https://img.shields.io/badge/kotlin-%237F52FF.svg?style=for-the-badge&logo=kotlin&logoColor=white)
![Java](https://img.shields.io/badge/java-%23ED8B00.svg?style=for-the-badge&logo=openjdk&logoColor=white)
![Spring](https://img.shields.io/badge/spring-%236DB33F.svg?style=for-the-badge&logo=spring&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-6DB33F.svg?style=for-the-badge&logo=Spring-Boot&logoColor=white)
![Apache Tomcat](https://img.shields.io/badge/apache%20tomcat-%23F8DC75.svg?style=for-the-badge&logo=apache-tomcat&logoColor=black)
![Apache Maven](https://img.shields.io/badge/Apache%20Maven-C71A36?style=for-the-badge&logo=Apache%20Maven&logoColor=white)
![JUnit](https://img.shields.io/badge/JUnit5-25A162.svg?style=for-the-badge&logo=JUnit5&logoColor=white)
![ChatGPT](https://img.shields.io/badge/chatGPT-74aa9c?style=for-the-badge&logo=openai&logoColor=white)
![Jinja](https://img.shields.io/badge/jinja-white.svg?style=for-the-badge&logo=jinja&logoColor=black)
![JSON](https://img.shields.io/badge/JSON-000?logo=json&logoColor=fff)
![GitHub Actions](https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white)
![SonarQube](https://img.shields.io/badge/SonarQube-black?style=for-the-badge&logo=sonarqube&logoColor=4E9BCD)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![IntelliJ IDEA](https://img.shields.io/badge/IntelliJIDEA-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white)
[![License](https://img.shields.io/github/license/embabel/embabel-agent?style=for-the-badge&logo=apache&color=brightgreen)](https://www.apache.org/licenses/LICENSE-2.0)
[![Commits](https://img.shields.io/github/commit-activity/m/embabel/embabel-agent.svg?label=commits&style=for-the-badge&logo=git&logoColor=white)](https://github.com/embabel/embabel-agent/pulse)




<img align="left" src="https://github.com/embabel/embabel-agent/blob/main/embabel-agent-api/images/315px-Meister_der_Weltenchronik_001.jpg?raw=true" width="180">

&nbsp;&nbsp;&nbsp;&nbsp;

Embabel（读音：Em-BAY-bel）是一个用于在 JVM 上构建智能体流程的框架，能够无缝地将大语言模型 (LLM) 提示交互与代码和领域模型相结合。支持智能路径规划以实现目标。主要使用 Kotlin 编写，但为 Java 提供了自然的使用模式。来自 Spring 的创造者。

## 核心概念

智能体流程建模包含以下概念：

- **动作 (Actions)**：智能体执行的步骤
- **目标 (Goals)**：智能体试图实现的目标
- **条件 (Conditions)**：在执行动作或确定目标已实现之前需要评估的条件。条件会在每个动作执行后重新评估。
- **领域模型 (Domain model)**：支撑流程并为动作、目标和条件提供信息的对象。
- **计划 (Plan)**：实现目标的动作序列。计划由系统动态制定，而非程序员。系统会在每个动作完成后重新规划，使其能够适应新信息并观察前一个动作的效果。这实际上是一个 [OODA 循环](https://en.wikipedia.org/wiki/OODA_loop)。

> 应用程序开发者通常不需要直接处理这些概念，因为大多数条件来自代码中定义的数据流，允许系统推断前置和后置条件。

这些概念支撑了相比其他智能体框架的以下差异化特性：

- **复杂规划**：超越有限状态机或带嵌套的顺序执行，引入真正的规划步骤，使用非 LLM 的 AI 算法。这使系统能够通过以新颖的顺序组合已知步骤来执行未被编程的任务，并做出关于并行化和其他运行时行为的决策。
- **卓越的可扩展性和重用性**：由于动态规划，添加更多领域对象、动作、目标和条件可以扩展系统的能力，_无需编辑有限状态机定义_或现有代码。
- **强类型和面向对象的优势**：动作、目标和条件由领域模型提供信息，领域模型可以包含行为。一切都是强类型的，提示和手动编写的代码可以清晰地交互。不再有神奇的映射。享受完整的重构支持。

其他优势：

- **平台抽象**：编程模型和平台内部之间的清晰分离允许在本地运行，同时在生产环境中可能提供更高的服务质量，而无需更改应用程序代码。
- **为 LLM 混合而设计**：轻松构建混合 LLM 的应用程序，确保最具成本效益且功能强大的解决方案。这使系统能够为不同任务利用不同模型的优势。特别是，它促进了对特定任务使用本地模型。这对成本和隐私都很重要。
- **基于 Spring 和 JVM 构建**，使其易于访问现有的企业功能和能力。例如：
    - Spring 可以注入和管理智能体，包括使用 Spring AOP 装饰函数。
    - 提供强大的持久化和事务管理解决方案。
- **从头开始为可测试性而设计**。单元测试和智能体端到端测试都很容易。

流程可以通过以下两种方式之一编写：

- 类似于 Spring MVC 的基于注解的模型，使用 Spring 构造型 `@Agent`，使用 `@Goal`、`@Condition` 和 `@Action` 方法。
- 惯用的 Kotlin DSL，使用 `agent {` 和 `action {` 块。

无论哪种方式，流程都由可以具有丰富行为的领域模型对象支持。

> 我们正在努力允许部署自然语言动作和目标。

规划步骤是可插拔的。

默认的规划方法是[目标导向动作规划 (Goal Oriented Action Planning)](https://medium.com/@vedantchaudhari/goal-oriented-action-planning-34035ed40d0b)。GOAP 是游戏中流行的 AI 规划算法。它允许基于世界当前状态和智能体目标进行动态决策和动作选择。

目标、动作和计划独立于 GOAP。未来的规划选项包括：

- 由推理模型（如 OpenAI o1 或 DeepSeek R1）创建的计划。

框架通过 `AgentPlatform` 实现执行。

智能体平台支持以下执行模式：

- **专注模式 (Focused)**：用户代码请求特定功能：用户代码调用方法运行特定智能体，传入输入。这对于代码驱动的流程（如响应传入事件调用的流程）是理想的。
- **封闭模式 (Closed)**：用户意图（或其他传入事件）被分类以选择智能体。平台尝试在其知道的所有智能体中找到合适的智能体。智能体选择是动态的，但只有在特定智能体内定义的动作才会运行。
- **开放模式 (Open)**：评估用户意图，平台使用_所有_资源尝试实现它。平台尝试在其知道的所有目标中找到合适的目标，并从起始状态构建自定义智能体来实现它，包括相关的动作和条件。如果平台不确信任何目标的适用性，它将不会继续。`GoalChoiceApprover` 接口为开发者提供了进一步限制目标选择的方法。

开放模式是最强大的，但确定性最低。
> 在开放模式下，平台能够找到开发者未预见的新颖路径，甚至结合来自多个提供者的功能。

即使在开放模式下，平台也只会执行已指定的单个步骤。（当然，步骤本身可能是 LLM 转换，在这种情况下，提示由用户代码控制，但结果仍然是非确定性的。）

可能的未来模式：

- **演进模式 (Evolving)**：平台可以在同一过程中处理多个目标，并修改运行过程以添加更多目标和智能体。例如，一个动作可以意识到实现额外目标变得重要。

Embabel 智能体系统还将支持联邦，包括与其他 Embabel 系统（允许规划合并远程动作和目标）和第三方智能体框架的联邦。
## 快
速开始

在 5 分钟内运行智能体。

从我们的 [Java](https://github.com/embabel/java-agent-template) 或 [Kotlin](https://github.com/embabel/kotlin-agent-template) GitHub 模板创建您自己的智能体仓库，点击"使用此模板"按钮。

您也可以使用我们的快速开始工具在本地创建自己的 Embabel 智能体项目：

```
uvx --from git+https://github.com/embabel/project-creator.git project-creator
```

选择 Java 或 Kotlin，指定您的项目名称和包名称，如果您已经有 `OPENAI_API_KEY` 并安装了 Maven，您将在一分钟内运行智能体。

> **📚 示例和教程**，请参阅 [Embabel 智能体示例仓库](https://github.com/embabel/embabel-agent-examples)

> **🚗 实际应用示例**，请参阅 [Tripper 旅行规划智能体](https://github.com/embabel/tripper)

## 为什么需要 Embabel？

简而言之：因为智能体框架的演进还处于早期阶段，有很大的改进空间；因为 JVM 上的智能体框架将提供巨大的商业价值。

- _为什么我们需要智能体框架？_ 我们可以在没有更高级抽象的情况下编写代码，直接调用 LLM 并在代码中直接控制流程。然而，更高级的智能体框架提供了令人信服的好处。例如：
    - 分解 LLM 交互，使其更简单、更专注。这最大化了重用性，最小化了成本和错误。它通常允许我们为特定交互使用更便宜的模型。
    - 促进单元测试和集成测试，这对智能体系统和任何其他软件系统一样重要。
    - 增加可组合性，子流程和单个动作可以重用
    - 使应用程序更易管理和健壮，使工作流管理器能够控制其执行并重试操作，同时保持先前状态
    - 通过在许多地方应用护栏来增强安全性
- _当 Python 中存在解决方案时，为什么我们需要 JVM 的智能体框架？_：虽然这个领域目前在 Python（甚至 TypeScript）中发展得更好，但它还处于早期阶段，有很大的空间用于新颖且可能更优秀的方法。关键的邻接性通常不是 LLM——它只是一个简单的 HTTP 调用——而是现有的代码和基础设施资产，这些更可能在 JVM 上而不是在 Python 中。
- _为什么不只使用 Spring AI？_ Spring AI 很棒。我们基于它构建，并拥抱 Spring 组件模型。然而，我们相信大多数应用程序应该使用更高级的 API。一个类比：Spring AI 存在于 Servlet API 的级别，而 Embabel 更像 Spring MVC。复杂的需求在 Embabel 中比直接使用 Spring AI 更容易表达和测试。
- _为什么不尝试将此项目贡献给 Spring？_ 此项目需要与 Spring 不同的治理，Spring 中的大多数项目存在于稳定环境中，可靠性和稳定性胜过快速创新。其次，这些概念不是 JVM 特定的。我们希望 Embabel 成为跨平台的领先智能体框架。虽然 Spring 品牌在 Java 中很有价值，但在 TypeScript 或 Python 中并非如此。

## 展示代码

在 Kotlin 或 Java 中，智能体实现代码直观且易于测试。

```kotlin
@Agent(description = "根据一个人的星座寻找新闻")
class StarNewsFinder(
    // 像 Horoscope 这样的服务使用 Spring 注入
    private val horoscopeService: HoroscopeService,
    private val storyCount: Int = 5,
) {

    @Action
    fun extractPerson(userInput: UserInput): StarPerson =
        // 所有提示都是类型安全的
        PromptRunner().createObject("从此用户输入创建一个人，提取他们的姓名和星座：$userInput")

    @Action
    fun retrieveHoroscope(starPerson: StarPerson) =
        Horoscope(horoscopeService.dailyHoroscope(starPerson.sign))

    // toolGroups 指定此动作运行所需的工具
    @Action(toolGroups = [ToolGroup.WEB])
    fun findNewsStories(person: StarPerson, horoscope: Horoscope): RelevantNewsStories =
        PromptRunner().createObject(
            """
            ${person.name} 是一个相信占星术的人，星座是 ${person.sign}。
            他们今天的星座运势是：
                <horoscope>${horoscope.summary}</horoscope>
            基于此，使用网络工具并生成搜索查询
            找到 $storyCount 个相关新闻故事，用几句话总结它们。
            包含每个故事的 URL。
            不要寻找另一个星座运势阅读或直接返回关于占星术的结果；
            找到与上述阅读相关的故事。

            例如：
            - 如果星座运势说他们可能
            想要改善关系，你可以找到关于
            新颖礼物的新闻故事
            - 如果星座运势说他们可能想要改善职业，
            找到关于培训课程的新闻故事。
        """.trimIndent()
        )

    // @AchievesGoal 注解表示完成此动作
    // 实现了给定目标，因此智能体运行将完成
    @AchievesGoal(
        description = "基于目标人员的星座运势和当前新闻故事为其写一个有趣的文章",
    )
    @Action
    fun writeup(
        person: StarPerson,
        relevantNewsStories: RelevantNewsStories,
        horoscope: Horoscope,
    ): Writeup =
        // 自定义 LLM 调用
        PromptRunner().withTemperature(1.2).createObject(
            """
            取以下新闻故事并为目标人员写一些
            有趣的内容。

            首先以简洁、有趣的方式总结他们的星座运势，然后
            谈论新闻。以令人惊讶的签名结束。

            ${person.name} 是一个相信占星术的人，星座是 ${person.sign}。
            他们今天的星座运势是：
                <horoscope>${horoscope.summary}</horoscope>
            相关新闻故事是：
            ${relevantNewsStories.items.joinToString("\n") { "- ${it.url}: ${it.summary}" }}

            将其格式化为带链接的 Markdown。
        """.trimIndent()
        )

}
```

以下领域类确保类型安全：

```kotlin
data class RelevantNewsStories(
    val items: List<NewsStory>
)

data class NewsStory(
    val url: String,

    val summary: String,
)

data class Subject(
    val name: String,
    val sign: String,
)

data class Horoscope(
    val summary: String,
)

data class FunnyWriteup(
    override val text: String,
) : HasContent
```

## 狗粮政策

我们相信软件开发的所有方面都可以而且应该通过使用 AI 智能体大大加速。最终决策者仍然是人类，但他们可以而且应该得到大大增强。

> 此项目实践极端狗粮政策。

<!-- TODO photo of Duke with kibble -->

我们的关键原则：

1. **我们将使用 AI 智能体帮助项目的每个方面：** 编码、文档、制作营销文案等。任何执行任务的人都应该问为什么它不能自动化，并努力实现最大自动化。
2. **开发者保留最终控制权。** 开发者负责指导智能体朝向解决方案并根据需要迭代。提交或合并智能体贡献的开发者负责确保它符合项目编码标准，这些标准独立于智能体的使用。例如，代码必须是人类可读的。
3. **我们将只使用基于 Embabel 平台构建的开源智能体**，并贡献任何改进。虽然商业编码智能体可能更先进，但我们相信我们的平台是自动化的最佳通用解决方案，通过狗粮政策我们将最快地改进它。通过开源用于我们开源项目的智能体，我们将最大化对社区的好处。
4. **我们将优先考虑帮助加速我们进展的智能体。** 根据飞行安全建议，在帮助他人之前先戴上自己的面罩，我们将优先考虑帮助我们加速自己进展的智能体。这不仅会产生有用的示例，还会增加整体项目速度。

开发者必须仔细阅读他们提交的所有代码，并在可能的情况下改进生成的代码。## 入
门指南

- 获取代码
- 设置环境
- 运行应用程序

### 获取代码

选择以下之一：

- 通过 `git clone https://github.com/embabel/embabel-agent` 克隆仓库
- 创建新的 Spring Boot 项目并添加必要的依赖项（请参阅下面的"在您的项目中使用 Embabel 智能体框架"）

### 环境变量

> 环境变量与常见用法一致，而不是 Spring AI。例如，我们更喜欢 `OPENAI_API_KEY` 而不是 `SPRING_AI_OPENAI_API_KEY`。

必需：

- `OPENAI_API_KEY`：用于 OpenAI API

可选：

- `ANTHROPIC_API_KEY`：用于 Anthropic API。编码智能体需要。

> 我们强烈建议提供 OpenAI 和 Anthropic 密钥，因为一些示例需要两者。为给定任务尝试找到最佳 LLM 很重要，而不是自动选择熟悉的提供商。

### 服务

您需要安装了 Docker MCP 扩展的 Docker Desktop，用于 Docker MCP 工具，如网络搜索工具。确保从目录中激活以下工具：

- Brave Search
- Fetch
- Puppeteer
- Wikipedia

> 您也可以使用 Spring AI 约定设置自己的 MCP 工具。请参阅 `application-docker-desktop.yml` 文件作为示例。

如果您在本地运行 Ollama，设置 `ollama` 配置文件，Embabel 将自动连接到您的 Ollama 端点并使所有模型可用。

### 运行

使用以下命令创建您自己的智能体项目：

```
uvx --from git+https://github.com/embabel/project-creator.git project-creator
```

### 示例智能体

> **📚 示例和教程**，请参阅 [Embabel 智能体示例仓库](https://github.com/embabel/embabel-agent-examples)

```bash
# 克隆并运行示例
git clone https://github.com/embabel/embabel-agent-examples
cd embabel-agent-examples/scripts/kotlin
./shell.sh
```

#### Shell 命令

输入 `help` 查看可用命令。示例：

```
execute "Lynda is a Scorpio, find news for her" -p -r
```

选项：

- `-p` 记录提示
- `-r` 记录 LLM 响应

使用 `chat` 与智能体进行交互式对话。

> **提示：** Spring Shell 支持历史记录 - 输入 `!!` 重复上一个命令

输入 `help` 查看可用命令。

示例：

```
execute "Lynda is a Scorpio, find news for her" -p -r
```

这将寻找智能体，选择星座查找智能体并运行流程。`-p` 将记录提示，`-r` 将记录 LLM 响应。省略这些以减少详细日志记录。

使用 `chat` 命令进入与智能体的交互式聊天。它将保留对话历史，并尝试为每个命令运行最合适的智能体。

> Spring Shell 支持历史记录。输入 `!!` 重复上一个命令。这将在重启后保留，因此在迭代智能体时很方便。

#### 更多示例

Shell 内的示例命令：

```
# Perplexity 风格的深度研究
# 需要 OpenAI 和 Anthropic 密钥以及带有 MCP 扩展的 Docker Desktop（或您自己的网络工具）
execute "research the recent australian federal election. what is the position of the greens party?"

# x 是 execute 的快捷方式
x "fact check the following: holden cars are still made in australia; the koel is a bird native only to australia; fidel castro is justin trudeau's father"

```

尝试 [编码智能体](https://www.github.com/embabel/embabel-coding-agent)（单独的仓库）使用如下命令：

```

x "explain this project for a five your old"

x "take the StarNewsFinder kotlin example of the agent framework. create a parallel .java package beside its and create a java version of the same agent use the same annotations and other classes. use records for the data classes. make it modern java"

x "consider the StarNewsFinder kotlin class. This is intended as an example. Is there anything you could do to make it simpler? Include suggested API changes. Do not change code"
```

### 引入其他 LLM

#### 知名提供商的本地模型

Embabel 智能体框架支持来自以下提供商的本地模型：

- Ollama：只需设置 `ollama` 配置文件，您的本地 Ollama 端点将被查询。所有本地模型都将可用。
- Docker：设置 `docker` 配置文件，您的本地 Docker 端点将被查询。所有本地模型都将可用。

#### 自定义 LLM

您可以为任何有 Spring AI `ChatModel` 可用的提供商定义 LLM。

只需定义 `Llm` 类型的 Spring bean。请参阅 `OpenAiConfiguration` 类作为示例。

记住：

- 如果您知道知识截止日期，请提供
- 使配置类在任何必需的 API 密钥上有条件。

## 路线图

此项目处于早期阶段，但我们有宏大的计划。此仓库中的里程碑和问题是很好的参考。我们的关键目标：

- **成为 Gen AI 启用 Java 应用程序的自然方式**，特别是那些基于 Spring 构建的应用程序。
- **证明模型的力量**。证明此模型是最有能力的智能体模型。请参阅 [Dunnart 里程碑](https://github.com/embabel/embabel-agent/milestone/4) 了解详情。特别是：
    - 通过添加目标和动作来证明无需修改的可扩展性的力量
    - 证明成为自然语言 PaaS 的潜力
    - 证明 GOAP 模型内智能体联邦的潜力
    - 证明预算感知智能体的潜力，如"研究以下主题，如果您仍在学习，花费最多 20 美分"
    - 与数据存储集成并证明在组织内展现现有功能的力量
- **将模型带到其他平台**：概念框架不是 JVM 特定的。一旦建立，我们打算创建 TypeScript 和 Python 项目。

有很多工作要做，您很棒。我们期待您的贡献！

## 应用程序设计

### 领域对象

应用程序以领域对象为中心。这些可以由 LLM 或用户代码实例化，并由用户代码操作。

使用 Jackson 注解帮助 LLM 描述以及标记要忽略的字段。例如：

```kotlin
@JsonClassDescription("具有占星术详细信息的人")
data class StarPerson(
    override val name: String,
    @get:JsonPropertyDescription("星座")
    val sign: String,
) : Person
```

请参阅 [Java Json Schema Generation - Module Jackson](https://github.com/victools/jsonschema-generator/tree/main/jsonschema-module-jackson) 了解所用库的文档。

领域对象可以具有在作用域内时自动暴露给 LLM 的行为。只需使用 Spring AI `@Tool` 注解标注方法。

> 在领域对象上暴露 `@Tool` 方法时，确保工具调用是安全的。即使是最好的 LLM 也可能过于激进。例如，小心可能改变或删除数据的方法。这可能更好地通过在同一领域类上显式调用非工具方法在代码动作中建模。

## 将 Embabel 用作 MCP 服务器

您可以从像 Claude Desktop 这样的 UI 将 Embabel 智能体平台用作 MCP 服务器。Embabel MCP 服务器通过 SSE 可用。

在您的 `claude-desktop.yml` 中如下配置：

```json
{
  "mcpServers": {
    "embabel": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "http://localhost:8080/sse"
      ]
    }
  }
}


```

*注意：* 此功能目前不成熟。

## 消费 MCP 服务器

Embabel 智能体框架提供对消费模型上下文协议 (MCP) 服务器的内置支持，允许您通过标准化接口扩展应用程序的强大 AI 功能。

### 什么是 MCP？

模型上下文协议 (MCP) 是一个开放协议，标准化应用程序如何为大语言模型提供上下文和额外功能。由 Anthropic 引入，MCP 已成为连接 AI 智能体到工具的事实标准，作为客户端-服务器协议运行，其中：

- **客户端**（如 Embabel 智能体）向服务器发送请求
- **服务器**处理这些请求以向 AI 模型提供必要的上下文

MCP 通过标准化简化了 AI 应用程序和外部工具之间的集成，将"M×N 问题"转换为"M+N 问题"——类似于 USB 对硬件外设所做的。

### 在 Embabel 智能体中配置 MCP

要在您的 Embabel 智能体应用程序中配置 MCP 服务器，请将以下内容添加到您的 `application.yml`：

```yaml
spring:
  ai:
    mcp:
      client:
        enabled: true
        name: embabel
        version: 1.0.0
        request-timeout: 30s
        type: SYNC
        stdio:
          connections:
            docker-mcp:
              command: docker
              args:
                - run
                - -i
                - --rm
                - alpine/socat
                - STDIO
                - TCP:host.docker.internal:8811
```

此配置设置了连接到基于 Docker 的 MCP 服务器的 MCP 客户端。连接通过 Docker 的 socat 实用程序使用 STDIO 传输连接到 TCP 端点。

### Docker Desktop MCP 集成

Docker 通过其 Docker MCP 目录和工具包拥抱了 MCP，提供：

1. **集中发现** - 集成到 Docker Hub 中用于发现 MCP 工具的可信中心
2. **容器化部署** - 将 MCP 服务器作为容器运行，无需复杂设置
3. **安全凭据管理** - 集中、加密的凭据处理
4. **内置安全性** - 沙盒隔离和权限管理

Docker MCP 生态系统包括来自 Stripe、Elastic、Neo4j 等合作伙伴的 100 多个经过验证的工具，所有这些都可通过 Docker 的基础设施访问。

### 了解更多

- [Docker MCP 文档](https://docs.docker.com/desktop/features/gordon/mcp/)
- [Docker MCP 服务器仓库](https://github.com/docker/mcp-servers)
- [介绍 Docker MCP 目录和工具包](https://www.docker.com/blog/introducing-docker-mcp-catalog-and-toolkit/)
- [MCP 介绍和概述](https://www.philschmid.de/mcp-introduction)

## A2A

Embabel 与 [A2A](https://github.com/google-a2a/A2A) 协议集成，允许您连接到其他启用 A2A 的智能体和服务。

启用 `a2a` Spring 配置文件以启动 A2A 服务器。

您需要以下环境变量：

- `GOOGLE_STUDIO_API_KEY`：您的 Google Studio API 密钥，用于 Gemini。

使用 `a2a` Docker 配置文件启动 Google A2A Web 界面：

```bash
docker compose --profile a2a up
```

转到在容器内运行的 Web 界面 `http://localhost:12000/`。

在 `host.docker.internal:8080/a2a` 连接到您的智能体。注意 `localhost:8080/a2a` 不会工作，因为服务器在 Docker 容器中运行时无法访问它。

## 运行测试

通过 Maven 运行测试。

```bash
mvn test
```

这将运行单元测试和集成测试，但不需要互联网连接或任何外部服务。

## Spring 配置文件

Spring 配置文件用于为不同环境和行为配置应用程序。

交互配置文件：

- `shell`：在交互式 shell 中运行智能体。不启动 Web 进程。

模型配置文件：

- `ollama`：查找 Ollama 模型。您需要在本地安装 Ollama 并拉取相关模型。
- `docker-desktop`：在 Docker 外部运行但与带有 MCP 扩展的 Docker Desktop 通信时查找 Docker 管理的本地模型。**这是推荐的最佳体验，带有 Docker 提供的网络工具。**
- `docker`：在 Docker 容器中运行时查找 Docker 管理的本地模型。

日志配置文件：

- `severance`：[Severance](https://www.youtube.com/watch?v=xEQP4VVuyrY&ab_channel=AppleTV) 特定日志记录。赞美 Kier！
- `starwars`：星球大战特定日志记录。感受原力
- `colossus`：Colossus 特定日志记录。Forbin 项目。

## 测试

此框架的一个关键目标是易于测试。正如 Spring 简化了早期企业 Java 应用程序的测试一样，此框架促进了 AI 应用程序的测试。

测试类型：

- 单元测试：所有智能体都是单元可测试的，就像任何 Spring 管理的 bean 一样。使用模拟对象构造它们；调用单个动作方法。测试库促进测试提示。
- 集成测试：待定

## 日志记录

此项目中的所有日志记录要么是相关类本身的调试日志记录，要么是结果。